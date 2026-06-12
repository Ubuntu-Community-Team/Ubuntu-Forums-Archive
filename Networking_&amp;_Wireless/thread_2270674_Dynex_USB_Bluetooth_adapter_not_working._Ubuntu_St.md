---
title: "Dynex USB Bluetooth adapter not working. Ubuntu Studio 14.04"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by ninja_in_pajamas on 2015-03-24
Well, the title pretty much says it all.  I did some digging in Terminal to try to get some useful information that might aid in any assistance.

```
Removed@Satellite-C55D-A5108:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
Removed@Satellite-C55D-A5108:~$ lsusb
Bus 002 Device 003: ID 10f1:1a52 Importek 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 19ff:0239 Dynex 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

