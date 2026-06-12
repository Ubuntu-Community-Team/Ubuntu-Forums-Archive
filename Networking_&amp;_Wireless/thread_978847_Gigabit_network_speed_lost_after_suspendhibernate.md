---
title: "Gigabit network speed lost after suspend/hibernate"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by mkoonstra on 2008-11-11
Like the title says, my network card goes into 100mbit mode after suspend or hibernate. Only way to solve this is to reboot. Can this be fixed?

I am using ubuntu 8.10, my network adapter is a realtek rtl8169

---

### Post by GavinSpearhead on 2009-03-17
Dunno if this is still applicable to you. I seem to have the same problem.

sudo ethtool eth0 outputs, indicating it won't autonegotiate 1000baseT even though it is capable of it.

```

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

lshw outputs
```

lshw -C net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:d0:50:6d:c5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.71 latency=0 module=r8169 multicast=yes

```


I can force it to use gigabit ethernet by running
sudo ethtool -s eth0 advertise 0x020 
sometimes I need to add speed 1000 too

Adding either (or both) these to  /etc/network/interfaces doesn't seem to help.
pre-up echo /usr/sbin/ethtool -s $IFACE advertise 0x020
up echo /usr/sbin/ethtool -s $IFACE advertise 0x020

Anyone any particular ideas on how to  make the network card permanently advertise 1000/full?

---

### Post by GavinSpearhead on 2009-05-03
No one any ideas?

The problem persists in 9.04

---

### Post by korcsi on 2009-05-05
I have same problem.

I try edit in /etc/network/if-pre-up.d directory the pre-up files and /etc/network/if-up.d directory the up files but not help.
In /etc/acpi/resume.d/62-ifup.sh edit with /usr/sbin/ethtool -s eth0 advertise 0x020 command not help.

Sorry my wrong english!

---

### Post by GavinSpearhead on 2009-06-10
I editted the file /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
 and added the line:

/usr/sbin/ethtool -s eth0 speed 1000 advertise 0x020

which seems to resolve the problem Q&D. Not very satisfying really, but it works, at least for suspend. I haven't tried hibernate tho.

---

### Post by GriFF3n on 2009-12-05
Having the same problem as you GavinSpearhead. Your fix doesn't seem to work out for me though. Any other ideas? Using Server 9.10

GriFF

---

### Post by GriFF3n on 2009-12-05
Running "sudo ethtool -s eth0 speed 1000" Fixes the problem, but needs to be performed after every wake from suspend. Any ideas?

---

### Post by GriFF3n on 2009-12-06
BUMP for some help. I'm thinking I can add a script to be run on wake, but I'm not sure how to do it. Anyone?

---

### Post by GriFF3n on 2009-12-15
bump!

---

### Post by jcollie on 2010-02-03
I also have the same issue.  Create a file with the aforementioned command and place it in /etc/pm/sleep.d/

Shouldn't be necessary, but it does set the card to the proper values.

---

