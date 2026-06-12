---
title: "Linksys WPC11 ver3 not working"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Dalej on 2008-05-03
I have recently installed 8.0.4 and have not been able to get my wireless to work.  It worked in windows.  
iwconfig gives me the correct AP and the router can see the wireless card.  I'm using the ORINOCO driver. ifconfig does not show an IP address.  I can't ping or scan with iwlist -- it says "eth0 Failed to read scan data : Resource temporarily unavailable".

Is there anyone who has been able to get this card to work on Hardy?
Any suggestions?

Here is my wireless info:
-----------------------------------------------------------------------------------------------------------------
iwconfig
eth0      IEEE 802.11b  ESSID:"HOMENET"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/92  Signal level=-3 dBm  Noise level=-141 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
_________________________________________________________________________________

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:06:25:ac:45:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x100 
____________________________________________________________________________________

lshw -network            
 *-network
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:06:25:ac:45:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.2 multicast=yes wireless=IEEE 802.11b
_________________________________________________________________________________________
               
ping -c 4 192.168.1.1   ROUTER
ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.4.74 icmp_seq=1 Destination Host Unreachable
From 169.254.4.74 icmp_seq=2 Destination Host Unreachable
From 169.254.4.74 icmp_seq=3 Destination Host Unreachable
From 169.254.4.74 icmp_seq=4 Destination Host Unreachable


--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3009ms
, pipe 3


lspci -v                 ***************************************************************************************
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 128
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f0000000-f7ffffff
	Prefetchable memory behind bridge: 30000000-300fffff

00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
	Subsystem: IBM ThinkPad A21m/T20/T22
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00002000-000020ff
	16-bit legacy interface ports at 0001

00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
	Subsystem: IBM ThinkPad A21m/T20/T22
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 28000000-2bfff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001

00:03.0 Communication controller: Agere Systems WinModem 56k (rev 01)
	Subsystem: IBM Unknown device 018c
	Flags: medium devsel, IRQ 11
	Memory at e8004000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=8]
	I/O ports at 1800 [size=256]
	Capabilities: <access denied>

00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
	Subsystem: IBM ThinkPad A20m
	Flags: bus master, slow devsel, latency 64, IRQ 11
	Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
	Memory at e8100000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1c10 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1c20 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
	Flags: medium devsel, IRQ 9

01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13) (prog-if 00 [VGA controller])
	Subsystem: IBM Thinkpad T20/T22
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
	[virtual] Expansion ROM at 30000000 [disabled] [size=64K]
	Capabilities: <access denied>
**************************************************************************************************************************

---

### Post by cmnorton on 2008-05-03
I am not an expert and will probably be bumbling through this tomorrow, when I upgrade two laptops, one of them my development workstation, but here goes.

1) Is it possible there is a wireless on/off switch on your laptop? I am asking, because I was bitten by this on a Thinkpad T61p.  I had no  wireless, until I found this little switch on the edge of the front cover. I had accidentally shut it off, and that was during a 7.10 install.

2) What does your /etc/network/interfaces file look like? Mine had to look this way (not counting comments in the file), or I could not connect regularly or VPN).

auto lo
iface lo inet loopback

3) Can you connect directly with an ethernet cable plugged into your router?

4) What kind of hardware is this?

5) Did you back up config files, as well as /home? I'm curious as to what your old network settings files looked like.

---

### Post by Dalej on 2008-05-03
Thanks for the reply
1) The WPC 11 is a PCMCIA card.  There is no switch that I can find and it's obviously on since the router can see it and it's MAC address.
2) My interfaces file is the same.
3) I don't have a wired ethernet on this laptop.
4) It's an IBM Thinkpad T21.
5) I didn't back them up.  I installed Ubuntu to replace windows.

---

### Post by Dalej on 2008-05-04
Bump.........

---

### Post by cmnorton on 2008-05-06
I don't know about wireless, but after a fresh KUbuntu 8.04 install my network will not start automatically. Check the output of ifconfig, and if you don't have any IP address try issuing sudo dhclient.

I cannot test easily with wireless here but the fact no network will come up automatically might help you.

---

### Post by Dalej on 2008-05-06
I finally got mine working by removing the card and reinstalling UBUNTU.
It came up with the hostap driver instead of orinoco and it now works.  My next step is to add in encryption again (I'm using MAC filter now).  
Thanks.

---

