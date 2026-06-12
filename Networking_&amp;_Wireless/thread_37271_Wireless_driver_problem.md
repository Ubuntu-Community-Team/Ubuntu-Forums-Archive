---
title: "Wireless driver problem"
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by talon on 2005-05-26
Hey,
I just installed Ubantu on a partition on my hard drive, after not using it for a period of about 3 months. I got a bit annoyed with it as there were no drivers for linux for my wireless adapter, wiped it and installed xp. But I just re-installed it, thinking I would see if I could find a way around the problem. Can anyone help me with the driver problem? I have a belkin Wireless 802.11G USB network adapter, model F5D7050UK
Cheers. :smile:

---

### Post by jkndrkn on 2005-05-26
You don't need a linux-specific driver. Have you tried using ndiswrapper? If not, give this is a shot. It worked for me.

[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

You will need a .inf file provided to you by the Belkin manufacturer. You will find it in the bundle of software included in your install disk. You may also find it in the driver available for you to download from the Belkin website.

---

### Post by talon on 2005-05-27
Right, I have the ndiswrapper installed along with the drivers, but now if I go into networks and try to set up a new network, it doesn't work! I can select the WLan0 device, but it doesn't work ie. the light on my usb device doesn't start flashing, and the network doesn't activate. any ideas?

---

### Post by talon on 2005-05-28
Anyone any ideas?

---

### Post by argotnaut on 2005-05-30
Is there another device listed? If so, try activating that one even if it's not described as a wireless device.

Sometimes my wireless card shows up as eth0 and sometimes as eth1. Sometimes the description is mixed up: it shows up as an Ethernet device, and my Ethernet port is displayed as a wireless device.  :mad:

---

### Post by talon on 2005-05-31
ah, that might be it, 'll try that now and report back. thanks a lot. :)

---

### Post by talon on 2005-05-31
no, there is no second device, unless you count lo. I get that when I type iwconfig into a root terminal. And what's worse, if I try to set up a new wireless network, wlan0 isn't there anymore!
What is going on? :?  ](*,)

---

### Post by sirdef on 2007-01-17
I like many others have had problems installing the belkin f5d7050 driver
:D  but at last solution... i tried ver1 ver2 ver4 drivers which were quite easy to find but did not work...
 then after 3 hours searching i have found a ver3 driver which works  and my wireless dongle is now up and running..
 if you have the same problem visit 


_[http://web.belkin.com/support/article/Default.aspx?lid=en&pid=F5D7050&aid=5381&scid=0](http://web.belkin.com/support/article/Default.aspx?lid=en&pid=F5D7050&aid=5381&scid=0)_

This has ALL drivers for this item...

Good luck

---

### Post by chipdip on 2007-01-17
I still seem to be having problems, with the driver you suggester under ndiswrapper. It installs the driver and all, I select it in the Network Manager, and then it just does not work. Not a clue what could have gone wrong.

---

