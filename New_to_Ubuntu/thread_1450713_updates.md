---
title: "updates"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by hatridge on 2010-04-09
Been having trouble with updates. I get this error message

  	 	 	 	 	 	  E: python-evolution: subprocess installed post-installation script returned error exit status 2  
 E: python-gtkmozembed: subprocess installed post-installation script returned error exit status 2  
 E: python-wnck: subprocess installed post-installation script returned error exit status 2

---

### Post by -humanaut- on 2010-04-09
try running ```
sudo dpkg --configure -a 
```

---

### Post by hatridge on 2010-04-09
I get this...

$ sudo dpkg --configure -a
[sudo] password for jim: 
Setting up python-wnck (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-wnck (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-wnck
jim@jim-desktop:~$

---

### Post by -humanaut- on 2010-04-09
you could try ```
sudo apt-get -f remove 
``` That should atleast give you back your package manager

---

### Post by hatridge on 2010-04-09
I am still receiving errors no matter what I attempt...so far.....

jim@jim-desktop:~$ sudo apt-get -f remove
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-evolution (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-evolution (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-gtkmozembed (2.25.3-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gtkmozembed (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-wnck (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-wnck (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-evolution
 python-gtkmozembed
 python-wnck
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-desktop:~$

---

