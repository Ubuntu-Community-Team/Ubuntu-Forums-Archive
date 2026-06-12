---
title: "Netgear WG511T help please"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by xpantz on 2007-03-21
Hey All

I'm having another shot at Ubuntu.

I was using a USB wirless device but gave up on it and bought a Netgear WG511T

It doesnt seem to want to work for me either.

I have reinstalled 6.10 The only change I have made so far is to install the restricted modules.

WG511T is blinking 'side to side'
Network Tools lists ath0 and wifi0 as 'unknown interface'

Could somebody have a look at the outputs below please.
(I note some errors in the output from 'sudo dhclient atho')

Anything else I can report?

Thanks



 > lspci -v

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Subsystem: Compaq Computer Corporation Armada M700/E500
        Flags: bus master, medium devsel, latency 64
        Memory at 50000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 40000000-410fffff
        Prefetchable memory behind bridge: 28000000-280fffff

00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
        Subsystem: Compaq Computer Corporation Armada E500
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 41100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
        Subsystem: Compaq Computer Corporation Armada E500
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 41180000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 24000000-25fff000 (prefetchable)
        Memory window 1: 26000000-27fff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 3420 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 3400 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
        Subsystem: Compaq Computer Corporation Armada M700/E500
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 3000 [size=256]
        Capabilities: <access denied>

00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
        Subsystem: Intel Corporation EtherExpress PRO/100+ MiniPCI
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at 41280000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3440 [size=64]
        Memory at 41200000 (32-bit, non-prefetchable) [size=128K]
        [virtual] Expansion ROM at 28100000 [disabled] [size=1M]
        Capabilities: <access denied>

00:09.1 Serial controller: Agere Systems LT WinModem (prog-if 00 [8250])
        Subsystem: Intel Corporation PRO/100+ MiniPCI on Armada E500
        Flags: medium devsel, IRQ 11
        I/O ports at 3430 [size=8]
        Memory at 41300000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Armada E500
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=256]
        Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 28000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Netgear Unknown device 5b00
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 22000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>



 > sudo ifconfig

ath0      Link encap:Ethernet  HWaddr 00:14:6C:7F:8D:E2  
          inet6 addr: fe80::214:6cff:fe7f:8de2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:93:4A:E6  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe93:4ae6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10281493 (9.8 MiB)  TX bytes:490832 (479.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-7F-8D-E2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43119 errors:0 dropped:0 overruns:0 frame:43588
          TX packets:102196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3760160 (3.5 MiB)  TX bytes:5416388 (5.1 MiB)
          Interrupt:11 Memory:d0b40000-d0b50000 


> sudo dhclient atho

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
atho: ERROR while getting interface flags: No such device
atho: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device


> sudo lspci | grep Ethernet

00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


 > sudo iwlist ath0 scanning

ath0      Scan completed :
          Cell 01 - Address: 00:13:D3:7B:FA:52
                    ESSID:"Moonbase Alpha"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/94  Signal level=-49 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:50:18:3B:C5:D0
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:B5:BC:3E:EA
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/94  Signal level=-71 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 04 - Address: 00:50:18:3B:C5:D0
                    ESSID:"Moonbase Bravo"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

---

### Post by xpantz on 2007-03-22
Just installed the latest Feisty alpha for the exercise.

Detected the card.

Detected both my wireless networks... and all my neighbours.

Just wanted the WPA2 KEY.

Hooked right up.

Way to go Ubuntu!

---

### Post by ffxr on 2007-03-22
im getting the same card.. do you know if its using NDISWRAPPER or native linux drivers.. ?

---

### Post by xpantz on 2007-03-22
> **ffxr said:**
> im getting the same card.. do you know if its using NDISWRAPPER or native linux drivers.. ?

When I first installed Feisty it appeared to be using native support.

However after letting the machine update I received a warning from 'Restricted Driver Management' that it was using proprietary drivers that cannot be supported.

Atheros Hardware Access Layer.

NDISWRAPPER is not installed.

---

