---
title: "No wireless after upgrade to Xubuntu 15.04"
date: 2015-07-07
forum: Networking &amp; Wireless
---

### Post by jeftobias on 2015-07-07
Upgraded from 14.10 to 15.04 and discovered I had no wireless. Ran the suggested script and here are the relevant portions:

```
##### lspci #############################

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]

```

```
##### lsusb #############################

Bus 002 Device 002: ID 154b:00b2 PNY 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c06c Logitech, Inc. Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.8.104  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:feaf:58b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10829817 (10.8 MB)  TX bytes:664661 (664.6 KB)
          Interrupt:18 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

```

Help?

---

### Post by chili555 on 2015-07-07
May we see the entire results of the script, please? There are parts that we think are relevant that you've omitted.

---

### Post by jeftobias on 2015-07-07
> **chili555 said:**
> May we see the entire results of the script, please? There are parts that we think are relevant that you've omitted.

I'm sorry, I tried to mark the thread "solved" as I discovered I needed to purge the 
bcmwl-kernel-source and then install the correct b43 firmware. It's working now.

---

