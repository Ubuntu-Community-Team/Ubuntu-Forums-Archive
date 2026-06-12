---
title: "MSI ex620 help!"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-10-10
hi, i'm helping a friend find out the wonder that is ubuntu.  the only thing not working is the sound.  i found a place to fix the sound (editing sudo gedit /etc/modprobe.d/alsa-base.conf and adding at the bottom - options snd-hda-intel model=targa-dig).  but the mic wont work, and i can't seem to find a way to fix it...

please help convert another person!
thx

---

### Post by mörgæs on 2010-10-10
Hi, which versions of Ubuntu have you tried?

---

### Post by daveboy23 on 2010-10-10
ubuntu 10.10 and linux mint

---

### Post by mörgæs on 2010-10-10
How does it work with 10.04?

---

### Post by sandyd on 2010-10-10
> **daveboy23 said:**
> hi, i'm helping a friend find out the wonder that is ubuntu.  the only thing not working is the sound.  i found a place to fix the sound (editing sudo gedit /etc/modprobe.d/alsa-base.conf and adding at the bottom - options snd-hda-intel model=targa-dig).  but the mic wont work, and i can't seem to find a way to fix it...

please help convert another person!
thx
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/463708](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/463708)

---

### Post by daveboy23 on 2010-10-11
yeah, i found that, but couldn't get the mic to work, just the speakers

---

### Post by sandyd on 2010-10-11
> **daveboy23 said:**
> yeah, i found that, but couldn't get the mic to work, just the speakers
yeah, I know. its still a bug, which means your mic wont work until someone decides to look into it.

---

### Post by daveboy23 on 2010-10-11
ohhh, ok.

thx then for your time

---

