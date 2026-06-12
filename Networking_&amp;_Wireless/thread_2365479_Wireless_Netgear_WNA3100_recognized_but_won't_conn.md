---
title: "Wireless Netgear WNA3100 recognized but won't connect"
date: 2017-07-07
forum: Networking &amp; Wireless
---

### Post by fanialivio on 2017-07-07
Hi there,

I followed [this tutorial]("https://ubuntuforums.org/showthread.php?t=2221251") to install my Netgear WNA3100 Usb adapter. The device is recognised and I'm able to see wireless connection, but when trying to connect, the wifi loads for a while and asks for the password again, infinitely.

I checked and double checked the password. I think it's a driver-related issue. 

If you have any clue, I'd appreciate it. 

Thanks

**lsusb**

liviux@liviux-worstation:~$ lsusb
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 003 Device 004: ID 056a:00fa Wacom Co., Ltd 
Bus 003 Device 002: ID 056a:00f9 Wacom Co., Ltd 
Bus 003 Device 011: ID 12d1:108a Huawei Technologies Co., Ltd. 
Bus 003 Device 008: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**ndiswrapper -l**

liviux@liviux-worstation:~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9020) present

**iwconfig **

liviux@liviux-worstation:~$ iwconfig
enp0s20u11  no wireless extensions.

enxa42b8cf69054  IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enp3s0    no wireless extensions.

lo        no wireless extensions.

**lshw -C network**

liviux@liviux-worstation:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 11
       serial: f0:79:59:6b:05:79
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: enp0s20u11
       serial: 32:e3:2a:a6:e6:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.61 link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: enxa42b8cf69054
       serial: a4:2b:8c:f6:90:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx64 driverversion=1.60+,08/26/2009, 5.10.79.30 link=no multicast=yes wireless=IEEE 802.11g
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by jeremy31 on 2017-07-07
You may want to read [https://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](https://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)
It is a terrible device in Linux.  Now chili555 tells posters I sent it to him just to torture him :)
If you can find a TP-Link WN722N 150Mbps version 1 it will work right away in Ubuntu, some of the newer versions may need source code from [https://github.com/lwfinger/rtl8188eu.git](https://github.com/lwfinger/rtl8188eu.git)

---

### Post by johndough2 on 2017-07-08
Hi

Really need the script pastebinned in please.

But...
#################
*-network:1
description: Wireless interface
physical id: 2
logical name: enxa42b8cf69054
serial: a4:2b:8c:f6:90:54
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmn43xx64 driverversion=1.60+,08/26/2009, 5.10.79.30 link=no multicast=yes wireless=IEEE 802.11g
WARNING: output may be **_*incomplete or inaccurate*_**, you should run this program as super-user. 
#######################

I query the "ndisrapper +bcmn43" as this suggests a Broadcom rather than Netgear.
And is the .11g too specific for the network type?

When you pastebin the wifi script in we may be able to pinpoint the problem.

---

### Post by chili555 on 2017-07-08
> I query the "ndisrapper +bcmn43" as this suggests a Broadcom rather than Netgear.The chipset deep within the Netgear device is a Broadcom. As far as I am aware, Netgear manufactures no silicon of its own.

I suggest that you instead Google the usb.id:```
ID [COLOR="#FF0000"]0846:9020 [/COLOR]NetGear, Inc. WNA3100(v1) Wireless-N 300 [***Broadcom BCM43231***]
```

[https://wikidevi.com/wiki/Netgear_WNA3100](https://wikidevi.com/wiki/Netgear_WNA3100)

---

### Post by fanialivio on 2017-07-09
Thank you very much for your replies. I ended up buying a [COLOR=#000000]TP-Link WN722N. Since the device was recognised I [/COLOR]tought I was closer to the solution than reality, but after reading all those threads I preferred to spend 15€ rather than spend a couple of days trying to find a solution. 

Cheers,

---

