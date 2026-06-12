---
title: "Network Manager Nudge Needed for Network Access"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by LaneLester on 2008-04-12
The basic problem is that everything seems OK, except that I can't access my LAN (can't ping the router) until I do "something" with "Network Settings" in Xubuntu. The "something" can be as little as changing the "Password type" from "WPA Personal" to "WPA2 Personal." Then full access is enabled.

The password type is irrelevant, because I don't use WPA or WEP, relying instead on MAC filtering.

Before i do the above, and I'm unable to ping the router, "sudo iwlist scanning" shows the following:

wlan0 Scan completed :
Cell 01 - Address: 00:14:BF:18:8D:A9
ESSID:"PANTHER"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:68/100 Signal level:-52 dBm Noise level:-96 dBm
Encryption keyff
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0

I believe this indicates that the driver is fine and can see the network. But the computer does not have access to the network until "Network Settings" is nudged as described above.

Can you help me eliminate the nudges?

Lane

---

### Post by sammy_pal on 2008-04-13
:( I too had the same problem in Fiesty. But the problem vanished from Gutsy onwards. In roaming mode, my network manager automatically connects to available network.

---

### Post by The Cog on 2008-04-13
I had thos problem in Gutsy after I changed fro WEP to WPA. I found that running **ifdown eth1** followed by **ifup eth1** was enough of a nudge. So I wrote this script file (I called it eth1-restart) and placed it in **/etc/event.d/**:
```
start on started rc2
start on started rc3
start on started rc4
start on started rc5

script
    ifdown eth1
    sleep 2
    ifup eth1
end script
```
The 2 second sleep was a guess and may not be needed, but doesn't get in the way.

---

### Post by sammy_pal on 2008-04-14
I have *Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) wireless card *and using WPA2 Personal, I have never faced this problem in Gutsy and Hardy *Beta*.:confused:

---

