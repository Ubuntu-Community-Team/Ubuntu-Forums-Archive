---
title: "Internet Connection Troubles"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by marcus_pearce on 2005-06-08
Hi there, I'm an absolute beginner with ubuntu, however i'm an MCSE for the windows stuff. So i thought i would try and build a spare laptop with this Linux stuff. everything seems to be ok but i can't get the internet connection working. sometimes it works but not consistently, sometimes it doesn't work at all, just says connecting to [www.website.com](www.website.com) ....... Anyway i appear to have an ip address provide by my router, i can ping both the url and the ip address of the router and web sites outside eg bbc and google. so this would suggest that all is ok, all seems to go wrong when i browse. DNS is set to be the router and the connection setting in the browser (mozilla) are set to direct connection to the internet.  I have three windows machines all connecting through the router and they are all fine. The Laptop is a dell latitude LS It would be great if anyone had any ideas, Thanks

Marcus ](*,)

---

### Post by kleeman on 2005-06-08
This sounds like a possible ipv6 issue. To resolve this issue in firefox enter 

about:config

in the address bar

In the filter box at the top enter "ipv6"
this will give the line
network.dns.disableIPV6
which will be set to false
reset to true by double clicking

---

### Post by marcus_pearce on 2005-06-08
Fantastic, this worked! don't understand why but it did! could you tell me what i did or give me a link to some resources that explain. Also now i've found an expert how do i get my Buffalo airstation wli-usb-kb11 wireless adapter working? i take it it needs drivers as it doesn't recognise this, any ides?

---

