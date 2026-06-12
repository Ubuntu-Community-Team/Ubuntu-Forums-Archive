---
title: "dhclient won't give me an ip.. :/"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by identitet5000 on 2006-09-13
I'm running the madwifi drivers on my Thinkpad Z60, but I haven't gotten it to give me an ip.

Here's what happens:



root@SaturnusU:/mnt# iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:11:85:FF:B3:DB
                    ESSID:"Nackademin3"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

root@SaturnusU:/mnt# iwconfig ath0 essid "Nackademin3"

root@SaturnusU:/mnt# dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:7d:dc:4b
Sending on   LPF/ath0/00:14:a4:7d:dc:4b
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
[...]



Anyone who have had a similar problem and maybe could shed a little light on this?

---

