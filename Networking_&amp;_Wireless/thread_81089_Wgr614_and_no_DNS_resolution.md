---
title: "Wgr614 and no DNS resolution"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by soaper on 2005-10-23
I've got a new laptop with an IPW2200 nic and had been using an old orinoco access point (802.11B) and a netgear rp614v2 router.  Internet access works great.  Removed all that and plugged in a netgear wgr614v6 router to take advantage of the 802.11g and can't access the net.  I pick up an address from the router just fine but it can't find anything beyond that, I get a network not found message.  If I manually enter the dns servers in my resolv.conf, I get connection refused.  When I boot this same box into windows, works fine.  When I use another laptop running Debian with a 2.4.x kernal and a B card, that gets out just fine.  Windows boxes all get out without any problems.  Any ideas, my resolv.conf is below. Thanks!

resolv.conf on old setup (all linux machines, using the rp614 router)
search hsd1.pa.comcast.net
nameserver 68.87.64.196
nameserver 68.87.66.196

resolv.conf on new setup (all linux boxes using the wgr614 router)
search 
nameserver router_address_here

---

