---
title: "T41 internal wifi card driver"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by daggerx on 2008-07-21
Is there a wifi driver out there for the IBM T41.
Just Got the laptop recently and wondering if a driver exist and if it is compiled for the internal card. Currently im using a wifi usb that is using a prism54 driver I believe. The connection is in and out and it does not stay consistent. Please advise and suggests some tutorials if you have any. Thanks in advance.

---

### Post by chili555 on 2008-07-21
The T41 came with three different wireless cards. Which one does yours have? Open a terminal and do:```
sudo lshw -C network
```We will then know if you have the Intel 2100, the Atheros or the Cisco Aironet.

---

### Post by daggerx on 2008-07-21
that command gave:

```
*-network               
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:81:43:d8
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=N/A ip=192.168.1.138 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s

```

Please advise and thanks in advance.

---

### Post by chili555 on 2008-07-22
It looks, at this point, like you have no wireless card built in. Is it perhaps not enabled in the BIOS?

---

### Post by daggerx on 2008-07-22
> **chili555 said:**
> It looks, at this point, like you have no wireless card built in. Is it perhaps not enabled in the BIOS?

It is enabled in the bios.

---

### Post by chili555 on 2008-07-23
I'm not quite sure how to activate a wireless card that is not even seen in any way by the computer. You might do:```
dmesg | grep -i wireless
sudo cat /var/log/messages | grep -i wireless
```Let's see if there are any interesting messages. Please be sure your USB wireless device is detached first, although, if it was attached on boot, some messages may be given related to it.

---

### Post by daggerx on 2008-07-23
Ill give that a shot tonight when I get back home.

---

