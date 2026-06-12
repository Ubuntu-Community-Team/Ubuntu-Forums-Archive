---
title: "Shutting Down Problem in Ubuntu 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by nns2006 on 2009-10-31
Hi,
I have upgraded Ubuntu 9.04 to 9.10 yesterday. After up-gradation I am not able to shut down my laptop normally.Each time I have to press power button to turn it off.
I am getting this messages on screen during shutdown process.(I have tried to put it exactly as it appears on screen.)  


> 
*stopping kernel Oops catching service kerneloops
*stopping internet superserver inetd
*stopping wifi-radar daemon...
*stopping the winbid daemon winbid
*shutting down ALSA...
*Asking all remaining processes to terminate...
*Deconfiguring network interfaces...
*Deactivating swap...
[19533.731276] Buffer I/O error on device loop0, logical block 3043332
[19533.731953] Buffer I/O error on device loop0, logical block 3044132
[19533.732731] Buffer I/O error on device loop0, logical block 3044133
[19533.733321] Buffer I/O error on device loop0, logical block 3044134
[19533.842788] Buffer I/O error on device loop0, logical block 1838616
[19538.010393]Buffer I/O error on device loop0, logical block 22973
[19538.010763] Aborting journel on device loop0.
[19538.010865] Buffer I/O error on device loop0, logical block 1099.


Please help,
Thanks in advance

---

### Post by Liolikas on 2009-10-31
wubi user?
You may try to reformat swap, do not know if this helps.

---

### Post by nns2006 on 2009-10-31
> **Liolikas said:**
> wubi user?
You may try to reformat swap, do not know if this helps.

Thats right. I have installed Ubuntu 8.04 and since then i am upgrading it. I have had no problem till date in booting up or shutting down.

---

### Post by nns2006 on 2009-11-01
Any suggestions for it?

---

### Post by rustymercedes on 2009-11-01
I have the same problem on two computers.  Both wubi installs.  One on xp desktop and the other on vista laptop. I will wait for someone to tell me how to repair.  I was thinking maybe reinstall 9.10 with wubi.

---

### Post by LewRockwell on 2009-11-01
quit using wubi...perhaps?

a quick search regarding wubi problems should convince most not to use it

we suppose if you've got nothing to lose and you've done all your back-ups and you've secured all your valuable data and you don't mind spending your time re-installing your stuff...go for the wubi-buntu-grenade...

we'll continue to put our distros in separate partitions

as always, your mileage may vary, buyer beware, and buyer be aware

we now return you to your regularily scheduled programming

.

---

### Post by rustymercedes on 2009-11-01
I just reinstalled with wubi 9.10 and it works great.  The upgrade to 9.10 within a wubi 9.04 is the problem. so don't upgrade from 9.04 if it is a wubi install.

---

### Post by nns2006 on 2009-11-01
But i have already upgraded  to 9.10

---

### Post by pastalavista on 2009-11-01
Just an idea... before shutting down, try, in terminal, the command
```
sudo swapoff -a
```

---

### Post by poo706 on 2009-11-01
This is getting talked about on all of these other threads:
[http://ubuntuforums.org/showthread.php?t=1306005](http://ubuntuforums.org/showthread.php?t=1306005)
[http://swiss.ubuntuforums.org/showthread.php?p=8206421](http://swiss.ubuntuforums.org/showthread.php?p=8206421)
[http://georgia.ubuntuforums.org/showthread.php?p=8216794](http://georgia.ubuntuforums.org/showthread.php?p=8216794)
[http://ubuntu-ky.ubuntuforums.org/sh....php?p=8212799](http://ubuntu-ky.ubuntuforums.org/sh....php?p=8212799)

The most promising thing I've seen is from the last one, and it's just a workaround at best. The advice from post #6 (from P4man) halfway worked for me. When I get the buffer errors, I can get it to shutdown without holding the power button, but I couldn't get it to reboot via that method. In doing searches for this nearly every day for the last few weeks, it looks like it's a problem that's hit Wubi before. And there's a lot of people talking about it, so I'm sure a fix will be released soon.

[poo]

---

