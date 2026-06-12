---
title: "Xorg eating 50% CPU, how do I find out what is causing this?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by jon.reeve on 2009-05-06
I've been using 9.04 UNR for some time now without any problems, but for some reason all of a sudden xorg is using 50%-100% of the CPU, and won't stop. I can't seem to find anything pertinent in the logs. I don't suppose this has anything to do with it? (from the xorg log) 

(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): DRI2 requires UXA

I don't suppose this has anything to do with the recent intel video driver updates? 

At the very least, I'd like to know how to check the processes in greater detail, so that I might be able to figure out exactly what's going on here.

---

### Post by gettinoriginal on 2009-05-06
Have you checked System > Administration > System Monitor > Processes Tab to see what processes/programs/apps might be using the CPU ??

---

### Post by Didius Falco on 2009-05-06
I think you are on the right track with the intel driver issue. Here is a HowTo that may be of use:

[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)

I hope it helps...

Regards,

Didius

On Edit: here are more resources, that are a bit more complex. I'd recommend trying the first one out, and if that doesn't resolve the issue, you can move on to these:

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

