---
title: "problem connectin to internet after upgrade from 7.04 to 7.10"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by mshaheen on 2007-10-19
after a successful upgrade to ubuntu 7.10 i lost my connection to the internet completely 
everything was working in temrs of hardware , i had my IP address assigned from DHCP correctly but firefox simply couldn't connect to anything !

even trying to ping any website was not working for me 

this was solved just by doing the following 

open firefox
type " about:config" in the address bar
serch for IPV
change "network.dns.disableipv6 " from "false" to "true" by just double clicking it

that's it 
restart firefix and you should have your internet connection back to normal
i don't know what exactly happpened bt it just worked for me

---

