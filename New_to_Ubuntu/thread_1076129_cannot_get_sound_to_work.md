---
title: "cannot get sound to work"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by dragon_reborn on 2009-02-21
Hi, I have installed Mythbuntu 8.10. and everything works but the sound. I have a Sound Blaster Xfi USB soundcard. If I enter aplay -l it displays my soundcard as below:

**** List of PLAYBACK Hardware Devices ****
E: client-conf-x11.c: XOpenDisplay() failed
card 1: S51 [SB X-Fi Surround 5.1], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: S51 [SB X-Fi Surround 5.1], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

However if I enter alsamixer I get this:

andre@homeserver:/media/MyBook/downloads$ alsamixer
E: client-conf-x11.c: XOpenDisplay() failed

alsamixer: function snd_ctl_open failed for default: No such file or directory
andre@homeserver:/media/MyBook/downloads$

Can anybody help?

---

### Post by dragon_reborn on 2009-09-20
got this working by reinstalling mythbuntu

---

