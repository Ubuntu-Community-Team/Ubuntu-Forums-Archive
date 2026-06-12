---
title: "problem with wireless"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Zlatan on 2008-03-24
hello, after playing with wicd online installer, my ubuntu gutsy does not recognize wireless network card at all- even after reinstalling bcm43xx driver through restricted driver manager. how could i put drivers back?

thank you

---

### Post by imdano on 2008-03-24
Wicd doesn't touch your drivers, so they should still be there.  Whats the output of ```
iwconfig
iwlist scan
sudo lshw -C network
```

---

### Post by Zlatan on 2008-03-24
> **imdano said:**
> Wicd doesn't touch your drivers, so they should still be there.  Whats the output of ```
iwconfig
iwlist scan
sudo lshw -C network
```

===
thanks for the reply. here are the outputs:
===
laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
===
laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
===
laptop:~$ sudo lshw -C network
[sudo] password for .....:
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:cc:01:b4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.1.7 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
===
so lshw shows my eth1 card.

what could i do here?

---

### Post by imdano on 2008-03-24
It's there, but no driver is associated with it, which probably happened when you reinstalled  the bcm43xx driver.  You might have to run something like ```
sudo modprobe bcm43xx
``` to load the driver again.

Out of curiosity, did you edit the /etc/network/interfaces file when you installed wicd?  Sometimes messing around with that will make interfaces not appear when you start up the computer (though they're still there, you just have to manually bring them up before they appear).

---

### Post by Zlatan on 2008-03-24
> **imdano said:**
> It's there, but no driver is associated with it, which probably happened when you reinstalled  the bcm43xx driver.  You might have to run something like ```
sudo modprobe bcm43xx
``` to load the driver again.

Out of curiosity, did you edit the /etc/network/interfaces file when you installed wicd?  Sometimes messing around with that will make interfaces not appear when you start up the computer (though they're still there, you just have to manually bring them up before they appear).

it works!:) but this drops after restart- no wireless option in networking again. how could i solve this to have association after restart automatically?
/etc/network/interfaces was not edited, unless wicd.py script did that.

---

### Post by Zlatan on 2008-03-24
ok, i've just added following:
==
sudo gedit /etc/modules
bcm43xx
==
am i right with this?
i can see that it works, wireless option loads with startup, but is this way right one?

---

