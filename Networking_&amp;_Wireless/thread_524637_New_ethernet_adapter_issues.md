---
title: "New ethernet adapter issues"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by neptunix on 2007-08-13
I've inserted a new ethernet adapter to a running Ubuntu Feisty Server. It seems to be recognised during boot process

[ 19.922101] 8139too Fast Ethernet driver 0.9.28
[ 19.922175] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 20
[ 19.922518] eth0: RealTek RTL8139 at 0xe0846000, 00:80:48:17:9a:56, IRQ 20
[ 19.922522] eth0: Identified 8139 chip type 'RTL-8100B/8139D'
[ 19.922555] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 21
[ 19.922891] eth1: RealTek RTL8139 at 0xe0848000, 00:04:61:66:3f:a3, IRQ 21
[ 19.922895] eth1: Identified 8139 chip type 'RTL-8101'

*lcpci*:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Compex FN22-3(A) LinxPRO Ethernet Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at b000 [size=256]
        Memory at f6010000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 30000000 [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: EPoX Computer Co., Ltd. Onboard RTL8101L 10/100 MBit
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at b400 [size=256]
        Memory at f6011000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 30010000 [disabled] [size=64K]
        Capabilities: [50] Power Management version 2
```

Added lines for the new interface to /etc/network/interfaces
```
auto eth1
iface eth1 inet static
        address 172.16.8.28
        netmask 255.255.255.0
        network 172.16.8.0
        broadcast 172.16.8.255
        gateway 172.16.8.1
```

But if I try to up the interface - it fails:

neptune@ugate:~$ sudo ifup eth1
eth1: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.


Tried booting with Ubuntu Server Cdrom, it recognizes both card.
Did I miss something? Thx

---

### Post by neptunix on 2007-08-13
Well, resolved :)

Wrote "eth1 mac 00:80:48:17:9A:56 arp 1" to /etc/iptab and that's it :)

after booting it became eth2...

"ip link" command helps

---

