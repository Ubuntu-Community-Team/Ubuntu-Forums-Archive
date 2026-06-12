---
title: "Citrix Window Size"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by alanwalterthomas on 2014-06-23
I followed these instructions [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo) -> Citrix Receiver 13.0 on Ubuntu 13.10 64-bit.
The connection works.
The problem is with the Window Size.
My monitor is 1920x1200, and the resolution sent is also that, but the unity top & side bars get in the way, and I have to scroll up to close a window, then down to press the start button, etc. I would love to be able to set the resolution requested to something like 1800x1080, but I can't. I tried setting "DesiredVRes=1080" & "DesiredHRes=1800" in /opt/Citrix/ICAClient/config/All_Regions.ini, but that had no effect.

Any ideas how to make that setting stick?

---

### Post by alanwalterthomas on 2014-06-23
I guess I already solved my own problem!
This webpage helped out: [http://www.ingmarverheij.com/the-citrix-ica-file-explained-and-demystified/](http://www.ingmarverheij.com/the-citrix-ica-file-explained-and-demystified/)
It was only necessary to set TWIMode is set to Off / False for the desired resolution to be used. Just open the All_Regions.ini file and search for TWIMode.

---

