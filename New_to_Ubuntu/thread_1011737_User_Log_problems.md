---
title: "User Log problems"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-12-15
I find the following in my user log each time I log in.  Can someone tell me if they are important and if so, how to fix them ??

Dec 15 03:44:47 gettin-desktop bonobo-activation-server (gettin-16190): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ukWgw1rr9H: Connection refused
Dec 15 03:46:22 gettin-desktop pulseaudio[7175]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 15 03:46:22 gettin-desktop pulseaudio[7177]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 15 03:46:22 gettin-desktop pulseaudio[7177]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 15 03:46:37 gettin-desktop pulseaudio[7177]: module-x11-xsmp.c: X11 session manager not running.
Dec 15 03:46:37 gettin-desktop pulseaudio[7177]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by gettinoriginal on 2008-12-15
bump  Please help, this is driving me insane trying to find the fix. :confused:

---

### Post by gettinoriginal on 2008-12-15
I posted a thread about errors earlier:
[http://ubuntuforums.org/showthread.php?t=1011737](http://ubuntuforums.org/showthread.php?t=1011737)

Now my system seems to be slowly deteriorating !!  I no longer have either a user log or backup in /var/logs, my sound is negligable, and every time I log in I have to reset my video driver (Nvidia).  When I do a terminal search of Xorg of any kind, I get a blank page.  Yet here I am, online in Ubuntu typing this.  I have done the gamut of options in reboot ie: fix xorg, repair packages, and fskd.  Heeeeeeeeeeelp please.  ](*,)

---

### Post by bodhi.zazen on 2008-12-15
First please do not start multiple threads on the same topic.

Second, can you give us more details ?

Assuming things were working, and now are not, my guess would be a hard ware problem.

Did you install something ? Version of Ubuntu ? Hardware ?

---

### Post by gettinoriginal on 2008-12-15
First, I apologize for getting impatient, the first thread was getting no response, and things just started getting worse from there.  No, I have not changed anything, no installs, except for trying to get pulse to work.  I checked my user log and got the results I posted, and the next time I logged in, I went to check them to see if pulse was working, and the logs were missing.  I am running compiz, so I thought that may be why bonobo was failing to connect, and was getting my desktop, so wasn't all that worried.  But when I tried to check my xorg files and got blank results, I then started to worry.

I am running 8.10 with compiz/emerald on an Nvidia GeForce FX 5200 which functions well as long as I reset the driver each time.  All updates are applied to the system.

---

### Post by bodhi.zazen on 2008-12-15
The nvidia problem should be easy ...

run :```
gksu nvidia-settings
```

set the resolution / options you want, save settings.

When you save the settings, DO NOT merge with the existing xorg (un check the box).

---

### Post by gettinoriginal on 2008-12-15
Thank you for that, although I wasn't sure about the tick box, as nothing mentioned "merge".

Any info on how to get my user.log back ??

---

### Post by duanedesign on 2009-02-04
I am receiving the same errors in my log. Has anyone been able to shed any light on this.

I found this bug report.
[https://bugs.launchpad.net/ubuntu/+s...bo/+bug/293970](https://bugs.launchpad.net/ubuntu/+s...bo/+bug/293970)
It only mentions the bonobo error and no mention of the following pulseaudio errors.

Also there is this thread started by someone with the same errors in their log.
[http://ubuntuforums.org/showthread.php?p=6673296#post6673296](http://ubuntuforums.org/showthread.php?p=6673296#post6673296)

Feb 3 18:56:23 duanedesign-laptop bonobo-activation-server (duanedesign-4830): could not associate with desktop session: Failed to connect to socket /tmp/dbus-QF8gjDTYCr: Connection refused
Feb 3 19:29:15 duanedesign-laptop pulseaudio[4733]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 3 19:29:15 duanedesign-laptop pulseaudio[4737]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 3 19:29:15 duanedesign-laptop pulseaudio[4737]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 3 19:29:15 duanedesign-laptop pulseaudio[4737]: alsa-util.c: Cannot find fallback mixer control "Mic".
Feb 3 19:29:31 duanedesign-laptop pulseaudio[4737]: module-x11-xsmp.c: X11 session manager not running.
Feb 3 19:29:31 duanedesign-laptop pulseaudio[4737]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.

---

