---
title: "[SOLVED] Reset networking interfaces to default"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by fahadsadah on 2008-06-22
In the past few days I have been messing around with my /etc/network/interfaces, trying to get my VirtualBox to have a bridged connection.
I now have no internet unless I bring down my bridge and my vbox0.

How do I either reset networking to the way it was before, or delete the bridge and vbox0?

Thank you very much in advance!

---

### Post by dmizer on 2008-06-23
without a backup copy, this will be impossible.  but i think we can get you working again anyway.

please post the output of:
```
lshw -C network
```

---

### Post by fahadsadah on 2008-06-24
Of course:
```

fahad@fahad-linux:~$ sudo lshw -C network
[sudo] password for fahad: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:13:8f:e4:60:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: br0
       serial: 00:13:8f:e4:60:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.0.4 link=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: vbox0
       serial: 00:ff:a8:36:42:c4
       size: 10MB/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A link=no multicast=yes port=twisted pair speed=10MB/s

```

I ran it with sudo as it gave a warning the first time saying to run it as root.

I have fixed the networking problem, but I am still wondering if I can delete these spare interfaces. I got the VirtualBox working with NAT.

---

### Post by dmizer on 2008-06-24
> **fahadsadah said:**
> Of course:
I ran it with sudo as it gave a warning the first time saying to run it as root.
for this particular information, the sudo command is not necessary, but it didn't hurt anything either.

> **fahadsadah said:**
> I have fixed the networking problem, but I am still wondering if I can delete these spare interfaces. I got the VirtualBox working with NAT.

the only thing i can think of is to remove them from /etc/network/interfaces:
```
gksudo gedit /etc/network/interfaces
```
remove the extra entries, and carry on.  it might help to know what you did to create them in the first place though.

---

### Post by fahadsadah on 2008-07-12
Sorry I forgot this thread.

Anyway, I finally solved it: I had created the interfaces with VboxAddIF, which makes them persist.
VboxDeleteIF fixed the problem

---

