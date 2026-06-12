---
title: "LAN not working"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Bishek on 2011-01-07
Hi, i'm a new user of Ubuntu. I have intel D865GLC motherboard and two hdd. one with XP and other with Ubuntu. I can connect to internet if i boot from XP but not able to connect to internet with Ubuntu. Network manager simply displays "No Connection". Cant we change the connection speed from 100MBPS to 10MBPS or Automatic like in XP??
I'm using Ubuntu 10.04 LTS (Lucid Lynx).

---

### Post by cariboo on 2011-01-08
Could run the following command and post the output in your next post:

```
sudo lshw -C network > network.txt
```

The above command creates a text file called network.txt, with your networking details, that you can copy to your windows partition.

---

### Post by Bishek on 2011-01-08
> **cariboo907 said:**
> Could run the following command and post the output in your next post:

```
sudo lshw -C network > network.txt
```

The above command creates a text file called network.txt, with your networking details, that you can copy to your windows partition.
Thanks cariboo, the command worked, here is the complete copy of the result. I'm dying to use internet from Ubuntu.

*-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth0
       version: 10
       serial: 00:19:d1:36:4c:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:b800(size=256) memory:ff8ffc00-ff8ffcff

---

### Post by Bishek on 2011-01-12
i tried Linux mint 9 too but the same problem. In Ubuntu 10.04 and Linux mint 9 i installed the OS, updated it online. No problem with the network connection until this point. The problem emerged after i restart my computer after i update it.
the command:
sudo lshw -C network
shows the same except for "duplex=full" before restart and "duplex=half" after restart.
i searched to solve this problem but it requires eth-tool or mii-tool to do the trick but i have non. how can i fix this problem.

---

### Post by Bishek on 2011-01-12
i even managed to install eth-tool offline, it worked, the link is now full duplex but my problem persists...i cant connect to the internet via LAN. what i noticed now is, when i put my Ethernet device in DHCP mode and do "ifconfig" it shows three devices- eth0 with no IP address, eth0:avahi.... with ip of range 169.xxx.xxx.xxx and loopback adapter of ip range 127.0.0.1.
I have worked on XP and know that IP range of 169.xxx.xxx.xxx and 127.xxx.xxx.xxx cannot connect to the internet.
What do I do???

---

