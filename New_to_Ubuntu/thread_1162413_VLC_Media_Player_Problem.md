---
title: "VLC Media Player Problem"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by rvgsd on 2009-05-17
Hi All, 

I changed my color **DefaultDepth **to **16 **to improve my systems performance. The performance is more smooth now, but I cannot play any media file in VLC. I get a green, black or blue screen everytime with the sound working properly. I tried changing the video output to OpenGl but that plays the media with really reduced quality (not watchable!). 

If I change the **DefaultDepth **back to 24 in the xorg.conf, then it works fine, but then my system becomes impossibly laggy and unusable.

Is there any remedy for this problem?

Regards, Rvgsd.
(Pentium IV, 2.4 Ghz single core, 1 Gig RAM.
Ati 7500 radeon mobility graphics card.)

---

### Post by blueridgedog on 2009-05-17
Have you tried it with no desktop effects?  System..Preferences.. Appearance...Desktop effects tab then click none.

---

### Post by alphacrucis2 on 2009-05-17
> **rvgsd said:**
> Hi All, 

I changed my color **DefaultDepth **to **16 **to improve my systems performance. The performance is more smooth now, but I cannot play any media file in VLC. I get a green, black or blue screen everytime with the sound working properly. I tried changing the video output to OpenGl but that plays the media with really reduced quality (not watchable!). 

If I change the **DefaultDepth **back to 24 in the xorg.conf, then it works fine, but then my system becomes impossibly laggy and unusable.

Is there any remedy for this problem?

Regards, Rvgsd.
(Pentium IV, 2.4 Ghz single core, 1 Gig RAM.
Ati 7500 radeon mobility graphics card.)

Which graphics driver are you using?

---

### Post by rvgsd on 2009-05-17
I don't have any desktop effects turned on, I have completely uninstalled compiz. 
I am using the open source drivers which came default with the Ubuntu 9.04 setup, not the fglrx drivers, since they are not meant for ATI Radeon 7500 as its very old. 
Help!!!

---

### Post by alphacrucis2 on 2009-05-17
> **rvgsd said:**
> I don't have any desktop effects turned on, I have completely uninstalled compiz. 
I am using the open source drivers which came default with the Ubuntu 9.04 setup, not the fglrx drivers, since they are not meant for ATI Radeon 7500 as its very old. 
Help!!!

OK. There are two different Open Source drivers. I believe the default one is just called ati. You may want to try the OSS radeonhd driver as explained here:

[https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

Actually I don't know if radeonhd will support your card as it says r5xx, r6xx, r7xx chipsets. It looks like yours may be older again.

---

### Post by rvgsd on 2009-05-19
Nothing seems to work...! Help!!!!!!

---

### Post by rvgsd on 2009-06-19
Bump!

---

