---
title: "Home network with multiple routers?"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by erikcw on 2006-08-28
Hi all,

My home network is setup with 2 routers.
-A vonage linksys RTP300 router. (IP range 192.168.15.xxx)
-A Compex NetPassage 26G Wireless Router (IP range 192.168.168.xxx)

The vonage router is plugged into the cable modem, and provides the VOIP and has the office computer, and the wireless router plugged into it.

The setup works great for internet browsing, but LAN file and print sharring is not working.  The pc that are on one router cannot ping the IPs of the PCs on the other router.

How can I configure the routers to allow LAN traffic between each other?  I think NAT might have something to do with it, but I'm not sure where to go from here...

Thanks!

---

### Post by NetworkGuy on 2006-08-28
I would start by turning off the firewall on the unit that isn't on the Internet. The firewall would block the file and print sharing between the two networks

---

### Post by erikcw on 2006-08-28
I switched off the NAT and firewall for the wireless router, but my pc on the other router still can't ping anything in the other router's IP range.

Do I need to somehow configure them to both use the same IP range or turn of DHCP or something?

Thanks!

---

