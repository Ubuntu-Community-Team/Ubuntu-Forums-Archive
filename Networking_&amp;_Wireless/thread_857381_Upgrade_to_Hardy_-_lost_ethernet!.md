---
title: "Upgrade to Hardy - lost ethernet!"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by PhileinSophia on 2008-07-12
I was happily running Gutsy for quite some time. I waited awhile before upgrading to Hardy, until I was good and bored with Gutsy.

I was expecting to lose wireless - I've got a Broadcom wireless card. I also expected Hardy to have the fast-and-easy way of getting it up and running that Gutsy did... but...

After the upgrade, I lost networking completely - I was unable to connect with ethernet which was strange because I've -never- had a problem with that before.

I grumbled, grabbed my Gutsy CD, reinstalled it, still no ethernet. I reformatted the partition that I've had Ubuntu on, reinstall Gutsy - no ethernet. I tried once more for luck and still no-go.

I managed to get the wireless working with Gutsy, with fwcutter and the rest but my wireless is painfully slow and unreliable (which it was only very occasionally in the past)...

Any guesses what could have caused the loss of eth0? How to get it back? I don't think it's the hardware since it was working right up until I upgraded, eth0 is being recognised as a Broadcom card, but it just won't enable.

Any guesses?

---

### Post by prshah on 2008-07-12
> **PhileinSophia said:**
> 
after the upgrade, I lost networking completely - I was unable to connect with ethernet which was strange because I've -never- had a problem with that before.


Lets get some more information ```

lspci | grep -i net
sudo lshw -C network
cat /etc/network/interfaces
dmesg | grep -i eth

```

or you can try a quick step```
sudo /etc/init.d/networking restart
``` and if it doesn't work, post back error messages.

---

### Post by PhileinSophia on 2008-07-12
That actually did the trick

And now I'm going to sit back, scratch my head, and try to figure out how that works... 

Thanks!:KS

---

### Post by prshah on 2008-07-13
> **PhileinSophia said:**
> That actually did the trick


Check if your /etc/network/interfaces file includes lines similar to the following, for the interface in question (should be eth0)```

iface eth0 inet dhcp
auto eth0
```

---

### Post by PhileinSophia on 2008-07-13
```
auto lo
iface lo inet loopback
```

That's all it's saying. But I'm able to connect with eth0 and wireless is working fine. 

This was the information you were looking for before - 

```

denise@amoeba:~$ lspci | grep -i net
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
```

```

denise@amoeba:~$ sudo lshw -C network
[sudo] password for denise:
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:f9:72:17
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:40:5f:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.11.3 latency=32 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
```

I'm back to running Gutsy, I don't know if I'd have the same trouble again if I reattempted an upgrade.

---

