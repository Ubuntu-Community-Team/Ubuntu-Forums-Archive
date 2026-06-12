---
title: "cant run openshot video editor"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by manny43 on 2010-06-19
Hello friends.Could you please help me with this issue?Openshot is in Applications Sound
& Video but it wont open after i click it.Thanks
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
Process no longer exists: 3146.  Creating new pid lock file.
*** ERROR: MLT Python bindings failed to import ***
*** ERROR: MLT Python bindings failed to import ***
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/pymodules/python2.6/openshot/classes/thumbnail.py", line 170, in run
    mlt.Factory().init()
NameError: global name 'mlt' is not defined

-------------------------------------------------------
Error:  OpenShot has not been installed in the Python path.
(Both the site-packages and /usr/share/openshot folders were checked)

Use the following command to install OpenShot:
  $ sudo python setup.py install

manny@mannyschmitty-desktop:~$ sudo python setup.py install
python: can't open file 'setup.py': [Errno 2] No such file or directory
manny@mannyschmitty-desktop:~$

---

### Post by manny43 on 2010-06-19
solved with the following command ln -s $(ls -C /usr/lib/libmlt++.so.* | cut -f 1 -d' ') /usr/lib/libmlt++.so.2

---

