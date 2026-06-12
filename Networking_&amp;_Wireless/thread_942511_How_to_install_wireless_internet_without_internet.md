---
title: "How to install wireless internet without internet"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by F8M on 2008-10-09
Under the lshw -C network command, this is what my laptop has.
*-network
  description: Network controller
  product: BCM4311 802.11b/g WLAN
  vendor: Broadcom Corporation
  physical id: 0
  bus info: pci@0000:03:00.0
  version: 01
  width: 32 bits
  clock: 33MHz
  capabilities: bus master cap list
  configuration: driver=b43-pci-bridge latency=0 module=ssb
*-network
  description: Wireless interface
  physical id:1
  logical name: wlan0
  serial: 00:1a:73:1d:bf:0a
  capabilities: ethernet physical wireless
  configuration: broadcast=yes multicast=yes wirless=IEEE 802.11g
ANY HELP WOULD BE APPRECIATED - THANK YOU

---

### Post by Ayuthia on 2008-10-09
You can try this link:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Just go to Option 2 and it will have instructions on where to get the files and install it in Ubuntu.

Hope that helps.

---

### Post by F8M on 2008-10-11
This seems like the way to go. But this solution won't work because I have no LAN internet, just wireless. How would I go about doing this without internet.

---

### Post by Ayuthia on 2008-10-11
Option 2 tells you where you have to download the files.  You will have to do this from another computer or one that has an internet connection.

If you need to have it without the internet connection, you will have to wait until 8.10 is released.  It comes with the wl driver installed so all you have to do is enable it in System->Administration->Hardware Drivers.

---

