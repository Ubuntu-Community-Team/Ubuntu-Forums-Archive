---
title: "A slightly different white screen prpblem"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Snootz on 2009-02-19
I've read much about the white screen problems occuring in ubuntu with ati drivers but my problem seems to be slightly different.  When starting up, i get no login screen at all and am immediately faced with a white flickering screen, there is no mouse cursor or anything. 

system: 
Acer extensa 4420
Radeon xpress 1250 video card
dual core amd 64 bit processor


What I did before.
I'd just installed catalyst 9.1 drivers for my radeon xpress 1250 and it worked fine.  Took me a bit because I'm new but eventually all the control centers and everything were running after reboot.  Then I installed the 285 updates that I needed to upgrade, let that finish, reboot, and white screen.  all the fixes that have come up assume that you can get into the failsafe mode and use your desktop in some fashion.  I can only use the tty command lines.

So here's a list of things i've tried.

after getting to tty1 (ctrl-alt-f1)
- the "dpkg-reconfigure xserver-xorg" fix.  after running this i try startx and get an error that spits me back into the command line.  with 
"```
Saw signal 11. server aborting 
giving up 
errno 111: unable to connect to X server 
xinit: no such process (errno 3)"
```

-since the drivers are installed, i can go run "/usr/bin/aticonfig --initial" again and that gets me back to where i started. A white flickery screen. after hitting ctrl-alt-f1 again though, i get some new errors 
```
(WW)fglrx: no matching device section for instance busID PCI:0@0:numbers) found
FATAL: Module fglrx not found 
(EE)fglrx(0): [FB] Can not get FB MC address range
(EE)fglrx(0): atiddxDriScreenInit failed, GPS not been initialized 
(EE)fglrx(0):XMM failed to open CMMQS connection
(EE)fglrx(0): fireg1_SetSuspendResumeState Failed -9
```

and from here the prompt dissappears.  I think i may have screwed something up in my original attempts to install and configure the drivers, so I'll be reinstalling by the end of the day if I can't fix this. I've only just installed ubuntu so I'm not losing much. I'd just like to prevent this from happening again.

---

### Post by blueridgedog on 2009-02-22
I have no great wisdom to fix your install, but a question and an observation.  Question:  Can you run the live CD and get into X?  

If so, then I would re-install and NOT install the ATI drivers.  I have had similar issues with ATI and simply ditched the card and put in an NVIDIA card.  ALL of my graphics issues are now resolved and I can watch multiple video streams with high end desktop graphics running.

---

