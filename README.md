Region 1: tight

Region 2: loose

Region 0: neither

### running
get a copy of backend_atto_cmssw/CMSSW_10_6_20.tgz and backend_histo_cmssw/CMSSW_10_6_20.tgz

make sure scramv1 b ProjectRename runs in cmssw-el7 container
```
mkdir backend_atto_cmssw
cd backend_atto_cmssw
cp /home/chiarito/work/atto_framework_apr22restart/backend_atto_cmssw/CMSSW_10_6_20.tgz .
#cmssw-el7 at LPC
cmssw-el7 -p --bind `readlink $HOME` --bind `readlink -f ${HOME}/nobackup/` --bind /uscms_data --bind /uscmst1b_scratch --bind /cvmfs -- /bin/bash -l
#cmssw-el7 at HEX
source /home/joey/alma8_setups/setup_cmssw-el7_apptainer.sh
scramv1 b ProjectRename
```
Do the same for backend_histo_cmssw

Submit jobs with condor_submit.py

### to work on backend
1. get a copy
```
backend_plotting_get.sh
```
2. change code and run interactively, under CMSSW_10_6_20/src/PhysicsTools/NanoAODTools/python/fmk_plotting directory
3. git push
4. copy tarball to cmslpc for use with next job
```
backend_plotting_xrdcp.sh 
```
