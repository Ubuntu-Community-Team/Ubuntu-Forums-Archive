---
title: "Atheros and Macbook Pro WEP not working"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by Stelmate on 2006-11-25
I'm having some problems getting my Atheros card in my macbook pro working.

I can do a iwlist ath0 scan and see my AP but when I try to set the key and essid I get:
ath0      IEEE 802.11a  ESSID:"DebianROUTER"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:13 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you noticed it's laveled Not-Associated.  I'm using the madwifi 0.9.1 drivers.

Also when I try to connect:
stelmate@stelmate-laptop:~$ sudo ifup ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:50:d5:af
Sending on   LPF/ath0/00:17:f2:50:d5:af
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15

The gnome network-manager is no longer showing my wifi card as well.  It use to and I don't think I changed anything, it just stopped working.  Any help would be much appreciated.

---

