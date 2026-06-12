---
title: "POSIX way to detect Python dependencies from Bash"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by outleradam on 2010-10-21
I have a bash script which runs a python script. My bash script checks for all its dependencies by using "test `which binary` || echo "binary missing, please install".
 
I am trying to extend this into a python script. For python, how would you check for dependencies? I need to ensure that two packages which don't have binaries are installed:
 
```
if [  libmyth-python  is found && python-lxml is found ]; then
     echo "found python dependencies running script"
     runPython.py
else 
     echo "python dependencies not found, install libmyth-python and python-lxml"
fi
```
 
Obviously this if statement wont work.... [ libmyth-python is found && python-lxml is found ] I need to figure out the proper POSIX way to do this.

---

