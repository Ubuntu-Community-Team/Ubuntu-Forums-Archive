---
title: "No option to network wirelessly (only wired)"
date: 2014-11-05
forum: Networking &amp; Wireless
---

### Post by Mikael_Gafi on 2014-11-05
im running on 14.04 and I have no option whatsoever to run wireless ( im on a wired connection right now) . I need  assistance, and anything that can be done to network wirelessly. Thanks!

---

### Post by Bucky Ball on 2014-11-05
Please post the output of:

```
sudo lshw -C network
```

---

### Post by Mikael_Gafi on 2014-11-05
> **Bucky Ball said:**
> Please post the output of:

```
sudo lshw -C network
```


negacy@apex:~$ sudo lshw -C network
[sudo] password for negacy: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5c:fb:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f4200000-f4203fff ioport:3000(size=256)

---

### Post by Bucky Ball on 2014-11-05
Was this card working previously? What actually happened? You switched the machine on one day and there was no wireless or is this the first time you've tried to use it?

Check Additional Drivers while online with a cable and see if there is anything there for wireless. Incidentally, is this a USB wireless dongle or internal wireless card? Please give all relevant information.

One thing's for sure and certain: there is no sign whatsoever of any wireless device in your machine which would indicate that, if it's an internal card that was working, it may have died (it happens). If it is a USB dongle, it's not plugged in. If it's a USB device make sure it is plugged in throughout the instructions you're trying unless advised otherwise.

If it is a USB device, plug it in and give the output of this:

```
lsusb
```

PS: Please use [code] tags when posting code. See last link in my signature. ;)

---

### Post by Mikael_Gafi on 2014-11-06
> **Bucky Ball said:**
> Was this card working previously? What actually happened? You switched the machine on one day and there was no wireless or is this the first time you've tried to use it?

Check Additional Drivers while online with a cable and see if there is anything there for wireless. Incidentally, is this a USB wireless dongle or internal wireless card? Please give all relevant information.

One thing's for sure and certain: there is no sign whatsoever of any wireless device in your machine which would indicate that, if it's an internal card that was working, it may have died (it happens). If it is a USB dongle, it's not plugged in. If it's a USB device make sure it is plugged in throughout the instructions you're trying unless advised otherwise.

If it is a USB device, plug it in and give the output of this:

```
lsusb
```

PS: Please use [code] tags when posting code. See last link in my signature. ;)




The laptop was given to me from a friend. the wireless card is not a usb wireless dongle, and it is internal. intel wm3945abg



lsusb

negacy@apex:~$ lsusb
Bus 002 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Hadaka on 2014-11-06
Hi, please verify your wireless is enabled. Click the up/down arrow..
network mgr. (next to envelope) See that Enable Wireless has a check mark.
then open a terminal ctrl/alt/t COPY and paste one line at a tiime into the terminal.
```
uname -a
cat /etc/issue
lspci -nn | egrep '0200|0280'
rfkill list all
```
post the output.
thanks

---

### Post by Mikael_Gafi on 2014-11-10
> **Hadaka said:**
> Hi, please verify your wireless is enabled. Click the up/down arrow..
network mgr. (next to envelope) See that Enable Wireless has a check mark.
then open a terminal ctrl/alt/t COPY and paste one line at a tiime into the terminal.
```
uname -a
cat /etc/issue
lspci -nn | egrep '0200|0280'
rfkill list all
```
post the output.
thanks

negacy@apex:~$ uname -a
Linux apex 3.13.0-38-generic #65-Ubuntu SMP Thu Oct 9 11:39:01 UTC 2014 i686 i686 i686 GNU/Linux
negacy@apex:~$ cat /etc/issue
Ubuntu 14.04 LTS \n \l

negacy@apex:~$ lspci -nn | egrep '0200|0280'
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
negacy@apex:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
negacy@apex:~$

---

