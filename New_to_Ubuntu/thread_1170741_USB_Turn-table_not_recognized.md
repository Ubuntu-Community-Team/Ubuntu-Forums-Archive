---
title: "USB Turn-table not recognized"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by rtowsley on 2009-05-26
Hi, I have install ubuntu 9.04 and love it. There is one thing I have found not to work. I have a USB connected turn-table for playing records and it is not recognized when I plug it in. Do I need to install a different program?

---

### Post by halitech on 2009-05-26
with the turn table disconnected and connected, can you post the output of
```
lsusb
```

---

### Post by NHArticleTen on 2009-05-26
[http://www.usbturntables.net/](http://www.usbturntables.net/)

---

### Post by rtowsley on 2009-05-26
I used the code lsusb with the turn table plugged in and with it not plugged in and the only difference is
Bus 002 Device 006: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
This tells me it is recognized. How do I get it recognized in Audacity or able to play through sound card?

---

### Post by zobcat on 2009-05-26
quote: The key is in the Audacity set up. You have to pick the input as USB codex and the output as the same. You have to change the output to ALSA to playback.

from this thread: [Audio/Video Capture with ADS Tech devices- I found the answer]("http://ubuntuforums.org/showthread.php?t=497649")

Good luck!

---

