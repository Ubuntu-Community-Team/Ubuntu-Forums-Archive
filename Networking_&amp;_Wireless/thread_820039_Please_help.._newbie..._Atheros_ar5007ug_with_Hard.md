---
title: "Please help.. newbie... Atheros ar5007ug with Hardy 8.04 and medion laptop"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by stahoster on 2008-06-05
Wireless not working. Please help. I've been to all forums here, as well as numerous websites and ubuntu help topics all over the Internet and still cannot get my wireless card working. My details:

Medion 96340 laptop
Atheros ar5007ug wlan
AMD Athlon 64 x2 dual-core processor tk-53
dual partition with internet connection on the windows vista (32-bit) partition
no internet connection on the ubuntu partition

I cannot view my wlan card anywhere in Ubuntu, even the network section. Driver not viewable in "hardware drivers" section. I tried to install ndiswrapper with no success.

I really want to use Ubuntu, I'm a newbie, but after a week of trying to connect to the Internet, I'm ready to give up on linux. Please spell out instructions for me as I am still unfamiliar with some of the commands and terms. Also, I was unable to install ndiswrapper because I don't know where to put the files, and how to 'tar'?

Thank you for your help. Ken.

---

### Post by Nzer24 on 2008-07-26
I'm pretty sure that the ar5007ug chipset you have is compatible with the ZyDAS zd1211rw drivers that work very well with linux. I personally have a zd1211 usb card, which works, which was bought out by artheros and renamed. If you can't get a connection, double check the physical device and make sure that it is actually an ar5007ug.

If everything goes well, you should be able to use the card natively, without ndiswrapper.

---

### Post by stahoster on 2008-07-26
> **Nzer24 said:**
> I'm pretty sure that the ar5007ug chipset you have is compatible with the ZyDAS zd1211rw drivers that work very well with linux. I personally have a zd1211 usb card, which works, which was bought out by artheros and renamed. If you can't get a connection, double check the physical device and make sure that it is actually an ar5007ug.

If everything goes well, you should be able to use the card natively, without ndiswrapper.
Thanks for the help nzer24. I was just about to give up on ubuntu because cannot get wireless to work. I will try and hop this works. Question: not sure what file to download the driver file to? Thanks, Ken

---

