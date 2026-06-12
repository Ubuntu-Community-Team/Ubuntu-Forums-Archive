---
title: "Computer Won't Wake Up"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-04-22
Am running Ubuntu 8.10 and have set it up dual boot with Windows XP. After the computer is left alone for about 30 minutes it goes to sleep; i.e. only activity is the screen saver. When the mouse or spacebar is moved nothing happens and I have to do a complete shutdown and reboot the system. My power management is set up with the original defaults; i.e. Computer never goes to sleep and display shuts down after 45 minutes.

Here is a copy of the system log immediately after I had to reboot the system. 

Apr 22 06:36:03 rog3236-desktop pulseaudio[5041]: ltdl-bind-now.c: Failed to find original dlopen loader.

Apr 22 06:36:03 rog3236-desktop pulseaudio[5046]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted

Apr 22 06:36:03 rog3236-desktop pulseaudio[5046]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

Apr 22 06:36:29 rog3236-desktop pulseaudio[5046]: module-x11-xsmp.c: X11 session manager not running.

Apr 22 06:36:29 rog3236-desktop pulseaudio[5046]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

Apr 22 06:37:40 rog3236-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 

Apr 22 06:37:42 rog3236-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 

Apr 22 07:16:03 rog3236-desktop pulseaudio[5044]: ltdl-bind-now.c: Failed to find original dlopen loader.

Apr 22 07:16:03 rog3236-desktop pulseaudio[5046]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted

Apr 22 07:16:03 rog3236-desktop pulseaudio[5046]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

Apr 22 07:16:29 rog3236-desktop pulseaudio[5046]: module-x11-xsmp.c: X11 session manager not running.

Apr 22 07:16:29 rog3236-desktop pulseaudio[5046]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

Apr 22 07:17:41 rog3236-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 

Apr 22 07:17:44 rog3236-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 

Any help would be appreciated.

---

### Post by sydbat on 2009-04-22
Disable the screensaver, then change the power option to turn off monitor after 5 minutes. Wait for the monitor to go off and see if moving your mouse will turn it back on. If this works, it is something with the screensaver.

I never use the screensaver because it always messed up something, but have never had a problem (yet) with simply powering down the monitor.

---

