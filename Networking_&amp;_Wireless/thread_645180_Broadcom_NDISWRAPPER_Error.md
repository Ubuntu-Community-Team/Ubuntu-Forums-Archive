---
title: "Broadcom NDISWRAPPER Error"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by mallama on 2007-12-19
Yes another broadcom ndiswrapper problem. For some reason i keep getting this error? Any help would be greatly appreciated!```
mallama@mallama-lp:~/Desktop/sp33008$ sudo -i
root@mallama-lp:~# ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
root@mallama-lp:~# ndiswrapper -l
bcmwl5 : invalid driver!
root@mallama-lp:~#

 

```

---

### Post by mallama on 2007-12-20
Ok i removed the old driver and reinstalled the new broadcom driver w/ndiswrapper. When i run "ndiswrapper -i" it shows installed. But when i try to enable my wireless card it will show enabling .... and then not enable? Any suggestions?

 Thanks in advance.
 Mallama

---

### Post by Stu09 on 2007-12-22
I am getting the same error trying to install wireless on my MacBook :(
In the MacBook wiki it says to install ndiswrapper-1.8. 1.9 was the only one available.
Would this have anything to do with it ?

---

### Post by kevdog on 2007-12-22
Try a new version of bcmwl5  (make sure you uninstall the older one).  This shread should provide a link:

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

