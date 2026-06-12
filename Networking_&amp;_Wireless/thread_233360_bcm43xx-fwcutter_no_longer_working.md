---
title: "bcm43xx-fwcutter no longer working"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by nelux on 2006-08-10
I have been using the bcm43xx-fwcutter to get my wireless conecction working. Now all the sudden, it not longer works.

My wireless binds to eth1 when it works. However, now eth1 when executing a ifconfig eth1 down or up an error states that "there is no such device".

has any1 seen this problem? or better if there is a way to fix this?

Thanks in advanced.

Nelo

---

### Post by nelux on 2006-08-10
One more thing to add.  I have followed the steps in  How to: Broadcom Wireless cards howto to get this going back in June.

Nelo

---

### Post by MarkSheely on 2006-08-10
Which Broadcom card do you have?

--Mark

---

### Post by nelux on 2006-08-10
The broadcom driver uses the bcmwl5.sys. driver.

Here is a description from compaq.
This package contains drivers for the listed Broadcom Wireless LAN adapters in the listed notebooks and operating systems.

This driver supports 802.11i/WPA2 for a/b/g and certain b/g WLAN cards. For other cards, it provides Wi-Fi protected access (WPA) support. This driver also supports Cisco Compatible Extensions Program V3.0 features (software supplicant required) and provides support for "125 High Speed Mode" for notebooks with Broadcom 802.11g and 802.11a/b/g cards that support "125M High Speed Mode." 

Sorry, I am not at home to get the actual name of the wireless card.

--nelo

---

### Post by nelux on 2006-08-10
I found another thread with similar information. It seems after a kernel upgrade I starting having this problem.  The other thread has the same error i get. "The problem is I have is already seen by someone else SIOCGIFFLAGS error - no such device"

--Nelo

---

### Post by zirrush on 2006-08-10
my wireless card also uses the bcmwl5 driver (linksys wmp54g).  I never tried using the bcm43xx stuff, but ubuntu tried using it from autodetection. I had always used ndiswrapper in slackware to get it running so stuck with the bread and butter.  That being said, I had similiar problems you could say and resolved them simply by unloading the bcm43xx module and loading ndiswrapper.  Note on ndiswrapper, the version ubuntu has the deb package for is an older version that wouldn't work for me, can download the most recent 1.22 version and give it a shot though (works fine with my card).

You can compile, install, and test out ndiswrapper without setting it to load when linux starts up.  Once you get it installed and your driver installed, bring down your wireless connection, modprobe -r bcm43xx, depmod -a, modprobe ndiswrapper...  if all goes well your wireless connection should show up in iwconfig and you'll know ndiswrapper works before deciding to start using it in place of fwcutter

---

### Post by nelux on 2006-08-11
thank you zirrush.

Went back to ndiswrapper and it works :)

--Nelo

---

