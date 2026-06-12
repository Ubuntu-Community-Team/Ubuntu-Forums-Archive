---
title: "NAT and router behind"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by flygin on 2006-12-25
I have a TEW-431BRP wireless router.
I tried to set it up in the following way, because the modem has PPPoA but the router not (PPPoA slightly better thatn PPPoE) and I could not forward ports from the modem via router to my station.

[FONT="Fixedsys"]modem ---- computer (eth0) 
                 computer (eth1) -- router (+wlan) --- .. stations
[/FONT]

The router has 4 lan ports and one wlan port. 
I used firestarter to forward the eth1 but without success. (I also tried iptables)
                                                                 
what confusues me is the wan port on the router. I think whatever is not the nework configured in the router will be routed to the wan port. However, ping tests were not successful.

what the trick??

---

