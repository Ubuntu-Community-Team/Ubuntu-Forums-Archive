---
title: "Connects to unsecure router but no internet."
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by Josefcito on 2008-07-02
This is my first ubuntu wireless experience. I am able to connect to the wireless network. When I do I am unable to get firefox/updates to work.

HARWARE: EMACHINE t1842, LINKSYS WMP54G v.4 Wireless Card. All the threads I've read say the RT2500 driver is valid for the WMP54G. I'm not sure what step I'm missing? 

Here is some data from terminal:
[B][COLOR="Black"][INDENT]
uname -a
Linux joe-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:2b:43:d6:27  
          inet addr:192.168.1.97  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::240:2bff:fe43:d627/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2964396 (2.8 MB)  TX bytes:578337 (564.7 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108800 (106.2 KB)  TX bytes:108800 (106.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:71:8e:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5327 (5.2 KB)  TX bytes:10658 (10.4 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:12:17:71:8e:07  
          inet addr:169.254.3.239  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-71-8E-07-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ lspci -nv
00:00.0 0600: 8086:2560 (rev 03)
	Subsystem: 109f:3189
	Flags: bus master, fast devsel, latency 0
	Memory at ec000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA controller])
	Subsystem: 109f:3189
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 0c03: 8086:24c2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 109f:3189
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1d.1 0c03: 8086:24c4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 109f:3189
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1820 [size=32]

00:1d.2 0c03: 8086:24c7 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 109f:3189
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]

00:1d.7 0c03: 8086:24cd (rev 02) (prog-if 20 [EHCI])
	Subsystem: 109f:3189
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at e8080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 0604: 8086:244e (rev 82) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: e8100000-e81fffff

00:1f.0 0601: 8086:24c0 (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 0101: 8086:24cb (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: 109f:3189
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 0c05: 8086:24c3 (rev 02)
	Subsystem: 109f:3189
	Flags: medium devsel, IRQ 9
	I/O ports at 1880 [size=32]

00:1f.5 0401: 8086:24c5 (rev 02)
	Subsystem: 109f:3189
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e8080c00 (32-bit, non-prefetchable) [size=512]
	Memory at e8080800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:02.0 0200: 10ec:8139 (rev 10)
	Subsystem: 109f:3189
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at 2000 [size=256]
	Memory at e8112000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:09.0 0780: 14f1:2f00 (rev 01)
	Subsystem: 155d:8d8b
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e8100000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 2400 [size=8]
	Capabilities: <access denied>

02:0a.0 0280: 1814:0201 (rev 01)
	Subsystem: 1737:0032
	Flags: bus master, slow devsel, latency 64, IRQ 21
	Memory at e8110000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11  ESSID:"belkin546"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:43:AB:F7   
          Tx-Power=26 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT][/COLOR][/B]

---

### Post by superprash2003 on 2008-07-02
in your terminal type ping google.com and post output here

---

