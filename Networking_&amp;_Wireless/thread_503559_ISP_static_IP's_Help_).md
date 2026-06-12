---
title: "ISP static IP's Help :)"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by RichGuk on 2007-07-18
Hello,

I currently have a Netgear DG834 router and I'm going to be requesting a block of static IP's from my ISP (4 or maybe 8) and would like to have some of my PC's using the static IP's assigned by my ISP so I can access them from else where in the world but I'll also need some of the PC's still behind the NAT stuff so I'd like to still be able to use the 192.168.0.x private IP's etc... I heard that to get the static ISP assigned IP's to work I'd need to turn NAT off on the router but that'll take out the private IP's?

My main question I suppose is I do have another router, Linksys WAG354G would it be possible to get this router to do the DHCP and private IP' stuff and the other router does public IP's or would I be best turning one of my linux boxes into a router for the private IP's?

Thanks,

Rich

---

### Post by jarrett on 2007-07-18
Hmmm.. I guess you need to use the netgear as a bridge, so you'll get a IP from your isp on the linksys router, then enable NAT on the linksys one and redirect the ports you want on the linksys. If the linksys router gets an IP from the isp then it would answer on all ports on that ip and redirect as needed to the computer(s) in question.

---

