---
title: "Can't connect at hotspots?"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by Ripfox on 2006-09-17
Ok, I have figured out alot of things in Ubuntu...including how to get my wireless working with ndiswrapper and my wep key. (at home) but this is driving me NUTS. Whenever I go to a hot spot like say a hospital (my gf has frequent procedures) or the laundrymat or a hotel, I cant seem to get on the net. These are "open" connections, and when i click on "networking" under "system" I see the wireless networks in the dropdown menu and select dhcp, but there is no wep key since it is "open", right? Well I click "activate" and it appears to be connected. Even Kwifi manager says "ultimate" connection, but no go with the browser. No internet. Sorry this was so long but I felt I needed to explain well to get help. Thanks everybody!

---

### Post by MrHorus on 2006-09-18
Once you're connected, does it when work if you try dhclient?

I had to set mine up to run dhclient manually once it connects.

---

### Post by Ripfox on 2006-09-18
Well, I didn't even know what dhclient was...but the command seems to execute from the terminal. Do I just run that after it connects at the hospital? I haven't been able to try it yet, what exactly does it do? Thanks all.

---

### Post by Ripfox on 2006-09-18
This is what I got after it said it was connected at the laundromat down the street...I had no activity in the browser so I executed sudo dhclient and:


Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:14:bf:c1:16:dc
Sending on   LPF/wlan0/00:14:bf:c1:16:dc
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
Trying recorded lease 192.168.1.102
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

---

