---
title: "audio issues lucid 10.4"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by stren_g on 2010-07-07
i have an hp compaq nc6000 and just installed ubuntu 10.4. everything works. except the audio. no sound on youtube and such. any ideas?

---

### Post by jtarin on 2010-07-07
Open a terminal and enter ```
alsamixer
``` then adjust your volumes.

---

### Post by stren_g on 2010-07-08
i did that and it said there is no such file or directory

---

### Post by lidex on 2010-07-08
You may need to re-install alsa. Try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

---

### Post by jtarin on 2010-07-08
> **stren_g said:**
> i did that and it said there is no such file or directory
Try ```
sudo alsamixer
```If that works then you will probably need to add user to aduio group.

---

