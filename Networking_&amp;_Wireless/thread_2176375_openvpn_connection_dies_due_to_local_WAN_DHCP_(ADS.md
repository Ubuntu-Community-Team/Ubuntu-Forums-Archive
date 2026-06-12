---
title: "openvpn connection dies due to local WAN DHCP (ADSL)"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by sjhupp on 2013-09-24
Hi, hoping someone can help me please.
I have ubuntu server 12.04 running on my little home microserver, and it has all the goodies like torrents, usenet etc, and I chose to purchase a VPN service. I set up as the server as the client and push all traffic down there by default (don't think I'm clever enough to mess with routing tables to pick and choose which traffic goes where) and it all works great... most of the time.
Issues arise when my WAN connection, a standard ADSL connection to my ISP, changes its DHCP lease.
When this happens my tunnel stops working. It doesn't get pulled down, just black holes.
So I have to 'sudo service openvpn stop' and then similar to restart it.
Then all is well again until the next DHCP lease, which may be a few days away.
Obviously this is a pain, as I'd prefer not to have to SSH in and fix it so often.
Does anyone have a good solution?
I cannot use my gateway router for anything (Juniper SRX) as it doesn't support openvpn, so think I need to leave the client config on the server, but it won't know of a WAN IP change.
Any help appreciated.

---

