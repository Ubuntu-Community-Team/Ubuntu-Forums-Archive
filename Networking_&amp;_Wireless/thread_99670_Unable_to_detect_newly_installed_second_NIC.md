---
title: "Unable to detect newly installed second NIC"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by ironblade on 2005-12-06
Hi all,

I've got a server set up running the base install of Kubuntu (Breezy).
We've shut it down, put a second network card (NIC) into it, and rebooted.
I'd expect it to be automatically detected, but ifconfig shows only eth0 and lo, no eth1 as expected.
I've put an entry for eth1 into /etc/network/interfaces as follows:

```
auto lo eth0 eth1

(there's also a section for eth0, but as that works, I'll leave it out)

iface eth1 inet static
        address 192.168.100.1
        netmask 255.255.255.0
```

lspci -v gives (for the ethernet controllers):
```
0000:00:08.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 20)
        Flags: bus master, stepping, medium devsel, latency 0, IRQ 10
        I/O ports at a800 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e4000000 [disabled] [size=64K]
        Capabilities: [44] Power Management version 1

0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at ec00 [size=256]
        Memory at e5001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
```

The output of dmesg is a bit odd:
<snip>
```
eth0: Macronix 98715 PMAC rev 32 at 0001a800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 10.
[4294677.429000] 8139too Fast Ethernet driver 0.9.27
[4294677.430000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294677.430000] PCI: setting IRQ 5 as level-triggered
[4294677.430000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294677.430000] eth1: RealTek RTL8139 at 0xec00, 00:d0:70:00:25:8c, IRQ 5
[4294677.430000] eth1:  Identified 8139 chip type 'RTL-8139B'
[4294677.437000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
```
<snip>

Why is it odd, you ask? Well, if you look at the MAC addresses above, then at the one from eth0 in ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:D0:70:00:25:8C
```

Notice that the active interface eth0 has 00:d0... but in dmesg, it's eth1 that has that address?

Anyway, that's the background info.
I just want to know if I can force (k)ubuntu to re-detect NICs after install is already complete?
I've tried messing with modprobe, but the modules are already loaded, it's just that the interface won't come up:
```
root@localhost# ifup eth1
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
```

Any network gurus out there who can help before I have to reinstall the whole thing?

---

### Post by Mathboy on 2005-12-06
In my dmesg I have eth0 (RTL8169) and eth1 (RTL-8139C), but when it comes time to use them they're eth0 (RTL-8139C) and eth2 (RTL8169).

dmesg gives no hint it's actually eth2, but /proc/net/dev lists them as eth0 and eth2. :???: 

I really have no idea what's going on, I've been trying to resolve gigabit-ethernet performance issues in Ubuntu rather than work out why the ethernet devices get swapped around.

Anyway, maybe you too have an eth2? ;)

---

### Post by ironblade on 2005-12-06
[QUOTE=Mathboy]Anyway, maybe you too have an eth2? ;)[/QUOTE]

You, sir, are a gentleman and a scholar!
I do indeed have it in /proc/net/dev as eth2, not eth1!!!!
A quick edit of /etc/network/interfaces, and voila!

Thanks!!!! :-D

---

### Post by Mathboy on 2005-12-07
Glad that helped :razz: 

I now know how to move it to eth1 also... Ubuntu puts fixed mappings from the ethernet mac address to a specific eth# number in the /etc/iftab file.
If you delete the eth1 line from /etc/iftab your second nic should end up at eth1 on next boot. :smile:

---

