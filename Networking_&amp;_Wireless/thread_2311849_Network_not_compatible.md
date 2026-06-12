---
title: "Network not compatible"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by da-stuhl on 2016-01-30
Hi, ubuntu is pretty new to me. so is programming and advanced stuff like this. i still like it. but yesterday i made an update (14.04. LTS) and since then i have no internet connection. i found this problem on some forums, but i really cannot handle the suggestions. 

so when i go to system settings and then i click 'network' it says 'the network service of this system is not compatible with this version. i also cannot create a manual network because all the buttons are grey. 

i just want to delete the last update. when i ask for the dpkg.log file there are soo many updates that have been installed, so i cannot figure out which one is responsible for the network error. i could upload a screenshot if it helps. would it be possible to just dele it via 'sudo apt-get remove .....'?

can you please tell me step by step what i would have to do?

thanks

---

### Post by howefield on 2016-01-30
If you have the proposed repository enabled, it might be worth looking at this thread.

[http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705)

---

### Post by da-stuhl on 2016-01-30
this really sounds like the same issue. i feel a bit stupid. but i still couldnt make it.i dont really know wich files to download ([B]libnl-3-200_3.2.21-1_amd64.deb libnl-genl-3-200_3.2.21-1_amd64.deb libnl-route-3-200_3.2.21-1_amd64.deb) ??? 
[/B]these ones i couldnt find...

---

### Post by da-stuhl on 2016-01-30
oh i think i got it now. f.e. when i download the libnl-3-200- file. i have two options. eiter amd64 or i386. so i guess this is about the processor, right? i have an intel i5 :/

sorry for those noob-questions :D

---

### Post by howefield on 2016-01-30
> **da-stuhl said:**
> oh i think i got it now. f.e. when i download the libnl-3-200- file. i have two options. eiter amd64 or i386. so i guess this is about the processor, right? i have an intel i5 :/

Sort of about the processor, but it really refers to the operating system.. if you are using a 32 bit operating system choose i386, if you are using a 64 bit operating sytem choose amd64.

Click on the cog wheel on the top panel and select "About this Computer" - should tell you in there what you are running.

> sorry for those noob-questions :D

Please don't worry about the questions, a forum thrives on them :)

---

### Post by grahammechanical on 2016-01-30
I have seen elsewhere on this forum someone solving a problem like this by selecting a previous Linux kernel from the Grub menu Advanced options for Ubuntu. It may have been a kernel update that caused the problem.

In a few days the developers may put out another kernel update to fix this and then you can stop using Advanced options to load to a desktop.

Regards

---

