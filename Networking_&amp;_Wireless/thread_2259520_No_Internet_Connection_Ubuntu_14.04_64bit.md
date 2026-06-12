---
title: "No Internet Connection Ubuntu 14.04 64bit"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by robert145 on 2015-01-04
I installed Ubuntu over windows 7 today *I am new* and my drive is cleaned.

I have an Crosshair V Motherboard which i use the onboard port for the internet cable

I do not have wireless

I have a Dlink Router

Tried 2 cables


I've tried downloading wicd 1.7.3, I googled how to manually add a package, I configure it but after i do sudo python setup.py install it says Installing but then gives an error something like "inside dirct Init something Debian and doesnt install


I can not install anything from the Ubuntu Manager like Wicd because i have no internet connection. 

I have a connecting network that stays connecting that's Marllow? Ethernet Giga 

I've tried making a Ethernet thing in the networking

I don't know how to save terminal posts or Copy, if i could i would put it on a usb to bring over to this computer

in the Ifconfig - a i have 400 bytes or something under the eth0 if that means something just no internet?

Ask away for any extra info I will get back hastily

---

### Post by TheFu on 2015-01-05
**lshw -C network**
Please.

You can redirect output  to a file with **tee**.
**lshw -C network| tee /tmp/net-output** - this only gets stdout, not stderr. Do the same for ifconfig.

You've done some amazing things and provided good background info. Usually this stuff "just works".  Does the networking work under a liveCD boot (not the install)?

---

