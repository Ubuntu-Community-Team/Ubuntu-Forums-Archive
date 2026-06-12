---
title: "Sometimes IP's can't be loaded (but only on one Port)"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by Wild-Storm on 2006-12-07
Hi,
i've got a problem:
Sometimes my machine (Ubuntu Dapper Drake) is unable to load any information from an IP (pingin works). But the strange thing is, that it's not the whole portrange, but only a specicified port. E.g. HTTP (:80) works, but FTP (:21) doesn't. This varies with the time, and after a random time (mostly between 1 minute and about 30 minutes) i am again able to load the page/ip/port.

I've got a DNS-Entry and my MTU-Value is 1500. But setting it down doesn't change anything.

Neatgear WGT624Tv3 Router + T-Sinus 111 Data Router/Modem
WLAN Card (PCI): Atheros AR5212 802.11abg NIC (Netgear WG311T)

wildstorm@my-0wn:~$ route
Kernel IP Routentabelle
Ziel Router Genmask Flags Metric Ref Use Iface
192.168.1.0 * 255.255.255.0 U 0 0 0 ath0
172.16.250.0 * 255.255.255.0 U 0 0 0 vmnet1
192.168.104.0 * 255.255.255.0 U 0 0 0 vmnet8
default 192.168.1.1 0.0.0.0 UG 0 0 0 ath0 <--Genmask 0.0.0.0?

wildstorm@my-0wn:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"WiLD-108MBiT" Nickname:"WiLD-108MBiT"
Mode:Managed Frequency:2.462 GHz Access Point: 00:14:6C:20:CC:AA
Bit Rate:48 Mb/s Tx-Power:18 dBm Sensitivity=0/3
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=22/94 Signal level=-73 dBm Noise level=-95 dBm
Rx invalid nwid:17320 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:163 Invalid misc:163 Missed beacon:2


I'm using "Netzwork-Manager-Applet 0.6.2", but before that, it didn't worked either :(

I would be very pleased about a solution/help :)

---

