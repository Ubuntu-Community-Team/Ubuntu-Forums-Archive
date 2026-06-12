---
title: "How do I Install Network Driver?"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by yatgirl on 2008-07-06
Can someone point me to some directions to properly install? I have a driver cd with the Linux drivers.

I have been using the how-to above but it assumes I know how to install the drivers.

thanks

---

### Post by Tomatz on 2008-07-06
I can't see the how-to you describe? What network adaptor is it?

---

### Post by yatgirl on 2008-07-06
The Sticky on the Networking & Wireless forum:
How To: Manual Network Configuration without the need for Network Manager

I have several nic cards, wireless and wired. I'd be happy to get the wireless going. I have this wired pcmcia card Zonet Zen1200,I have a Hawking 2.4 GHz HWC54G wireless, and a Cheifmax USB wireless.
I have driver cd's for the first 2, both have Linux drivers.

thanks

---

### Post by chili555 on 2008-07-06
Let's try the Hawking. They came with several chipsets, so let's see which one you have. Please post the output of these two terminal commands:```
lspci -v
lspcmcia -v
```The first command will spit out a lot of information, so feel free to trim out the information you are sure doesn't relate to the wireless device.

---

### Post by yatgirl on 2008-07-06
chela@ubuntu:~$ lspi -v 
bash: lspi: command not found 
chela@ubuntu:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03) 
	Flags: bus master, medium devsel, latency 64 
	Memory at 18000000 (32-bit, prefetchable) [size=64M] 
	Capabilities: <access denied> 

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode]) 
	Flags: bus master, 66MHz, medium devsel, latency 128 
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64 
	I/O behind bridge: 0000e000-0000efff 
	Memory behind bridge: fd000000-fedfffff 
	Prefetchable memory behind bridge: 30000000-300fffff 

00:04.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10) 
	Subsystem: Micron Unknown device c376 
	Flags: bus master, medium devsel, latency 64, IRQ 10 
	I/O ports at f800 [size=256] 
	Capabilities: <access denied> 

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02) 
	Flags: bus master, medium devsel, latency 0 

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master]) 
	Flags: bus master, medium devsel, latency 64 
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8] 
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1] 
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8] 
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1] 
	I/O ports at fcf0 [size=16] 

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI]) 
	Flags: bus master, medium devsel, latency 64, IRQ 5 
	I/O ports at fcc0 [size=32] 

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02) 
	Flags: medium devsel, IRQ 9 

00:0a.0 CardBus bridge: Texas Instruments PCI1251B 
	Subsystem: Texas Instruments PCI1251B 
	Flags: bus master, medium devsel, latency 168, IRQ 11 
	Memory at 30100000 (32-bit, non-prefetchable) [size=4K] 
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176 
	Memory window 0: 20000000-23fff000 (prefetchable) 
	Memory window 1: 24000000-27fff000 
	I/O window 0: 00001400-000014ff 
	I/O window 1: 00001800-000018ff 
	16-bit legacy interface ports at 0001 

00:0a.1 CardBus bridge: Texas Instruments PCI1251B 
	Subsystem: Texas Instruments PCI1251B 
	Flags: bus master, medium devsel, latency 168, IRQ 11 
	Memory at 30101000 (32-bit, non-prefetchable) [size=4K] 
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=176 
	Memory window 0: 28000000-2bfff000 (prefetchable) 
	Memory window 1: 2c000000-2ffff000 
	I/O window 0: 00001c00-00001cff 
	I/O window 1: 00002000-000020ff 
	16-bit legacy interface ports at 0001 

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc) (prog-if 00 [VGA controller]) 
	Subsystem: ATI Technologies Inc Rage LT Pro AGP 2X 
	Flags: bus master, stepping, medium devsel, latency 66, IRQ 9 
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M] 
	I/O ports at e800 [size=256] 
	Memory at fedfe000 (32-bit, non-prefetchable) [size=4K] 
	[virtual] Expansion ROM at 30000000 [disabled] [size=128K] 
	Capabilities: <access denied> 

02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface 
	Subsystem: Abocom Systems Inc Unknown device ab80 
	Flags: bus master, medium devsel, latency 64, IRQ 11 
	Memory at 24020000 (32-bit, non-prefetchable) [size=8K] 
	Memory at 24000000 (32-bit, non-prefetchable) [size=128K] 
	Capabilities: <access denied> 

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139 
	Flags: bus master, medium devsel, latency 64, IRQ 11 
	I/O ports at 1c00 [size=256] 
	Memory at 2c000000 (32-bit, non-prefetchable) [size=512] 
	Capabilities: <access denied> 

________________________________________________
chela@ubuntu:~$ lspcmcia -v 
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0) 
	Configuration:	state: on	ready: unknown 
			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V 
  CardBus card -- see "lspci" for more information 
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.1) 
	Configuration:	state: on	ready: unknown 
			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V 
  CardBus card -- see "lspci" for more information 
chela@ubuntu:~$

---

### Post by yatgirl on 2008-07-06
I think I should add this as well...

chela@ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Wireless interface 
       product: ACX 111 54Mbps Wireless Interface 
       vendor: Texas Instruments 
       physical id: 2 
       bus info: pci@0000:02:00.0 
       logical name: wlan1 
       version: 00 
       serial: 00:12:0e:1a:3e:f6 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+ 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 3 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:50:22:9b:0a:10 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

### Post by chili555 on 2008-07-06
Looks like your Hawking is all set with a driver right now. Let's see if we can connect. Please open a terminal and do:```
sudo iwlist wlan1 scan
```This should produce output something like:```
Cell 01 - Address: 99:13:19:62:8D:F7
                    ESSID:"mylilrouter"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/100  Signal level=-68 dBm  Noise level=-88 dBm
                    Encryption key:on
---snip---
```So let's try to connect:```
sudo iwconfig wlan1 essid mylilrouter
sudo iwconfig wlan1 key <my_WEP_key>
sudo dhclient wlan1
```Skip 'key' if you do not have any encryption. Did you connect?

By the way, since this card got wlan**1**, I think another of your cards grabbed wlan0 and is also all set for drivers.

---

### Post by yatgirl on 2008-07-06
chela@ubuntu:~$ sudo iwlist wlan1 scan 
[sudo] password for chela: 
wlan1     Scan completed : 
          Cell 01 - Address: 00:11:50:4A:C2:38 
                    ESSID:"belkin54g" 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=50/100  Signal level=30/100  Noise level=0/100 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 

chela@ubuntu:~$ sudo iwconfig wlan1 essid belkin54g 
chela@ubuntu:~$ sudo dhclient wlan1 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/wlan1/00:12:0e:1a:3e:f6 
Sending on   LPF/wlan1/00:12:0e:1a:3e:f6 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 19 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
chela@ubuntu:~$ 

Also, should I close the manual network config thingy (the gui one) that has the icon by my battery meter?

Thanks again for helping me. I sure hope I have some wifi in my near future :) I am really liking Gnome. :)

---

