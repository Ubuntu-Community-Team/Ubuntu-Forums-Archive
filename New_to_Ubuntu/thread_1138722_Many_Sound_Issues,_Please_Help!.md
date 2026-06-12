---
title: "Many Sound Issues, Please Help!"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by amor0fati on 2009-04-26
For as long as I've had Ubuntu, I haven't been able to record sound at all.  My audio card is a Sound Fusion CS46xx.  I can get sound in an out of the card, as in, audio generally works for all applications (until recently) and I can hear my line in coming through my line out.  The problem is that audacity and sound recorder don't pick up my line in at all, even though I can hear it.  The problems I've been having seem fairly standard from my research, but none of the solutions I've found seem to work.

That's only the beginning of my sound problems.  I recently upgraded to Jaunty, and while I can hear Rhythmbox just fine, neither Flash nor VLC have sound.  I also recently started using a USB audio device:  A Behringer UCA202.  I can get sound in and out of that as well as with the sound card, but no sound with video and still no luck with Audacity.

Before Jaunty, I was using Alsa for all of my sound, but since the upgrade, I haven't been able to.  I've only been able to use OSS, I've mainly been using Burr-Brown from TI USB Audio Codec USB Audio (OSS).  And as far as Audacity or VLC goes, I don't even see an option for this in the audio preferences.

I can't remember all of what I've done to try and fix it, but they've all been fairly standard solutions that seem to work for almost everyone else.  I really just need someone to walk me through possible solutions.

Thanks!

---

### Post by Didius Falco on 2009-04-26
Hi,

Follow this HOWTO. It's pretty much the definitive guide:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working)

Work your way through this, and if you still have any issues, post again. Me, I'd post in that thread[U] 
[/U]

---

### Post by amor0fati on 2009-04-26
Thanks.  This is what I get at the last step of part A:

> $ pulseaudio & pavucontrol
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[1] 8417
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Xlib:  extension "RANDR" missing on display ":0.0".
W: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[1]+  Exit 1                  pulseaudio


---

### Post by amor0fati on 2009-04-26
Some progress has been made.  I can hear VLC and Flash through my sound card on autodetect and alsa.  I can still only hear rhythmbox through my USB device but can now do it with the alsa USB codec.  Why can't I hear the audio from video applications through my USB, and is there any way to get both my USB and soundcard working simultaneously?

Edit:
Audacity is now able to record from my USB device.

---

### Post by amor0fati on 2009-04-28
Seems to be fixed.  I guess a reboot may have solved it.

---

