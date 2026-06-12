---
title: "Kubuntu Networking Issues"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by Chipsterian on 2007-05-31
I originally posted this in the Absolute Beginners area, where apparently I stumped them (or they don't want to deal with me...).

My problem.
Kubuntu 6.06 LTS installed on an older Acer Veriton 5100.
No wireless card, but an on-board Intel Pro/100 VE NIC.

lspci -v result:
[INDENT]01;08:0 Ethernet controller: Intell Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
Subsystem: Intel Corporation EtherExpress PRO/100 VE
Flags: bus master, medium devsel, latency 32, IRQ 9
Memory at 80101000 (32-bit, non-prefetchable) [size=4K]
I/O ports at 74 [size=64]
Capabilities: ,access denied>[/INDENT]

and then asked for the results of sudo ifconfig
results post:
[INDENT]eth0
Link encap:Ethernet HWaddr 00:00:E2:33:9A:AB
inet6 addr: fe08:200:e2ff:fe33:9aab/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueue:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

lo
Link encap:Local Loopback
inet addr: 127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:160 errors:0 dropped:0 overruns:0 frame:0
TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueue:1000
RX bytes:12080 (11.7 Kib) TX bytes:12080 (11.7 KiB)[/INDENT]

which I'm told is a functioning NIC, and was asked for the contents of /etc/network/interfaces: 
posted here:
[INDENT]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/INDENT]

The network is using a Windows 2003 Server for DHCP, and it should work since there are two other towers on my network (unbuntu 6.06 LTS) that are happily connecting to the internet.

What am I missing?

---

### Post by Chipsterian on 2007-06-04
Adding some further info that I discovered tinkering around...

The Comp in question has been hooked directly to the DSL modem, which is set to be a DHCP server.

The modem, when checked on a by a another computer will show the xubuntu's correct MAC, but the boxen will not pick up an IP, nor when set to static, not ping or be pingable.

I will clarify as needed.

---

### Post by Chipsterian on 2007-06-04
To everyone who tried to come to my rescue, thank you.

I'm installing Win 2k on the machines, and living with those issues. At least I know them best.

---

