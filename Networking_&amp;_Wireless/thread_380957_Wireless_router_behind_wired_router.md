---
title: "Wireless router behind wired router"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by jae1227 on 2007-03-10
Last night I bought a Linksys wireless router. I needed it to work more like a wireless switch because I want my wired router to assign IP addresses with DHCP. The problem is that when I turn the DHPC server on the wireless router, the wired router is unable to assign an IP addresses and nothing works. The wireless router is a Linksys WRT54G but this problem seems generic.

---

### Post by chili555 on 2007-03-10
Not sure what your configuration might be, number of computers, rooms, etc., but several approaches come to mind.
1. Ditch the wired router altogether. What is it doing for you that the wireless won't?
2. Set up the wireless router without DHCP. Your wireless machines must then be set up with static IP's outside the range of the DHCP server on the wired router.
3. There may be another way to have two DHCP servers working the same side of the street, but I don't know of one.  As an experiment, I might try to let the wireless assign IP's in the 192.168.1.100 to 192.168.1.120 range and the wired from 192.168.1.150 to 192.168.1.170 range. 
Tell us more.

---

### Post by jlhughes on 2007-03-10
> **jae1227 said:**
> Last night I bought a Linksys wireless router. I needed it to work more like a wireless switch because I want my wired router to assign IP addresses with DHCP. The problem is that when I turn the DHPC server on the wireless router, the wired router is unable to assign an IP addresses and nothing works. The wireless router is a Linksys WRT54G but this problem seems generic.

I have a similar setup. You DON'T want DHCP running on the wireless router. 

Essentially, I needed to turn the wireless router into a dumb wireless access point. (To go with the dumb operator.)

On the wireless router, ignore the WAN settings.

Change the LAN IP address to something compatible with the existing wired network. (In my case, change it from the default 192.168.0.xxx to 192.168.1.xxx)

Turn OFF the DHCP server on the wireless router. (Wired server has DHCP running)

Most important: Plug the LAN wire feeding the wireless router into a LAN plug and NOT the WAN plug.

Everything now works.

---

