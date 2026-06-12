---
title: "Cisco Aironet 340 not recognised by Edgy"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by joshdavies on 2007-05-03
Kernel: 2.6.17-11-386 (has support for the aironet340)

When I insert the adaptor, the lights blink, and then nothing.

lspcmcia says the slot is empty.
dmesg | tail says "cs: pcmcia_socket0: time out after reset."


anyone have any ideas? It is strange that it doesnt "just work" seeing as the kernel is supposed to support it. :-\

---

### Post by chili555 on 2007-05-03
I understand this is supposed to work with the module *airo_cs.*. Please try:```
sudo modprobe airo_cs
```See if your card springs to life.

---

### Post by joshdavies on 2007-05-04
> **chili555 said:**
> I understand this is supposed to work with the module *airo_cs.*. Please try:```
sudo modprobe airo_cs
```See if your card springs to life.

nope. still the same.

---

### Post by joshdavies on 2007-05-05
Upgrading to feisty didnt help.

This is annoying and strange...

EDIT: this [http://forums.fedoraforum.org/showthread.php?p=784487#post784487](http://forums.fedoraforum.org/showthread.php?p=784487#post784487) looked relavent, but I couldn't get it to do anything when adding it to modprobe. where exactly would I be adding that line?

---

### Post by chili555 on 2007-05-05
May we please see:```
sudo lshw -C network
ifconfig -a
lsmod | grep airo
```Thanks.

---

### Post by joshdavies on 2007-05-05
```
joshd@joshd-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 51
       serial: 00:40:d0:21:ad:aa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=half latency=128 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: ioport:e800-e8ff iomemory:f0000000-f00000ff irq:10
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@06:00.0
       logical name: ra0
       version: 01
       serial: 00:13:d3:82:68:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 ip=192.168.0.100 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:2c000000-2c001fff irq:11
```
```
joshd@joshd-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:D0:21:AD:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KiB)  TX bytes:5276 (5.1 KiB)

ra0       Link encap:Ethernet  HWaddr 00:13:D3:82:68:A8  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe82:68a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7175 errors:1 dropped:1 overruns:0 carrier:0
          collisions:53 txqueuelen:1000 
          RX bytes:938956 (916.9 KiB)  TX bytes:496013 (484.3 KiB)
          Interrupt:11 Base address:0xc000
```
```
joshd@joshd-laptop:~$ lsmod | grep airo
```

---

