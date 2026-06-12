---
title: "Ubuntu 14.04 fresh install - No Wireless access"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by tmoflash2 on 2016-01-29
I have just installed Ubuntu 14.04 but I do not have any access to the internet, specifically WiFi. I have Netgear WNDA3100 v2. I am pretty new to Linux as a whole so I am sure it is something simple.

---

### Post by chili555 on 2016-01-29
Please open a terminal and run these commands. Post the result here.```
sudo modprobe ndiswrapper
dmesg | grep ndis
ndiswrapper -l
lsusb
```In the second command, that funny pipe symbol | is on the right side of my US keyboard on the same key with \. In the third command, the last letter is a lower-case L, not a one.

---

### Post by tmoflash2 on 2016-01-29
ndiswrapper is currently not installed

I tried "sudo apt-get install ndisgtk" but it told me Unable to locate package ndisgtk

---

### Post by chili555 on 2016-01-29
> **tmoflash2 said:**
> I tried "sudo apt-get install ndisgtk" but it told me Unable to locate package ndisgtkDo you have a temporary working internet connection? Please try again:```
sudo apt-get update
sudo apt-get install ndisgtk
```

---

### Post by tmoflash2 on 2016-01-29
No I do not. I have an Ethernet cable connected as well but it is not working either. No connection to internet whatsoever.

---

### Post by chili555 on 2016-01-29
> **tmoflash2 said:**
> No I do not. I have an Ethernet cable connected as well but it is not working either. No connection to internet whatsoever.Before I drag out the sledgehammer and the plasma cutter, let's have a look at the ethernet:```
lspci -nnk | grep 0200 -A2
```Do you still have the 14.04 install DVD or USB?

---

### Post by tmoflash2 on 2016-01-30
I ran command and nothing happened, yes I have a USB with 14.04 on it.

---

### Post by chili555 on 2016-01-30
Please try:```
sudo lshw -C network
```

---

### Post by tmoflash2 on 2016-01-30
OK I got ethernet working. It was disabled in the bios

---

### Post by chili555 on 2016-01-30
> **tmoflash2 said:**
> OK I got ethernet working. It was disabled in the biosExcellent! Now, please go back to post #5 and proceed.

---

### Post by tmoflash2 on 2016-01-30
I followed this thread [http://ubuntuforums.org/showthread.php?t=1964173&page=2](http://ubuntuforums.org/showthread.php?t=1964173&page=2)

It tells me that the driver is installed

bcmn43xx64 : driver installed

however, when I run

```
iwconfig
```

I get:

eth0      no wireless extensions.


lo        no wireless extensions.

```
lsusb
```

Bus 006 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0781:5590 SanDisk Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bda:0301 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 006: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 005 Device 005: ID 046d:0a1f Logitech, Inc. G930
Bus 005 Device 004: ID 1532:001f Razer USA, Ltd 
Bus 005 Device 003: ID 19ff:0239 Dynex 
Bus 005 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2016-01-30
Any clues in the log?```
sudo modprobe ndiswrapper && dmesg | grep ndis
```

---

