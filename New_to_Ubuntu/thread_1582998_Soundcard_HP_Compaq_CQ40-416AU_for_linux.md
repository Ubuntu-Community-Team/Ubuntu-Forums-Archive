---
title: "Soundcard HP Compaq CQ40-416AU for linux"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by cahpogung on 2010-09-27
I have installed ubuntu 9.04 jaunty, but can't detect my soundcard. i've install amarok and these codec but still no working.
please your help, sorry if my english not good enough.
thank you...O:)

---

### Post by Bölvaður on 2010-09-27
check if your soundcard is detected. it will also be good to know the name of the sound card or motherboard because I cannot seem to find it online.

do you find the sound card or motherboard here?
> lshw

if you dont know then you can just dump all the output here with the code option (click the # sign next to < > and dialog sign when posting)

---

### Post by cahpogung on 2010-09-28
i used 
IDT High Definition Audio CODEC
can you help me??:razz:

---

### Post by Bölvaður on 2010-10-10
> **cahpogung said:**
> IDT High Definition Audio CODEC

This is not a sound card :P
I will need to know the sound card in order to know what to do.
If it isnt there try ```
sudo lshw
``` and look for something that looks like this

> *-multimedia
description: Audio device
product: 82801H (ICH8 Family) HD Audio Controller
vendor: Intel Corporation

obviously your audio device will not be the same one as I have.


Also you should install the latest ubuntu, not an old one that isnt supported any more. Go for either 10.04 or 10.10. The 10.04 is a long term service release but 10.10 has higher odds of having a better driver for your audio card.

---

