---
title: "No protocol specified xhost:  unable to open display &quot;:0&quot;"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by sachin6870 on 2008-12-08
Hi,

 I recently migrated to  ubuntu 8.10 from windows XP. I am trying to setup my development environment on ubuntu.
 I am installing oracle 11g by following [this link]("http://www.pythian.com/blogs/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex"),
 
 but while setting up X-server, I am getting following error,

```
oracle@sachin-laptop:~$ export DISPLAY=:0
oracle@sachin-laptop:~$ xhost +localhost
No protocol specified
xhost:  unable to open display ":0"
```

I tried all suggestion mentioned in above link, but it does not help. 

Any help/ pointers appreciated.

Thanks, 
Sachin
Ubuntu NewBie

---

### Post by bogdan.veringioiu on 2008-12-08
Hi.
Try to run "xhost +" as root.

Then export DISPLAY=:0.0 as oracle user.

Bogdan

---

### Post by sachin6870 on 2008-12-08
got it working myself by using sux package to swicth user

---

### Post by menng99 on 2009-05-20
> **bogdan.veringioiu said:**
> Hi.
Try to run "xhost +" as root.

Then export DISPLAY=:0.0 as oracle user.

Bogdan
It worked for Kubuntu 8.10 (Ibex) under VMWARE to display ORACLE-installer in WINDOWS host system.

---

### Post by ddieterich on 2009-05-26
Thanks for the tip on sux.  I ran across this problem as well.  However, sux didn't look like an easy fix.  I was able to use xhost to fix this problem on Jaunty with the following command:

xhost SI:localuser:oracle

---

### Post by snicklefritz on 2009-09-22
this worked for me:

```
oracle@whale:~/database$ DISPLAY=":0.0" export DISPLAY
```



but then i got :

```
Checking monitor: must be configured to display at least 256 colors
    >>> Could not execute auto check for display colors using command /usr/X11R6/bin/xdpyinfo. Check if the DISPLAY variable is set.    Failed <<<<
```

If I instead of trying to do this through vnc I setup ssh and got in and also set up tunneling along with allowing x11 all in Putty, and also installed and setup Xming....that worked great.
There are tons of tutorials on how to setup the ssh/xming way so just Google "xming ssh tutorial" and you should find something thats useful.

hope that info helps someone

---

