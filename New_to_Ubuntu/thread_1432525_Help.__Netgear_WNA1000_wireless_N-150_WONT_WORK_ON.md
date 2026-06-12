---
title: "Help.  Netgear WNA1000 wireless N-150 WONT WORK ON UBUNTU 9.10"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by odogwu on 2010-03-17
[B]Please Help. i've tried to get the network card to work but it doesn't. Ubuntu  does not recognise it when i check for it in lspci.
[/B]
chibuzor@chibuzor-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
chibuzor@chibuzor-desktop:~$ 
...........

**i also went into compat wireless and changed the driver to netgear WNA 1000 device id**

to/* Netgear WNA1000 */
    { USB_DEVICE(0x0846, 0x9040)

**i dont know what to do anymore please help**

---

### Post by cariboo on 2010-03-18
It looks like your device is a USB adapter, it won't show up in lspci, but it will show up when you run lsusb. 

To see if the device is detected in a terminal type:

```
lshw -C network
```

If the device is detected you should see something like this:

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:f0:a3:ca:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by odogwu on 2010-03-20
Hi sorry this is the output i got after further reading


lsusb

Bus 001 Device 005: ID 0846:9040 NetGear, Inc. 
Bus 001 Device 003: ID 054c:00ee Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chibuzor@chibuzor-desktop:~$ 


chibuzor@chibuzor-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth1
       version: 02
       serial: 00:0d:56:8b:3f:2a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 mingnt=255 multicast=yes
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
chibuzor@chibuzor-


What do I do next???

---

### Post by sc0g on 2010-05-18
(bump)

I have the same wireless card and will be searching for a solution... Let me know if anyone finds any info on this, and I'll be sure to do the same.


Thanks! :)

---

### Post by anewguy on 2010-05-18
I found [This]("http://ubuntuforums.org/showpost.php?p=8828250&postcount=14") which may be of help to you.  I didn't look at the things it has you download, so if you need help with it just post back.

Dave ;)

---

### Post by Schniels on 2010-05-28
Hi Dave!
I could use some help with it: 
 
FixIt PeteC wrote "1. Download and install compat-wireless-2010-02-01" 
 
I couldn't figure out how to install that...
If anyone else could help me, that would be lovely
 
Cheers
Niels

---

