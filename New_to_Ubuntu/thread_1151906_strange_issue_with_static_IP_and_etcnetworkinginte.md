---
title: "strange issue with static IP and /etc/networking/interfaces"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Hospadar on 2009-05-07
EDIT:
damn I'm dumb, eht0 instead of eth0

I have my wired network connection set up with a static IP in /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eht0
iface eth0 inet static
        address <my addr>
        netmask <my netmask>
        gateway <my gw addr>

```If I do ifup, it works fine
```
$ sudo ifup eth0
 * if-up.d/mountnfs[eth0]: waiting for interface eht0 before doing NFS mounts
```And then the network works perfectly, and everything is set correctly

But if I do (and this is what the startup script does, so the network doesn't start automatically on boot):```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Ignoring unknown interface eht0=eht0.                                                                      
 
```and the network doesn't work

This may also be of interest:```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:22:68:49:5e:ba
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 ip=35.8.48.107 latency=0 module=e1000e multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 82:bf:c8:c9:de:3b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```I've never run into this issue, so I'm at a loss for what to do

---

### Post by buntunub on 2009-05-07
Report this as a bug on launchpad.

---

### Post by raptor2552 on 2009-05-07
remove > auto eht0
 which by the way should be eth0 not eht0

---

