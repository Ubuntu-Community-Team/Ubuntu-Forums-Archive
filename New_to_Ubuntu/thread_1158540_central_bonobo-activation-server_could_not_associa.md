---
title: "central bonobo-activation-server could not associate with desktop session"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by chinaski on 2009-05-13
Ubuntu 9.04 64bit fresh install on Intel core 2 duo

Today I found out that if I visit this site:

[http://www.tim.it/consumer/o65726/tariffa.do](http://www.tim.it/consumer/o65726/tariffa.do)

Which is an italian ISP website, I am suddenly logged out as user and when I logged back in and checked log viewer (user.log section) I found this output:
```

May 14 01:13:07 central bonobo-activation-server (chinaski-5036): could not associate with desktop session: Failed to connect to socket /tmp/dbus-J2njecUTUJ: Connection refused
May 14 01:13:16 central pulseaudio[5226]: pid.c: Stale PID file, overwriting.
```Now I guess this issue has to do with some objects in the webpage, probably an audio or audio/video autoplay file that causes this mess, but I see pulseaudio was responsible for flash video files problem (issue was if I had two different flash video streaming site open and switch from one to another for playing videos, at one point I had no more sound until I killed pulseaudio process) on 8.10, it is apparently responsible for skype using nearly 100% processor resources and it is involved in this brutal log out loop, and believe me I was scared to death for few seconds thinking about hardware failure as since september 2005, when I discovered Ubuntu and started using it, I cannot recall such problems with it.

I am asking if anyone knows problem source and possible fix

cheers,
Cris

---

### Post by CocaFR on 2009-05-19
Hello, 

I have exactly the same problem with a ubuntu 8.10 updated in 9.04 for i386. My session crashes one or twice times by day. But I didn't find any solution for now :(


```

May 19 12:05:45 quentin-laptop kernel: [ 9784.674396] [drm] Num pipes: 2
May 19 12:05:49 quentin-laptop kernel: [ 9788.317747] [drm] Setting GART location based on new memory map
May 19 12:05:49 quentin-laptop kernel: [ 9788.320611] [drm] Loading R400 Microcode
May 19 12:05:49 quentin-laptop kernel: [ 9788.320655] [drm] Num pipes: 2
May 19 12:05:49 quentin-laptop kernel: [ 9788.320667] [drm] writeback test succeeded in 1 usecs
May 19 12:05:52 quentin-laptop bonobo-activation-server (quentin-16339): could not associate with desktop session: Failed to connect to socket /tmp/dbus-pB61CIGl4c: Connection refused
May 19 12:05:59 quentin-laptop pulseaudio[16434]: pid.c: Stale PID file, overwriting.

```

---

### Post by bleet on 2009-06-19
I have what appears to be the exact problem. It *almost* seems random, but the most recent one (today) happened as soon as I tried to play streaming radio in VLC.

Basic specs:
Dell D630 Laptop, 3GB RAM, 100GB drive.
Docking station + DVI and VGA monitor, NVIDIA driver + Twinview enabled.

----
Jun 19 09:49:37 bleet-laptop bonobo-activation-server (bleet-10322): could not associate with desktop session: Failed to connect to socket /tmp/dbus-oZcghu5Vi7: Connection refused
Jun 19 09:49:42 bleet-laptop bonobo-activation-server (bleet-10421): could not associate with desktop session: Failed to connect to socket /tmp/dbus-oZcghu5Vi7: Connection refused
----

This is a fairly recent problem, within the past 3 - 4 days. Possible related to some updates that I didn't necessarily pay close attention to. I update almost daily so it might be possible to track down if it was related to one.

---

### Post by gentracer on 2009-08-26
I am having the exact same problem.  

Previous attempts to fix this have been to turn off compbiz and to add an entry to the X11/xorg.conf file, Option		"AccelMethod" "UXA".  

Those seemed to have worked for a while and then today another crash.

I am SO sick of this - any ideas on a real fix would be really appreciated!!

I don't do anything special from a graphics perspective, although it does appear that I have pulseaudio messages in the log files.  I was on Skype this morning - could that be the cause??

Help!

Thanks.

---

### Post by brathk on 2009-11-29
I too had the same problem where I get this error and I see my session getting killed after I did an 8.10 upgrade and it persisted even after I upgraded it to 9.04. While doing the post upgrade checks my data, I noticed that I did not enabled the new kernel that came with the upgrades. I  retained my old /boot/grub/menu.lst so that I dont need to reconfigure my dual boot setup. but this file had  old kernel in it ( 2.6.22.14) as I did not change its reference to new kernel. After pointing to new kernel version (2.6.26.16 in my case), and reboot, I stopped seeing this problem. For me it got resolved.

---

### Post by rello on 2009-12-04
I was experiencing something similar.  In my case, shortly after upgrading to 9.10, I could no longer login at all.  At first a power cycle would fix it, then it did not matter if the PC was power-cycled or anything.  Every time I tried to login, I was immediately kicked out.  This was the error message:

**bonobo-activation-server** (abc-2666): **could not associate with desktop session: Failed to connect to socket** /tmp/dbus-IsgN6ywkMs: Connection refused

This was most frustrating.  After reading the Forums, I decided to try to get rid of bonobo and that meant switching to xfce.  Basically getting rid of the ubuntu-desktop and using xubuntu-desktop instead.  Maybe not the solution for everyone, but it works for me on my limited memory (512) and slower CPU...

Here is what I did as root:
aptitude update
aptitude install xubuntu-desktop
aptitude remove ubuntu-desktop

---

