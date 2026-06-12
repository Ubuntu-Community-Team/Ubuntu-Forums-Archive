---
title: "Network adapter (nvidia mcp61- forcedeth) not working"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by giancarlo76 on 2008-10-30
This is an excerpt of lspci -v:
```
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	Memory at dfefd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d480 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
```

NetworkManager says it's connected, but dhclient actually fails getting IP address. This is the output:
```
# sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:1f:c6:a7:e0:0a
Sending on   LPF/eth0/00:1f:c6:a7:e0:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
```

Any hint to solve this issue?
Thanks a lot.

---

### Post by giancarlo76 on 2008-10-31
Other pepole have the same problem, with other cards. Here's a link in italian: [http://forum.ubuntu-it.org/index.php?topic=228885.0]("http://forum.ubuntu-it.org/index.php?topic=228885.0")

Any hint?

---

### Post by mantelo on 2008-11-10
It seems that there is a problem with the new network manager.

To uninstall it, open a terminal and type:

sudo update-rc.d -f NetworkManager remove

Then edit your interfeces file:

sudo gedit /etc/network/interfaces

and add

auto eth0
iface eth0 inet dhcp

save and reboot

(taken from the italian forum mentioned above).

---

### Post by giancarlo76 on 2008-11-11
Thanks for your reply, it actually solved the issue.

---

### Post by billh1241 on 2008-11-11
Thank you so much.  It worked!!

---

