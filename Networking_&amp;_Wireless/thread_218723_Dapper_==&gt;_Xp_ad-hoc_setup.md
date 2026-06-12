---
title: "Dapper ==&gt; Xp ad-hoc setup"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by Culito on 2006-07-19
Hey folks,
I somehow got my D-link DWL-120 Wireless adaptor working.  I already have a LAN connection, and I want to share it through the D-Link to my ladies' XP computer (just across the room).  First up, some facts:
iwconfig:
wlan0     IEEE 802.11-DS  ESSID:"free"  Nickname:"free"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:0D:E4:CE:55:04
          Bit Rate:2 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=0/92  Signal level=-100 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

That's the D-link.  I guess it isn't getting a signal.  Anyway, on the client(XP) computer it says it has an excellent signal strength from "free", but it says "acquiring network address"....and just sits there.

On my adaptor, I gave it a static ip address as 192.168.01 and a subnet of 255.255.255.0, no encryption.  Any ideas on what else to do?

Tanx, --C

---

### Post by OpsVentus on 2006-07-19
If you want to use DHCP on the client computer, you have to setup a dhcp-server on your computer.
Install "dhcpd".
Have a look at this howto:
[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)
There's explained howto share your internet connection.

Good luck,
Bart.

---

### Post by Culito on 2006-07-19
Thanks!

Haven't got it to work yet, but...with some more tinkering...

---

