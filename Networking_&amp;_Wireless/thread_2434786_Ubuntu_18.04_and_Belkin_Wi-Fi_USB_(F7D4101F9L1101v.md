---
title: "Ubuntu 18.04 and Belkin Wi-Fi USB (F7D4101/F9L1101v1 BCM4323) Driver Issues"
date: 2020-01-10
forum: Networking &amp; Wireless
---

### Post by salmmus on 2020-01-10
ID 050d:615a Belkin Components F7D4101/F9L1101v1 Wireless Adapter [Broadcom BCM4323]

Hi there. I am trying to install the Belkin F9L1101v1 usb wi-fi that has the Broadcom BCM4323 chip on Ubuntu 18.04. I have tried numerous solutions and installations to no avail. I have tried ndiswrapper as well. The ndiswrapper was installed succefully and the Belkin drivers were added to it and "sudo modprobe ndiswrapper" completes succesfully.
Shows under lsusb: YES
Shows up in lwconfig: NO
I have a usb wi-fi+bt adapter (Edimax) that is in use. Before I add a bunch of command lists, I will await instructions to prevent clutter on this initial post.

---

### Post by CelticWarrior on 2020-01-10
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

This are the instructions. It's a sticky thread in the very same section you posted. ;)

---

### Post by salmmus on 2020-01-10
Thanks CelticWarrior. Unfortunately, that post was for PCI cards.

---

### Post by praseodym on 2020-01-11
Please run the wireless script from the sticky thread and show the output

---

### Post by chili555 on 2020-01-11
The answer is that you probably cannot.

ndiswrapper the package hasn't been updated regularly and not at all for some ten months. Questions on their own help forum go unanswered: [https://sourceforge.net/p/ndiswrapper/discussion/323167/thread/dd8b33b1/](https://sourceforge.net/p/ndiswrapper/discussion/323167/thread/dd8b33b1/)

As well, the Windows XP inf and sys files that ndiswrapper require are also quite old, dating to 2009. 

While there are a few threads reporting success, they are all with older kernel versions, 3.13-xx or so. While it is tempting to simply install an older Ubuntu version, these versions are, or will be soon, End-of-Life and will no longer receive any updates inluding critical security updates. As well, there is no guarantee that the specific Ubuntu version you pick will actually work properly with ndiswrapper.

On the other hand, for a few dollars, you could buy a fully supported, plug in and connect USB wireless. These sites will be helpful in selecting one: [https://ubuntuforums.org/showthread.php?t=2309068](https://ubuntuforums.org/showthread.php?t=2309068) and: [https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux) 

I am unaware of *any* Broadcom USB devices that can be made to work correctly *by any means* in a modern kernel version.

I regret that I do not have better news.

---

### Post by salmmus on 2020-01-11
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the output

Is there a way to reply under your post? Not sure how it all works. Anyways, I'm not sure what script you are referring to. If it is the first one (lspci -nn -d 14e4) , It comes up with nothing.

---

### Post by salmmus on 2020-01-11
> **chili555 said:**
> The answer is that you probably cannot.

ndiswrapper the package hasn't been updated regularly and not at all for some ten months. Questions on their own help forum go unanswered: [https://sourceforge.net/p/ndiswrapper/discussion/323167/thread/dd8b33b1/](https://sourceforge.net/p/ndiswrapper/discussion/323167/thread/dd8b33b1/)

As well, the Windows XP inf and sys files that ndiswrapper require are also quite old, dating to 2009. 

While there are a few threads reporting success, they are all with older kernel versions, 3.13-xx or so. While it is tempting to simply install an older Ubuntu version, these versions are, or will be soon, End-of-Life and will no longer receive any updates inluding critical security updates. As well, there is no guarantee that the specific Ubuntu version you pick will actually work properly with ndiswrapper.

On the other hand, for a few dollars, you could buy a fully supported, plug in and connect USB wireless. These sites will be helpful in selecting one: [https://ubuntuforums.org/showthread.php?t=2309068](https://ubuntuforums.org/showthread.php?t=2309068) and: [https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux) 

I am unaware of *any* Broadcom USB devices that can be made to work correctly *by any means* in a modern kernel version.

I regret that I do not have better news.

Thanks for the info. Yeah, I knew it was pretty old but I thought that I might be able to use it since I already have it. Although it is still possible that it could work, I haven't figured it out yet and I probably won't. I will most likely have to get one that actually works with Linux.

---

### Post by praseodym on 2020-01-12
> **salmmus said:**
> Is there a way to reply under your post? Not sure how it all works. Anyways, I'm not sure what script you are referring to. If it is the first one (lspci -nn -d 14e4) , It comes up with nothing.

This one

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

