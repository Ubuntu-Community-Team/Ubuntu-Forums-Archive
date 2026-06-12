---
title: "&quot;sudo hidd --connect...&quot; does nothing"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by freethinker89 on 2007-07-18
hello,

i've recently installed just about everything i could find in synaptic, in hopes of transferring files from my phone (motorla env) to my laptop.

once they were installed, i restarted the bluetooth services, performed "hcitool scan," and was presented with this:

> ben@ubentu:~$ hcitool scan
Scanning ...
00:19:A1:59:18:CC       enV

everything seemed fine, and i this is the method which allowed me to connect the two devices on my previous install. however, the next command (in every bluetooth guide i've found) is "sudo hidd --connect xx..."  and yes, i know the xx's are supposed to be replaces with the phone's address.

once again, this has worked for me on a previous installation, but that command now seems to do nothing.

> ben@ubentu:~$ sudo hidd --connect 00:19:A1:59:18:CC
ben@ubentu:~$ 

i'm fairly new to linux, so i thought that maybe some of the packages i had installed might be conflicting with each other, so i removed them all and followed [this]("https://help.ubuntu.com/community/BluetoothSetup") guide step-by-step... 

any suggestions?
any/all help would be sincerely appreciated.

---

