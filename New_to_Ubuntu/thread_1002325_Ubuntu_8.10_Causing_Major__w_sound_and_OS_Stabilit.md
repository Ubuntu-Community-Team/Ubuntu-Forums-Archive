---
title: "Ubuntu 8.10 Causing Major  w/ sound and OS Stability"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by DDurcsak on 2008-12-04
To any and all:

Loaded 8.10 shortly after it came out.  OS specs:
UBUNTU:  2.6.27-7 / 8.10 
and system started to act up almost right away.

I had started with Ubuntu 8.04 and everything worked fine..system screamed.

Problem was first noted when playing video on Firefox (3.0.4) and there was **no sound**.  I checked Sound Preferences and when I ran test the following msg came up:

[B]audiotestsrc wave=sine freq=512! 
audioconvert ! audiosample ! gconfaudiosink: 
Failed to connect stream; invalid argument 
[/B]
Can not close out error box.

Another issue is that some applications will hang and system has to be hard rebooted.

I then went to the User.Log and found this for each day after I loaded 8.10 Ubuntu:

User.log

[B]Nov 30 14:51:23 david-desktop bonobo-activation-server (david-8491): could not associate with desktop session: Failed to connect to socket /tmp/dbus-DUG18Hzx13: Connection refused
Nov 30 14:51:28 david-desktop bonobo-activation-server (david-8685): could not associate with desktop session: Failed to connect to socket /tmp/dbus-DUG18Hzx13: Connection refused
Nov 30 17:09:27 david-desktop pulseaudio[7134]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 30 17:09:27 david-desktop pulseaudio[7136]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 30 17:09:27 david-desktop pulseaudio[7136]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 30 17:09:27 david-desktop pulseaudio[7136]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Nov 30 17:09:27 david-desktop pulseaudio[7136]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0"): initialization failed.
Nov 30 17:09:51 david-desktop pulseaudio[7136]: module-x11-xsmp.c: X11 session manager not running.
Nov 30 17:09:51 david-desktop pulseaudio[7136]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 30 17:13:33 david-desktop compiz.real: *** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x0928a8d8 ***
Nov 30 17:13:38 david-desktop bonobo-activation-server (david-7933): could not associate with desktop session: Failed to connect to socket /tmp/dbus-HYMu1aOJFo: Connection refused
Dec  1 22:58:55 david-desktop pulseaudio[6035]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  1 22:58:55 david-desktop pulseaudio[6037]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  1 22:58:55 david-desktop pulseaudio[6037]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  1 22:58:55 david-desktop pulseaudio[6037]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Dec  1 22:58:55 david-desktop pulseaudio[6037]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0"): initialization failed.
Dec  1 22:59:19 david-desktop pulseaudio[6037]: module-x11-xsmp.c: X11 session manager not running.
Dec  1 22:59:19 david-desktop pulseaudio[6037]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.
Dec  2 08:14:07 david-desktop bonobo-activation-server (david-14473): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ZHvbRq2Nya: Connection refused
Dec  2 08:31:33 david-desktop pulseaudio[6448]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  2 08:31:33 david-desktop pulseaudio[6450]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  2 08:31:33 david-desktop pulseaudio[6450]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  2 08:31:33 david-desktop pulseaudio[6450]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Dec  2 08:31:33 david-desktop pulseaudio[6450]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0"): initialization failed.
Dec  2 08:31:57 david-desktop pulseaudio[6450]: module-x11-xsmp.c: X11 session manager not running.
Dec  2 08:31:57 david-desktop pulseaudio[6450]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.
Dec  3 22:50:52 david-desktop compiz.real: *** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x08250e30 ***
Dec  3 22:50:52 david-desktop bonobo-activation-server (david-4266): could not associate with desktop session: Failed to connect to socket /tmp/dbus-LoSSiRcl5I: Connection refused
Dec  3 22:50:57 david-desktop bonobo-activation-server (david-4513): could not associate with desktop session: Failed to connect to socket /tmp/dbus-LoSSiRcl5I: Connection refused
Dec  3 22:52:52 david-desktop pulseaudio[6137]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  3 22:52:52 david-desktop pulseaudio[6139]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  3 22:52:52 david-desktop pulseaudio[6139]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  3 22:52:52 david-desktop pulseaudio[6139]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Dec  3 22:52:52 david-desktop pulseaudio[6139]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0"): initialization failed.
Dec  3 22:53:16 david-desktop pulseaudio[6139]: module-x11-xsmp.c: X11 session manager not running.
Dec  3 22:53:16 david-desktop pulseaudio[6139]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.[/B]

---

### Post by ethoxyethaan on 2008-12-04
Hi try setting the audio setting to ALSA,

in gstreamer-properties 

(you can enter this by typing gstreamer-properties  in terminal or by pressing ctrl + F2) 

change the settings to alsa and try again.

i hope my post was helpfully.

---

### Post by sterne on 2009-01-21
I'd just like to add that I'm seeing the same errors in my log file.
Loads of PulseAudio stuff and Bonobo-activation stuff.

I've not noticed anything actually broken, I was just investigating why my computer had a sluggish boot, and came across these error messages

---

### Post by duanedesign on 2009-02-03
I am receiving the same errors in my log. Has anyone been able to shed any light on this.

I found this bug report. 
[https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970](https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970)
It only mentions the bonobo error and no mention of the following pulseaudio errors.

Feb  3 18:56:23 duanedesign-laptop bonobo-activation-server (duanedesign-4830): could not associate with desktop session: Failed to connect to socket /tmp/dbus-QF8gjDTYCr: Connection refused
Feb  3 19:29:15 duanedesign-laptop pulseaudio[4733]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  3 19:29:15 duanedesign-laptop pulseaudio[4737]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  3 19:29:15 duanedesign-laptop pulseaudio[4737]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  3 19:29:15 duanedesign-laptop pulseaudio[4737]: alsa-util.c: Cannot find fallback mixer control "Mic".
Feb  3 19:29:31 duanedesign-laptop pulseaudio[4737]: module-x11-xsmp.c: X11 session manager not running.
Feb  3 19:29:31 duanedesign-laptop pulseaudio[4737]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by why2jjj on 2009-03-12
Does anyone have a fix for this??  If so, could it be posted please?  I experience the error reported in the url posted ([https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970](https://bugs.launchpad.net/ubuntu/+source/bonobo/+bug/293970)) exactly as I use a KVM switch.  Thanks!

---

### Post by tomthumb99 on 2009-03-23
Folks, any answer here?  This is an old post, but I am getting the same error.  Major Nautilus and Bonodo conflicts upon boot/startup ( clean/error free only 50%).  Sound does work at a very very low volume if it's a clean boot.  I do not need sound, much rather have stable OS.

Thanks,

---

### Post by Gidgidonihah on 2009-03-26
I too am getting errors like this and having random freezes requiring hard reboot. Would LOVE to have a stable OS. Any ideas?

---

### Post by markbuntu on 2009-03-26
Go to System/Adminstration/Users and Groups. Add root and your users as members of the following groups

pulse
pulse-rt
pulse-access

logout and login or reboot.

This is a common problem with new Intrepid installs and upgrades from Hardy. To get pulseaudio set up correctly go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you have more problems go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by alex_o on 2009-04-05
[http://en.wikipedia.org/wiki/Dynamic_loading](http://en.wikipedia.org/wiki/Dynamic_loading)

dynamic loading/dlopen loader is the error! its trying to open it so the solution:

change the runlevel! ofcourse you will loose startup music but who cares! this has bin crashing my system for a few days know :mad:] (*,)

):P

---

