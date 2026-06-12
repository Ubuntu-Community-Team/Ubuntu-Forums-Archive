---
title: "Wireless stopped working after upgrade"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by laero on 2008-04-26
EDIT: Just want to say that I solved the issue by downgrading to Xubuntu 7.10 "Gutsy Gibbon". After that my wlan-adapter worked out of the box.

Hello all

First off, I'd like to say that i really like Xubuntu, my old laptop suddenly came alive again and before I upgraded to Hardy Heron everything was fine. But after the upgrade (from Gutsy Gibbon to Hardy Heron) my wireless connection stopped working. The nm-applet is able to identify my wireless network, but when I try to connect (via a wpa2 encrypted connection) the little blue dot just goes on and on spinning, nothing happens.

When I used Gutsy Gibbon, I was able to connect to the wlan with the Ralink rt61 driver, but it won't work in Hardy Heron. So I thought there was a problem with the driver, i tried to re-compile it, but that only yielded me this:
```

laero@Xubuntu-laptop:~/RT61_Linux_STA_Drv1.1.0.0/Module$ make all
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/laero/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Går till katalogen "/usr/src/linux-headers-2.6.24-16-generic"
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/laero/RT61_Linux_STA_Drv1.1.0.0
/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stannar.
make[1]: *** [_module_/home/laero/RT61_Linux_STA_Drv1.1.0.0
/Module] Fel 2
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.24-16-generic"
make: *** [all] Fel 2
```

Any ideas how to solve this? I've tried wifi-radar, it is also able to idetify the network but can't connect.

---

### Post by tmarlow on 2008-04-26
I don't have a solution but want to second this.  I installed ubuntu a couple of days ago and am using a laptop that has sat on a shelf for 6 months so I was happy.  I didn't think it would work with my NetGear WPN511 PCMCIA card but I plugged it in anyway.  To my suprise, I didn't have to do anything, the networks were visible and I just had to choose mine and put in the appropriate security information.  I then upgraded last night and all the sudden my wireless card doesn't work after the reboot.  Since it was so easy last time, I have no idea what to do now, I've been using linux for a week now.

-Travis

---

### Post by laero on 2008-04-26
Hm, I'm starting to get the feeling 8.04 contains some major network bug, or maybe the drivers don't work anymore.

---

### Post by dwp0980 on 2008-04-26
Agree - I've been trying all sorts to get this to work since the upgrade.  I just can't seem to crack it. ARGH!

---

### Post by Mr_Arne on 2008-04-27
Hi,
If you search in this forum on "rt61" you will find an unlimited well of threads and posts on different matters related to Ralink drivers - I think it's quite sad that the subject (after a couple of years really) still isn't solved. This seems to be the everlasting pain in the *** for The World Of Linux - it is related to the Kernel carpenters work as well. I don't know if it is politic, priority or any other issue laying behind.
This thread
[http://ubuntuforums.org/showthread.php?t=626246](http://ubuntuforums.org/showthread.php?t=626246)
Worked well for me when I was struggling with Gutsy (Ubuntu) to get things to work. It should be quite generic for all ubuntu distros I guess, so just give it a try.
regards
Ola

---

