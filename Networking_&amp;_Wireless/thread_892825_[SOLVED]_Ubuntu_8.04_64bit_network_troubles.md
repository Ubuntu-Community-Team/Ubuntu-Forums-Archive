---
title: "[SOLVED] Ubuntu 8.04 64bit network troubles"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Samsinsane on 2008-08-17
Hi all,
I am new to running linux, I recently got a new computer started off using Ubuntu 8.04 32bit everything worked fine to start with then I couldn't see any of my windows machines on the network(normally happens in windows so I wasn't that bothered by it). I decided I would upgrade to the 64bit version of 8.04 just to save time if I need 64bit in the future. Ever since upgrading to 64bit I have had problems with my internet connections(maybe even local network connections) on Ubuntu, it will randomly stop working, it takes a minimum of 5secs to start connecting to websites and I can't connect to the Australian repository(I think thats what you call it) all the time. I'm in no rush to have internet speed but if theres a fix for this can you point me in the right direction? I normally just search for answers but I couldn't find anyone with the same problem.

I know you might need computer specs and extra information. The computer specs are below but being new to linux I'm going to need guidance with the extra information lol.

CPU: AMD Athlon 64 X2 Dual Core 6000+
MOBO: Asus m2n-vm-hdmi
RAM: 2G geil(2x 1G)
HDD: 500GB Western Digital(green power version if that matters)

Thats all this computer is atm. Any help with this would be greatly appreciated. I tried installing the LAN drivers provided by ASUS but it failed the first step of the read me file.

Thank you for your time.

---

### Post by Ayuthia on 2008-08-17
> **Samsinsane said:**
> Hi all,
I am new to running linux, I recently got a new computer started off using Ubuntu 8.04 32bit everything worked fine to start with then I couldn't see any of my windows machines on the network(normally happens in windows so I wasn't that bothered by it). I decided I would upgrade to the 64bit version of 8.04 just to save time if I need 64bit in the future. Ever since upgrading to 64bit I have had problems with my internet connections(maybe even local network connections) on Ubuntu, it will randomly stop working, it takes a minimum of 5secs to start connecting to websites and I can't connect to the Australian repository(I think thats what you call it) all the time. I'm in no rush to have internet speed but if theres a fix for this can you point me in the right direction? I normally just search for answers but I couldn't find anyone with the same problem.

I know you might need computer specs and extra information. The computer specs are below but being new to linux I'm going to need guidance with the extra information lol.

CPU: AMD Athlon 64 X2 Dual Core 6000+
MOBO: Asus m2n-vm-hdmi
RAM: 2G geil(2x 1G)
HDD: 500GB Western Digital(green power version if that matters)

Thats all this computer is atm. Any help with this would be greatly appreciated. I tried installing the LAN drivers provided by ASUS but it failed the first step of the read me file.

Thank you for your time.

I don't know if I can help you here or not but it might be helpful for others if they have some information about your network cards.  Can you provide the results of (from the Terminal):
```
lshw -C network
```

---

### Post by Samsinsane on 2008-08-18
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:8c:ac:ec:0a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.9 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```
It's just an onboard network card if that that makes any difference.

---

### Post by foska on 2008-08-19
I am having similar troubles with my setup which has the same onboard ethernet controller.  Did you manage to get this resolved as yet?

> **Samsinsane said:**
> ```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:8c:ac:ec:0a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.9 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```
It's just an onboard network card if that that makes any difference.

---

### Post by Samsinsane on 2008-08-21
Yes actually, turns out my router was the cause of the problem, it was breaking down and deciding certain ports could stop working and then after a couple of hours they will work again. I had a D-Link Dl-524 if you have the same router I suggesting replacing it ASAP.

---

