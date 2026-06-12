---
title: "Won't boot due to display problems"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by tomp749 on 2009-08-01
Hi All,

I'm new to Ubuntu and was trying to set my system up for multi-monitors in display settings, when I reset it boots up about halfway then the screens messes up, wrong resolution/refresh I guess? This is as far as it gets.

I have tried xfix in recovery mode which doesn't seem to work, other threads tell me to use dpkg-*reconfigure xserver*-*xorg* which also doesn't work, just gives me some keyboard options!?!?!

I'm happy to go back to one screen as that is all I need!

Help... thanks in advance:confused:

---

### Post by jacklinux on 2009-08-01
Does your moniter have a 'Auto Correction' feature. when i first boot up after i install something my moniter is over to the left, i hit that button and it goes back to normal.

---

### Post by wojox on 2009-08-01
Disconnect the second monitor reboot try:

```
sudo dpkg-reconfigure -phigh xorg-xserver
```

---

### Post by tomp749 on 2009-08-01
Hi,

The second 'monitor' is a TV through the s-video, which seems to work on most of the boot until the main monitor goes all garbled and the tv blank. I'm pretty sure it does have an auto-correction feature.

sudo dpkg-reconfigure -phigh xorg-xserverthis doesn't seem to work 'xorg-xserver not installed', I've read that xserver doesn't have a feature to change the display settings anymore?!?

---

### Post by W4l0ck on 2009-08-01
There is your problem, take the cord out while booting.  You have 2 masters and 0 slaves.

---

### Post by tomp749 on 2009-08-01
It doesn't seem to make any difference whether the second is plugged in or not

---

