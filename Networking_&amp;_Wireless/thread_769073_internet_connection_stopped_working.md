---
title: "internet connection stopped working"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by lomnick on 2008-04-26
Hi,

I just got back from a short holiday to find that Gutsy Gibbon no longer connects to the net. This is via a router - a Windows XP PC is connected to the same router and it connects fine. (I'm using it to post this!) Networking has always been a blind spot of mine, so apologies if this is something incredibly obvious.

So far, I have rebooted, swapped round network cables, tried taking the router out of the equation by directly plugging the PC into the  cable modem etc. I tried [FONT="Courier New"]sudo dhclient[/FONT], but just got [FONT="Courier New"]NO DHCPOFFERS RECEIVED[/FONT].

Here's my [FONT="Courier New"]/var/log/syslog[/FONT]
```
Apr 27 01:43:23 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 27 01:43:23 Optiplex-GX110 NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr 27 01:43:26 Optiplex-GX110 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr 27 01:43:26 Optiplex-GX110 kernel: [   92.639375] NET: Registered protocol family 17
Apr 27 01:43:26 Optiplex-GX110 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Apr 27 01:43:33 Optiplex-GX110 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Apr 27 01:43:45 Optiplex-GX110 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 27 01:43:48 Optiplex-GX110 hcid[5570]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Apr 27 01:43:48 Optiplex-GX110 hcid[5570]: Default authorization agent (:1.19, /org/bluez/auth) registered
Apr 27 01:43:53 Optiplex-GX110 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 27 01:44:01 Optiplex-GX110 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 27 01:44:03 Optiplex-GX110 NetworkManager: <info>  Updating allowed wireless network lists. 
Apr 27 01:44:03 Optiplex-GX110 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Apr 27 01:44:15 Optiplex-GX110 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr 27 01:44:16 Optiplex-GX110 dhclient: No DHCPOFFERS received.
Apr 27 01:44:16 Optiplex-GX110 dhclient: Trying recorded lease 192.168.123.2
Apr 27 01:44:16 Optiplex-GX110 avahi-daemon[4705]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.123.2.
Apr 27 01:44:16 Optiplex-GX110 avahi-daemon[4705]: New relevant interface eth0.IPv4 for mDNS.
Apr 27 01:44:16 Optiplex-GX110 avahi-daemon[4705]: Registering new address record for 192.168.123.2 on eth0.IPv4.
Apr 27 01:44:19 Optiplex-GX110 avahi-daemon[4705]: Withdrawing address record for 192.168.123.2 on eth0.
Apr 27 01:44:19 Optiplex-GX110 avahi-daemon[4705]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.123.2.
Apr 27 01:44:19 Optiplex-GX110 avahi-daemon[4705]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 27 01:44:19 Optiplex-GX110 avahi-autoipd(eth0)[5974]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Apr 27 01:44:19 Optiplex-GX110 avahi-autoipd(eth0)[5974]: Successfully called chroot().
Apr 27 01:44:19 Optiplex-GX110 avahi-autoipd(eth0)[5974]: Successfully dropped root privileges.
Apr 27 01:44:19 Optiplex-GX110 avahi-autoipd(eth0)[5974]: fopen() failed: Permission denied
Apr 27 01:44:19 Optiplex-GX110 avahi-autoipd(eth0)[5974]: Starting with address 169.254.7.118
Apr 27 01:44:24 Optiplex-GX110 avahi-autoipd(eth0)[5974]: Callout BIND, address 169.254.7.118 on interface eth0
Apr 27 01:44:27 Optiplex-GX110 avahi-daemon[4705]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.7.118.
Apr 27 01:44:27 Optiplex-GX110 avahi-daemon[4705]: New relevant interface eth0.IPv4 for mDNS.
Apr 27 01:44:27 Optiplex-GX110 avahi-daemon[4705]: Registering new address record for 169.254.7.118 on eth0.IPv4.
Apr 27 01:44:28 Optiplex-GX110 avahi-autoipd(eth0)[5974]: Successfully claimed IP address 169.254.7.118
Apr 27 01:44:28 Optiplex-GX110 avahi-autoipd(eth0)[5974]: fopen() failed: Permission denied
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth0 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  avahi-autoipd running on eth0, assuming IPv4LL address 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  not touching eth0 configuration, was configured externally 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth0 
Apr 27 01:44:29 Optiplex-GX110 dhcdbd: Unrequested down ?:3
Apr 27 01:44:29 Optiplex-GX110 NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Apr 27 01:45:14 Optiplex-GX110 ntpdate[6053]: can't find host ntp.ubuntu.com 
Apr 27 01:45:14 Optiplex-GX110 ntpdate[6053]: no servers can be used, exiting
```

And the result of [FONT="Courier New"]ifconfig[/FONT]:```

eth0      Link encap:Ethernet  HWaddr 00:B0:D0:69:76:6A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:31455 (30.7 KB)
          Interrupt:5 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:B0:D0:69:76:6A  
          inet addr:169.254.7.118  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18224 (17.7 KB)  TX bytes:18224 (17.7 KB)
```

And finally the result of [FONT="Courier New"]lspci -v[/FONT]```

00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
	Subsystem: Dell OptiPlex GX110
	Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03) (prog-if 00 [VGA])
	Subsystem: Dell OptiPlex GX110
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Memory at ff000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fd000000-feffffff
	Prefetchable memory behind bridge: f9000000-f9ffffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Intel Corporation 82801AA IDE Controller
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation 82801AA USB Controller
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at ff80 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
	Subsystem: Intel Corporation 82801AA SMBus Controller
	Flags: medium devsel, IRQ 10
	I/O ports at dcd0 [size=16]

00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
	Subsystem: Dell OptiPlex GX110
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at d800 [size=256]
	I/O ports at dc80 [size=64]

01:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
	Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at ecf0 [size=16]
	I/O ports at ecd0 [size=16]
	I/O ports at ecb0 [size=16]
	I/O ports at ec90 [size=16]
	I/O ports at ec60 [size=32]
	I/O ports at e800 [size=256]
	Expansion ROM at f9020000 [disabled] [size=64K]
	Capabilities: <access denied>

01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
	Subsystem: Dell OptiPlex GX110
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at e480 [size=128]
	Memory at fdfffc00 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: <access denied>
```

Enough info for a diagnosis? TIA!

---

### Post by Iowan on 2008-04-27
> **lomnick said:**
> 
Enough info for a diagnosis?Almost... ;)
Can you **ping** the router (or the Windows box)?
Sometimes the modems will "lock onto" a MAC Address, so you might need to reset the modem for direct connection (but you might then need to reset to get router re-recognized).

---

