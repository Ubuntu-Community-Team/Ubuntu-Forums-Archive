---
title: "X11 nightmare. Please help"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by madu on 2009-02-03
Hey guys,

I think installation of nvclock (0.8b) has screwed my system. I already uninstalled it but there seems to some bad problems. For starters, when I switch on, after selecting Ubuntu from Grub, system gives a long beep like every other time.. I have to manually reboot.. after reboot it starts fine, but after Grub, the screen shows red/white lines and stuff.. but finally arrives at the login screen.. after that operation is fine.. but there are many errors I found on the system log.. I hope somebody can help me.. 

[B]USER.LOG

Feb  4 09:07:09 desktop pulseaudio[6175]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  4 09:07:09 desktop pulseaudio[6178]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  4 09:07:09 desktop pulseaudio[6178]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  4 09:07:32 desktop pulseaudio[6178]: module-x11-xsmp.c: X11 session manager not running.
Feb  4 09:07:32 desktop pulseaudio[6178]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.[/B]


These are the errors I have gotten right after I restarted the system.

Any ideas how to fix the X11?

Thanks in advance guys.

---

### Post by utnubuuser on 2009-02-04
Hi -- try:> sudo dpkg --configure -ain a terminal.

you could also try:> sudo dpkg-reconfigure xserver-xorg

then ctrl+alt+backspace to restart the x-session

---

