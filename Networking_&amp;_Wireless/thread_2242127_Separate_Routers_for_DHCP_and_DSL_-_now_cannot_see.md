---
title: "Separate Routers for DHCP and DSL - now cannot see Internet"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by trisgti2 on 2014-08-30
hi all - this is not specifically a Linux problem, but I'm hoping someone out there will be able to help me...

 
the router supplied by my broadband supplier (Technicolor TG582n) has  been struggling with all my internal network requirements and is a pig  to configure. 
 
I decided to dig out my old Netgear DG834GT router to use as for DHCP  and wireless, just leaving the Technicolor as the DSL modem. 
 
everything is set up on the internal network and working fine, except  nothing can access the internet.  I can get to the Technicolor config  page (via the router's IP). 
 
I have tried re-enabling DHCP on the Technicolor and connecting the  laptop to that and can access the internet, so I know it is connected  ok. 
 
 
any ideas?  is there a setting on the Netgear that I've missed somewhere? 
 
any help would be most appreciated [IMG]http://i.diynot.com/smilies/icon_smile.gif[/IMG]

---

### Post by weatherman2 on 2014-08-30
Leave DHCP turned on on your Technicolor.  Make sure your Netgear's WAN option is set to "DHCP" or "Automatic" not "static" or "PPPoE" or something else.

Connect your Netgear's WAN port to one of the LAN ports on the Technicolor, to get internet.

Make sure the DHCP range on the Technicolor is different from the one on the Netgear - for example, if Technicolor uses 192.168.1.1 make sure the Netgear uses 192.168.2.1 or some other subnet range.  If they are now the same it's probably easier to change the Netgear's range.

Finally - power cycle (turn off and then back on) the Technicolor once.  Sometimes, it will need to register a new MAC address attached to it (though I doubt it - but shouldn't hurt!).

If this works, then the only complication is that you have two different subnets to navigate if, say, you need to forward ports or something.  You can always fix the IP of the Netgear's WAN if you need to (because my suggestion above is to use DHCP on the Technicolor - in other words, you may not be able to guarantee what the IP of the Netgear's WAN is - 192.168.2.3 ?  192.168.2.4?  May not be the same every time unless you fix it or make a DHCP reservation for it.).  If you aren't forwarding any ports now, you probably don't have to worry about this at all.

---

