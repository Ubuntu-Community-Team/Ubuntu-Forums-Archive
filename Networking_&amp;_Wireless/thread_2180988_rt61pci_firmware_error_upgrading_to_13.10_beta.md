---
title: "rt61pci firmware error upgrading to 13.10 beta"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by AndrewWalker on 2013-10-15
I've tried an upgrade to 13.10 beta and it broke my wireless connection. I tried a re-install from scratch and that also failed to work. When I first upgraded it was ok but a recent update, yesterday in fact, caused the initial error. Can anyone confirm this problem? The symptoms are a console spilling out this repeatedly and dmesg full of this:

ieee80211 phy0: rt61pci_load_firmware: Error - MCU Control register not ready

I was under the impression this should work out of the box as the drivers are now in the kernel. Do I need to install firmware or is it a bug that needs reporting?

---

### Post by Sef on 2013-10-17
Moved to Networking and Wireless.

---

### Post by varunendra on 2013-10-17
> **AndrewWalker said:**
> ieee80211 phy0: rt61pci_load_firmware: Error - MCU Control register not ready

Please try a temporary parameter. In a terminal (Ctrl-Alt-T) -
```
sudo modprobe -rv rt61pci
sudo modprobe -v rt61pci nohwcrypt=Y
```
..and try to connect. Does it let you connect now?

It is a temporary change that will be lost at next boot, if it solves the problem, it can be made permanent. If not, then please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by AndrewWalker on 2013-10-31
No, that didn't make any difference, I don't get any errors though.
```
fred@Test:~$ sudo modprobe -rv rt61pci
[sudo] password for fred: 
rmmod rt61pci
rmmod eeprom_93cx6
rmmod rt2x00mmio
rmmod rt2x00pci
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211
fred@Test:~$ sudo modprobe -v rt61pci nohwcrypt=Y
insmod /lib/modules/3.11.0-12-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.11.0-12-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-12-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko nohwcrypt=Y
fred@Test:~$ 

```
 I've attached the results of wireless script.

---

### Post by varunendra on 2013-11-04
Sorry for not being able to reply earlier, got extra busy and may remain busy a few more days. It is definitely a bug and seems an old one. Please report it.

If I found something significant, will post back. You may also bump the thread (with a gap of minimum 24 hrs.) to get attention of others who may already have a solution/workaround.

---

