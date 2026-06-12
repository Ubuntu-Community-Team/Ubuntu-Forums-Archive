---
title: "Fritz W-Lan for Ubuntu"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by Julien1993 on 2008-10-02
**Hello.**
I have a problem with my Fritz W-lan USB Stick.
I need help i cant connect to the Internet.

It works with Windows,
what do I have to do,
to connect to Fritz W-lan

Informations:
[U]
[*]Ubuntu Hardy Herron 8.04
[*]HP pavilion zd7015ea (Laptop)
[*]1250 MB Ram
[*]120 GB Harddiskdrive[/U]

---

### Post by superprash2003 on 2008-10-02
in your terminal type lshw -C network and post output.. also post output of iwconfig

---

### Post by Julien1993 on 2008-10-02
rowidu@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:2d:26:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.117 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
rowidu@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

