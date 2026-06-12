---
title: "Installing Driver for Netgear WNA3100 Wireless Usb Adapater"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by somehavecalledme on 2014-08-24
I have been trying for quite a while to get a wireless connection working on this Dell XPS M1330. This computer does have a wireless card, but I think it may be broken as none of the commands I've been using in terminal have even recognized it. Thus I'm currently trying to install a driver for a Netgear WNA3100 Wireless USB Adapter. I have had no success unfortunately. I'm currently running Ubuntu 14.04 32-bit from a usb stick (so I haven't actually installed ubuntu). I have tried to install ndiswrapper, but that is my first problem. I added the Universe Repository and entered this into terminal to install ndiswrapper:
```
sudo apt-get install ndiswrapper-common
```
It certainly seems as though ndiswrapper is install since whenever I try to reinstall it says it's the newest version already. However, when I try to install the driver I downloaded using ndiswrapper in terminal, it says:
```
Error: unable to find a version of ndiswrapper!
```
So I'm just hoping someone could guide me through how to properly install a driver for this adapter as I'm very new to ubuntu and mostly clueless. It is also my understanding that this adapter in particular is gernerally a pain to get working, so if someone could help me out that'd be great. Thanks!

---

### Post by somehavecalledme on 2014-08-24
I have tried other methods of installing ndiswrapper, and I have still had no success. I tried to just download the newest ndiswrapper and follow the instructions in the package, but it still fails.

---

### Post by somehavecalledme on 2014-08-25
I hate to keep bumping this thread like this, but I simply cannot figure this out without help.

---

### Post by jeremy31 on 2014-08-25
[http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

You can get the broadcom files you need if ```
lsusb
``` shows it to be
 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]



 ```
wget http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz
```

---

### Post by chili555 on 2014-08-25
I think you also need ndiswrapper-utils-1.9.

---

### Post by Malcolm_Gaissert on 2014-08-25
This will be a lot easier when you remove the dead internal wireless card first. Your setup will work with Windows distros but the Linux will see the dead card and not allow the USB one to function completely.

---

### Post by somehavecalledme on 2014-08-25
Thank you all, I installed that ndiswrapper utils, and was then able to install the driver given. I'm posting using the wireless adapter right now, so thanks.

---

### Post by jeremy31 on 2014-08-25
> **chili555 said:**
> I think you also need ndiswrapper-utils-1.9.

This was on my laptop, perhaps as a dependency of another package?

---

### Post by chili555 on 2014-08-25
To get the whole thing to work, you need common and utils. However, common doesn't show utils as a dependency. That's why somehavecalledme could install common and not have a working install. That's one of many things that aren't apparent to newer users and sometimes trip them up.

The only advantage to being old and having callouses on my mouse fingers is that I'm made all those mistakes a few times myself!!

---

