---
title: "tp link wireless usb"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by olddave on 2007-09-22
Hi all hope someone can help just bought tp link tl-wn620g wireless usb adaptor and would like to no how to get it working in ubuntu edgy. Have found some info on the net about copying  some files from the windows insalation cd but where do i install them.
Thanks in advance
olddave

---

### Post by olddave on 2007-09-28
Me again.
finally got it working.  I had to install NDIS wrapper and the Windows Drivers for the USB wireless adapter TL-WN620G.  I had to use the downloaded version not the one provided with the device. copied and installed the following inf files: athfmwdl.inf and tl-wn605.inf.  We now need to know how to "disconnect" the device safely as when simply unplugging the device it takes a lot of messing around and restarting the PC to get it working again.

Whats the command to do the windows equivalent of "Safely remove usb device".

Hope this info helps.

---

### Post by dynamethod on 2007-11-22
Hey there i have exactly the same device "TP-LINK TL-WN620G" and im having a nightmare trying to install it :S

i cannot for the life of me find the tl-wn620g.inf, ive looked in the CD that came with it and even the tp site, but i cannot find it, i have the athfmwdl.inf file, but im very wary about installing these drivers though :S

last time i did i had to reformat because of a "kernel pannick" i couldnt boot my OS no more :S

ive followed this guide myself: [https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29?highlight=%28TP-LINK%29%7C%28TL-WN620G%29](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29?highlight=%28TP-LINK%29%7C%28TL-WN620G%29)

however, i was wondering if you could please state your steps to get your device working, because im really dont feel safe following the guide in the above link, as it fried my pc last time i tried those steps, any help much appreciated!

---

