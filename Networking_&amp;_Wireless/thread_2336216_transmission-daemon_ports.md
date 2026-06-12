---
title: "transmission-daemon ports"
date: 2016-09-06
forum: Networking &amp; Wireless
---

### Post by shindax on 2016-09-06
Good afternoon. I get internet thru the [COLOR=#000000][FONT=verdana]Netgear WNR834B v2. [/FONT][/COLOR]router. It distributes internet into local home network by dhcp service. Also, there are two Ubuntu servers 14.04.03 and 16.03 in local network. Each of it have a static IP 192.168.0.11 and 192.168.0.10 resp. Both server have installed transmission-daemon service with rpc-ports 9091 and 9090 respectively, peer ports are 51413 and 51414 resp. All ports are forwarded at router from WAN to LAN to the same ports, and respectively local adresses of servers. Router has a DMZ property. There is a some problem. From internet i see server is pointed as DMZ-server only. I.e. if pointed 192.168.0.10 i view my torrent jobs in browser, and in Transmission remote-GUI, but i can't see second server. If i point 192.168.0.11, i see second server, but not second, i.e. not both simultaneously. More than one DMZ-server not allowed. If i not point any DMZ-server, i cant see both servers. In all the above cases, i have accsess to my servers by ssh, ftp, i have accsess to MySQL, Webmin, and e.t.c. I understand, that more other ports must be forwarded, but dont find any additional info. I would be happy advice, thanks in advance.

---

### Post by howefield on 2016-09-06
Welcome to the forums, thread moved to the "*Networking & Wireless*" forum probably a better fit.

---

### Post by ian-weisser on 2016-09-07
See [https://trac.transmissionbt.com/wiki/PortForwardingGuide](https://trac.transmissionbt.com/wiki/PortForwardingGuide)

Transmission uses a default port 51413.
Obviously, both systems cannot use the same port on the router.
Change the port on one of them to 51412 (or whatever), using Transmission's settings. Then restart the daemon to reload the config.

On your router, forward port 51413 to the correct machine, and 51412 (or whatever you chose) to the appropriate machine.

---

### Post by shindax on 2016-09-09
I wrote above : 'peer ports are 51413 and 51414 resp.', servers adjusted accordingly. Or I don't understand something?

---

### Post by ian-weisser on 2016-09-09
If you have the router and networking set up properly, then I don't understand the relevance of the DMZ.

---

### Post by papibe on 2016-09-09
Hi shindax.

It seems the problem lays on how the Netgear WNR834B v2 interprets both rules. That is, a combination of port forwarding rules, and DMZ.

Some routers disable all port forwarding when a DMZ is set. Some support both: first port forwarding and then DMZ.

In any case, this problem requires more specific knowledge of the router rather than general networking. Unless you are using DMZ for a specific reason, I would disable it. If you need the DMZ, I would get more details on the router manual, or in router's forums like dslreports.

The worst case would be that you need the DMZ and the router doesn't support both rules. In this case, you could forward/allow the ports by using iptables on the DMZ host.

Just some thoughts,
Regards.

---

### Post by shindax on 2016-09-11
Thank you all for answers. At first a'll try to replace a router. After that, i will write here about results.

---

