---
title: "Easist way to share files on Ubuntu with OpenELEC"
date: 2016-08-30
forum: Networking &amp; Wireless
---

### Post by Arminius on 2016-08-30
Tried googling around, most are solutions on windows, the few linux ones I found seem to be out of date.
I have my Raspberry pi which has openelec on it, on the same WIFI as my PC which has ubuntu on it.
I want to watch the videos on my Raspberry pi which are currently on a folder on my PC.
Sounds easy but I've spent hours trying and failing to make this happen.

---

### Post by howefield on 2016-08-30
You could share the folder on the Ubuntu PC that has the videos (right click the folder in Nautilus/Files and select Local Network Share - might be slightly different terminolgy depending on the Ubuntu version) and then configure in OpenELEC by clicking on Videos on the main menu, then Add Videos and browse to the share folder. That's a brief summary of how you could do it but if you need more info just ask.

You could also alternatively ssh into OpenELEC and copy the videos over to the pi.

---

