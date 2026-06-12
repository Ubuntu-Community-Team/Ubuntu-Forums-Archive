---
title: "Wireless connection lost to WEP"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by Worbly on 2007-09-01
I downloaded Ubuntu 7.04 and loaded it onto an old Panasonic laptop with a PCMCIA wireless card (D-Link DWL-650). Out of the box the wireless connection worked perfectly, so I assumed that the card was supported and functioning properly.

I connect to the internet through my landlord's wireless router downstairs in her apartment. After I had everything working properly, she decided she needed to enable WEP encryption on her router. She gave me the key, and I have had no problems connecting on a Windows machine, but I cannot connect using the key on the Ubuntu system. 

My key limitation is that the router is in someone else's apartment, and let's just say that she is not very technically savy. Because of this it's really difficult for me to get any information about the router itself. She can't tell me if the key is open or shared, or if it's WEP 128-bit Passphrase, WEP 64/128-bit Hex or ASCII, although I've tried entering the key as all 6 of those options and gotten nowhere. Also I am brand new to linux, so I wouldn't classify myself as particularly savy either...

So I wonder if anyone has any suggestions where to go with this? I don't understand why enabling WEP encryption on the router would make me unable to connectl...

Some information from my system (commands I've seen posted in other threads):

sudo gedit /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth2 
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iwlist scan:

lo  Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
wifi0  Scan completed :
 Cell 01 - Address: 00:0f:B3:1E:44:61
               ESSID:"ACTIONTEC"
               Mode:Master
               Frequency:2.452 GHz (Channel 9)
               Signal level=-83 dBm Noise level=-90 dBm
               Encryption key:on
               Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
               Extra:bcn_int=200
               Extra:resp_rate=110
eth1  Scan completed :
 Cell 01 - Address: 00:0f:B3:1E:44:61
               ESSID:"ACTIONTEC"
               Mode:Master
               Frequency:2.452 GHz (Channel 9)
               Signal level=-83 dBm Noise level=-90 dBm
               Encryption key:on
               Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
               Extra:bcn_int=200
               Extra:resp_rate=110

iwconfig:
lo  no wireless extensions.
eth0  no wireless extensions.
wifi0  IEEE 802.11b ESSID:"ACTIONTEC " Nickname:" "
         Mode:Managed Frequency:2.452 Ghz Access Point: 00:0F:B3:1E:44:61
         Bit Rate:11 Mb/s Sensitivity=1/3
         Retry limit:8 RTS thr:off Fragment thr:off
         Power Management:off
eth1 IEEE 802.11b ESSID:"ACTIONTEC " Nickname:" "
         Mode:Managed Frequency:2.452 Ghz Access Point: 00:0F:B3:1E:44:61
         Bit Rate:11 Mb/s Sensitivity=1/3
         Retry limit:8 RTS thr:off Fragment thr:off
         Power Management:off
         Link Quality=16/70 Signal level=-84 dBm Noise level=-100 dBm
         Rx invalid nwid:0 Rx invalid crypt:2 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:63 Missed beacon:0

sudo lshw -C network:
*-network
description: Link DWL-650 11Mbps WLAN Card
product: Version 01.02
vendor: D
physical id: 0
slot: socket 0
resources: irq:3
*-network
 description: Ethernet interface
 product: RTL-8139/8139C/8139C+
 vendor: Realtek Semiconductore Co., Ltd.
 physical id:2
 bus info: pci@02:02.0
 logical name: eth0
 version: 10
 serial: 00:80:45:19:c9:90
 width: 32 bits
 clock: 33MHz
 capabilities: bus_master cap_list ethernet physical tp mii 10bt-fd 100bt 100bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
 resources: ioport:4400-44ff iomemory:d0602400-d06024ff irq:9
*-network
 description: wireless interface
 physical id: 1
 logical name: eth1
 serial: 00:05:5d:ed:bf:58
 capabilities: ethernet physical wireless
 configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.3.5 multicast=yes wireless=IEEE 802.11b

Thank you so much for any help you can offer, and let me know if there is any other information I can provide!

---

