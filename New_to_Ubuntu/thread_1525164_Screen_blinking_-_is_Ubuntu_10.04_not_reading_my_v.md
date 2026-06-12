---
title: "Screen blinking - is Ubuntu 10.04 not reading my video card correctly?"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2010-07-06
Hi,
I made a post last week about Ubuntu possibly not reading my video card properly.

Note: computer specs are in signature (I am using 10.04 not 9.04, can't figure out how to change my signature).

The issue is that my screen blinks frequently. I am currently using Compiz features and the blinking is somewhat of a nuisance and concern.

---

### Post by Nano Geek on 2010-07-07
Have you installed the proprietary Nvidia drivers?

---

### Post by benjamin.s.vaccaro on 2010-07-07
I believe so...

System -> Administration -> Hardware Drivers:
NVIDIA accelerated graphics driver (version 173): Activate
NVIDIA accelerated graphics driver (version 96): Activate
NVIDIA accelerated graphics driver (version current) [Recommended]: currently in use.


Upon installation of ubuntu 10.04 64bit I installed and activated version 173, rebooted. That did not seem correct so I installed 96, activated and rebooted. Then I tried the recommended and that is what I am currently using.

It may seem stupid that I tried the recommended last, but I was advised to do so. Another miscommunication in online support possibly.

---

### Post by Nano Geek on 2010-07-07
I did a Google search, and I found this.
[http://forums.fedoraforum.org/showthread.php?t=205368](http://forums.fedoraforum.org/showthread.php?t=205368)
Try what the last post suggests. It might fix your problem.

---

### Post by benjamin.s.vaccaro on 2010-07-07
That code is 2008 and isn't dword a microsoft registry? 

I just ask because I don't want to mess with video files, restart and not come back :X

I typed sudo nano -w /etc/modprobe.conf and modprobe.conf is empty. 

In my file System for modprobe.conf I have:
modprobe.conf
modprobe.conf
modprobe.conf
modprobe.conf
modprobe.conf.5.gz
noALSA.modprobe.conf
noOSS.modprobe.conf

---

### Post by Nano Geek on 2010-07-07
I don't have linux in front of me, but can't you do cp /etc/modprobe.conf /etc/modprobe-old.conf before you start and move it back if something goes wrong? Also, I think that code might work. It's from the Fedora forums, and they seem to describe the same problem you're having.

---

### Post by benjamin.s.vaccaro on 2010-07-08
There are a myriad of issues popping up right now with this install. I am going to reinstall the OS tomorrow and not install compiz for a few days. 

I didn't really change anything to the OS except download compiz and change the theme so I believe this is a bad install.

---

### Post by Nano Geek on 2010-07-09
ok. Let me know how things turn out.

---

### Post by ov3rcl0ck on 2010-07-09
There could be multiple things breaking your drivers right now, heres a few:

[LIST=1]
[*]You updated your kernel and never reinstalled drivers
[*]You are using really really old drivers not compiled to work with the current kernel (latest drivers in kernel is 195 i think)
[*]You have the Nouveau and/or NV display drivers installed
[*]Your xorg.conf file is all scrambled
[/LIST]

It doesn't sound like #1 is your problem, but I have somethings for you to try.

Try this series of commands:
```

sudo apt-get purge xserver-xorg-video nouveau xserver-xorg-video-nv
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig

```
That will uninstall conflicting drivers, install the latest nvidia drivers(well latest in the repos), and configure your xorg.conf file to use nvidia.

However you may get a problem where the Nvidia module/driver won't load, in this case your old Nvidia drivers are still left from previous driver installs and they are loading first.

I just had this problem yesterday when I tried to test out the new Nouveau drivers see how well the 3D worked, then all hell broke loose when I tried to install the nvidia drivers back.

If that doesn't work just post back and I'll help you out.

---

### Post by steveneddy on 2010-07-09
If that video driver is giving you issues then simply switch drivers and restart and see if that resolves your issue.

---

