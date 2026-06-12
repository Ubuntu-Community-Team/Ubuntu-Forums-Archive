---
title: "Wireless network adapter."
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Pondoro on 2009-04-10
I bought a USB wireless adapter. The CD with drivers (intended for Windows) will not autorun. How do I make Ubuntu see the device and download drivers?

Thanks

---

### Post by FrankT-Qc on 2009-04-10
The first thing you want to do is check if you could use it without downloading anything... plug it in, wait for a few seconds and then try this command :

```
ip link show
```

If you see a new network interface in there, you probably don't need any extra driver...

---

### Post by superprash2003 on 2009-04-10
in your terminal type **lshw -C network** and post output.. we first need to know what hardware it is..

---

### Post by Pondoro on 2009-04-10
> **FrankT-Qc said:**
> The first thing you want to do is check if you could use it without downloading anything... plug it in, wait for a few seconds and then try this command :

```
ip link show
```

If you see a new network interface in there, you probably don't need any extra driver...

Here it is...
mike@mike-desktop:~$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:40:ca:5a:70:a0 brd ff:ff:ff:ff:ff:ff
3: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 3a:d2:99:c7:c2:ac brd ff:ff:ff:ff:ff:ff

---

### Post by Pondoro on 2009-04-10
> **superprash2003 said:**
> in your terminal type **lshw -C network** and post output.. we first need to know what hardware it is..

 Here is what it said:
mike@mike-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:5a:70:a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.100 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:d2:99:c7:c2:ac
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
mike@mike-desktop:~$

---

### Post by halitech on 2009-04-10
those results don't look promising. whats the result of
```
lsusb
```
with the adapter plugged in and without

---

### Post by Pondoro on 2009-04-10
> **halitech said:**
> those results don't look promising. whats the result of
```
lsusb
```
with the adapter plugged in and without

With:
mike@mike-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3a0f D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Without:
mike@mike-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mike@mike-desktop:~$ 

Notice the "D-Link System in the 1st response? It is a D-Link adapter

---

### Post by halitech on 2009-04-10
good thing is the device is being seen. bad news is no info on setting up that particular device. You can try this:

[http://ubuntuforums.org/showthread.php?t=885847&highlight=07d1%3A3a0f](http://ubuntuforums.org/showthread.php?t=885847&highlight=07d1%3A3a0f)

hopefully that will work for you

---

