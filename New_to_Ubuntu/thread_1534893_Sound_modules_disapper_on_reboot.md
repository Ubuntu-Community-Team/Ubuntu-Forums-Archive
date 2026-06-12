---
title: "Sound modules disapper on reboot"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by pzs on 2010-07-20
(this may not belong in Absolute Beginners - if so, apologies)

I have a Dell Precision T5400. It has two sound cards:

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
09:02.0 Audio device: Creative Labs SB X-Fi

```

For ages, the support for the X-Fi has been weak so I used OSS with the Intel card. This required a bit of hacking to get the GNOME tools to work.

With Lucid, it started up with some X-Fi support, so I used that. Then my machine went down and now it's stopped working entirely. I've followed the various sound guides and the main problem is that the kernel modules for sound are just not there:

```
$ ls -lt /lib/modules/`uname -r`/kernel/sound/  
ls: cannot access /lib/modules/2.6.32-23-generic/kernel/sound/: No such file or directory

```

If I do this:

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

They reappear. Then I can modprobe snd-ctxfi, although it still doesn't show up in aplay -l. I thought maybe if I rebooted it would sort itself out, but actually what happened is that all the sound modules disappeared again.

I could build them myself, but if they're just going to disappear on a reboot, there doesn't seem a lot of point. I could also reinstall OSS and go back to using the Intel card, but the X-Fi does work - it worked for a whole day last week. It's frustrating that it would spontaneously break like that and I'd like to get it sorted out.

Is anybody else having similar problems?

---

### Post by pzs on 2010-07-20
So I've reinstalled the modules again, probed, managed to get a reading out of aplay -l and now when I try to play stuff I get:

```
$ aplay /usr/share/sounds/alsa/Front_Center.wav
ALSA lib pcm_direct.c:1117:(snd1_pcm_direct_initialize_poll_fd) unable to open timer 'hw:CLASS=3,SCLASS=0,CARD=0,DEV=0,SUBDEV=0'
ALSA lib pcm_dmix.c:1087:(snd_pcm_dmix_open) unable to initialize poll_fd
aplay: main:608: audio open error: No such file or directory

```

---

### Post by pzs on 2010-07-20
I've gone back to using OSS on the Intel card, which works fine after I rip out all the ALSA stuff.

I wonder why I bother "up"grading Ubuntu when it always breaks stuff like this. I've had to spend at least an hour getting sound to work on every single dist-upgrade. Also, why they hell am I grovelling around in kernel modules trying to get sound to work in 2010? 

I know these rants "aren't productive", but this stupid problem has taken up several hours of my time. I am an experienced Linux user and when I can't do this, I can't see how a newbie should be expected to cope.

---

