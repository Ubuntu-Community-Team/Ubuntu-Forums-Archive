---
title: "REQ Help, OpenVPN / D-Link / VMware"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by melgish on 2008-09-10
I'm not sure where to begin and what info is needed, but I think I'm in over my head, and could use some advice.

My network looks like this:

THE INTERNET (also known as Y'all)
ROUTER (dlink DGL-4300 router on 192.168.8.1 / 255.255.255.0
--Additional Route (192.168.7.0 / 255.255.255.0 -> 192.168.8.199

UBUNTU SERVER (192.168.0.199)
--OpenVPN as Router 192.168.7.0 / 255.255.255.0
----push "route 192.168.8.0 255.255.255.0"
--VMware Server 
----Guest 1 (Windows Server) 192.168.8.198
----Guest 2 (Windows Server) 192.168.8.197
----Guest 3 (Windows XP) 192.168.8.196

3 OTHER MACHINES (192.168.8.x)

All 192.168.8.x addresses are provided by router DHCP with static reservations for machines listed here.

Most things seem to work fine, with the following caveats (i.e. things I want advice about)

1. user route on ROUTER isn't pushed to clients.  I had to "ROUTE -p ADD 192.168.7.0 MASK 255.255.255.0 192.168.8.199" to get return traffic over VPN.  (is this a D-Link problem, an OpenVPN problem or something else?)

2. Over VPN most addresses resolve correctly to 192.168.8.x addresses.  The one notable exception is the VPN host itself which resolves to an address in the 172.x.y.z range.  This seems to be what's assigned to adapter "vmnet1".  How do I fix to resolve against "eth0"?

Any help would be most appreciated.  I'll provide whatever info is necessary.

---

