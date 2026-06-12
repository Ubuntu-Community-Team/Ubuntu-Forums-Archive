---
title: "Weird networking issue"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by carlos1992 on 2007-11-21
Hi guys, well i cannot connect to some wesite (chilehardware, Wikipedia, etc) but i still can connect to Google, Ubuntu forums
i tryed disable ipv6 (didn't work) maybe changing my sources (i can't update(didn't work)
I've tryin' to fix it but i'm got tired of trying (i'm still tryin xD) here some specs:

> velar@ubuntu-ultimate:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:E7:5C:41  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14712593 (14.0 MB)  TX bytes:1307387 (1.2 MB)
          Interrupt:16 Base address:0x8f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:840 (840.0 b)  TX bytes:840 (840.0 b)

> avelar@ubuntu-ultimate:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
        Subsystem: ASRock Incorporation Unknown device 2560
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation Unknown device 2562
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Unknown device 24c0
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at e400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Unknown device 24c0
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation Unknown device 24c0
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ec00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 24c0
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at dff7bc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dfd00000-dfdfffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation Unknown device 24c0
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fc00 [size=16]
        Memory at 10000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
        Subsystem: ASRock Incorporation Unknown device 434d
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at d800 [size=256]
        I/O ports at d400 [size=64]
        Memory at dff7ba00 (32-bit, non-prefetchable) [size=512]
        Memory at dff7b900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: Unknown device 4c21:5349
        Flags: medium devsel, IRQ 16
        I/O ports at e000 [size=256]
        I/O ports at dc00 [size=128]
        Capabilities: <access denied>

03:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: ASRock Incorporation Unknown device 8139
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at cc00 [size=256]
        Memory at dfdfff00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>


> avelar@ubuntu-ultimate:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

and i tryed to ping to Google.com but i took so long, about 10 minutes and the terminal restarted itself (autoerased) but i can connect to it here's a example

> avelar@ubuntu-ultimate:~$ wget [www.google.com](www.google.com)
--15:55:16--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 209.85.165.147, 209.85.165.99, 209.85.165.103, ...
Connecting to www.google.com|209.85.165.147|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.google.com.sv/](http://www.google.com.sv/) [following]
--15:55:16--  [http://www.google.com.sv/](http://www.google.com.sv/)
           => `index.html'
Resolving [www.google.com.sv](www.google.com.sv)... 209.85.165.103, 209.85.165.104, 209.85.165.147, ...
Reusing existing connection to [www.google.com:80](www.google.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,279         --.--K/s             

15:55:17 (141.39 MB/s) - `index.html' saved [3279]


and a website i cannot connect 
> avelar@ubuntu-ultimate:~$ wget [www.chilehardware.com](www.chilehardware.com)
--15:49:16--  [http://www.chilehardware.com/](http://www.chilehardware.com/)
           => `index.html'
Resolving [www.chilehardware.com](www.chilehardware.com)... 209.62.12.130
Connecting to www.chilehardware.com|209.62.12.130|:80... failed: Connection timed out.
Retrying.

--15:52:26--  [http://www.chilehardware.com/](http://www.chilehardware.com/)
  (try: 2) => `index.html'
Connecting to www.chilehardware.com|209.62.12.130|:80... failed: Connection timed out.
Retrying.

--15:55:37--  [http://www.chilehardware.com/](http://www.chilehardware.com/)
  (try: 3) => `index.html'
Connecting to www.chilehardware.com|209.62.12.130|:80... 


it just keeps "connecting till i got tired

---

### Post by rmemm on 2007-11-22
You might want to try to ping some of those IP addresses to see if there is actually a path.

Other thing that occurs to me -- I had some problem like this -- turned out to be DNS related.  If your using a DNS proxy on your router as the DNS server -- try the actual ISP DNS server and see if that helps.  I mention this because I had a strange problem somewhat like this and for some reason I got better results sending my DNS lookups directly to a good DNS server rather than through my router/gateway proxy.

Just a thought.

Rob

---

