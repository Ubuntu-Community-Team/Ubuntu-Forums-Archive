---
title: "Dead end!"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by nicculus on 2006-08-03
Hi,

I just installed dapper on my Dell 600m laptop with a Intel 2100 wireless card.  The install went fine other than I seem to be unable to get my wireless card to associate with my router.  I can see my router, my brothers and my neighbors:

nicculus@ubby:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:38:91:B4
                    ESSID:"meezer"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-40 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0F:B5:ED:EB:C8
                    ESSID:"Rogers"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-62 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
I am trying to connect to meezer.  It has no security on at the moment just while trying to get it to work.  Here is my interfaces:

nicculus@ubby:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless_mode managed
wireless-essid meezer

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless-essid meezer



I have tried both ndiswrapper and the ipw2100 driver that I compiled with the same results.  I don't seem to be getting a DHCP response from the router when it sends out a broadcast request.

nicculus@ubby:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller ( rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97  Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Fir eGL 9000] (rev 02)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabi t Ethernet (rev 01)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (re v 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (re v 20)
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini  PCI Adapter (rev 04)

nicculus@ubby:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0c:f1:38:59:51
Sending on   LPF/eth1/00:0c:f1:38:59:51
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

nicculus@ubby:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0C:F1:38:59:51
          inet6 addr: fe80::20c:f1ff:fe38:5951/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:fafef000-faff0000

nicculus@ubby:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s
          RTS thr:1600 B   Fragment thr:2344 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am currently on ndiswrapper (I think, I updated some packages automatically and rebooted, and before the reboot I know I was using ndiswrapper on wlan0 and now it looks like ndiswrapper on eth1.  Eth1 was the ipw2100 driver before).

 nicculus@ubby:~$ dmesg|tail
[17179812.724000] ndiswrapper (NdisMIndicateStatus:1760): unknown status: 400100FE
[17179827.248000] ndiswrapper (NdisMIndicateStatus:1760): unknown status: 400100FE
[17179880.484000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179880.484000] tg3: eth0: Flow control is on for TX and on for RX.
[17179880.488000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179896.400000] eth0: no IPv6 routers present
[17180519.472000] ndiswrapper (set_infra_mode:197): setting operating mode failed (C0010015)
[17180538.788000] eth1: no IPv6 routers present
[17181373.740000] ndiswrapper (set_infra_mode:197): setting operating mode failed (C0010015)
[17181389.664000] eth1: no IPv6 routers present

I have gotten this wireless card to work before on other disro's, but seem to be at a dead end.  I have unloaded reloaded, compiled the latest drivers, read and tried most suggestions from forums on the subject, and still no success.  Any help on this would be greatly appreciated. 

Thanks in advanced,
Nick

---

