---
title: "USB headset won't work on Ubuntu"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Mettel on 2009-11-20
Hi I've been using Ubuntu for about a month or two.


I do not have speakers so I haven't had to worry about sound for some time. Now I want to get a USB headset working for a gaming speak client but I can't get any sound out of the headphones speakers using anything (firefox, a downloaded mp3, etc.)

I've searched these forums up and down for help and here is what I've done so far:

1. set USB headset to primary device

```
cat /proc/asound/modules
```now shows
```
 0 snd_usb_audio
 1 snd_emu10k1
```2. I made sure that sound is not muted for the device and turned all the way up using the following code.

```
alsamixer
```3. I downloaded PulseAudio and tried to get it working through there.

NOTE: The gamimg speak client I am using requires that I use PulseAudio

---

### Post by Mettel on 2009-11-20
wow right after I posted this thread I changed 1 setting in Preferences>Sound and it now works.

been working on this for a few weeks so am now quite happy :D

---

