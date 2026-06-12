---
title: "iptables route traffic to specific address through second interface"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2013-12-28
My usenet access is limited to a specific speed per IP address so I got my ISPs router/modem converted to bridge mode and have connected two routers to it (2 IPs from ISP).

On my media centre/server I have it wired into the main one I want all normal traffic to go through so all LAN connections works. I also have it wireless to the second router.

I plan on leaving one usenet access address alone on eth0 (192.168.1.100) but how can I get any access to a second access address (using dns name not ip) to go through wlan0 (192.168.2.100) therby using my second IP and giving me double speed.

I have Googled it a bit but I have never in years been able to wrap my head around iptables so I need nelp.

Also I just set up both interfaces and have not tested much but I want to make sure eth0 is always primary regardless of connection order and wlan0 is only used for the extra usenet access.

---

### Post by darkshadow on 2013-12-28
I found out how to do it without iptables. only downside was nothing worked until I changed to straight IPs instead of host names

The command was a basic as.
route add -host 11.11.111.11 gw 192.168.2.1 dev wlan0

Now the only thing I would like to figure out is going to be harder. It's the same thing (limited usenet speed by ip) but with the problem of only one access address so I don't know how to force seperate accounts to different interfaces.

---

