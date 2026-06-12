---
title: "Home DNS"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by dingue on 2010-09-03
Hi,

I would like to setup a dns for my home network and have been looking at dnsmasq. I want to keep my router as the dhcp server and primary dns for my network but I want the internal dns to serve as a dns for my internal computers so I can access them by name instead of IP. I want to do it this way because if my server goes down I want the rest of the network to still be able to access the web

Can I do this with dnsmasq or do I need to use something else. Most of what I read about dnsmasq is using both the dns and dhcp services but I only want the dns services.

Thanks in advance
Dingue

---

### Post by CharlesA on 2010-09-03
You should be able to set yer router up as a local dns server. If not, then you'd just have to set yer local dns server as primary and the router's dns as secondary in order to resolve local names.

---

### Post by DavePlummer on 2010-09-03
If your router is supported by dd-wrt, which uses dnsmasq for both dhcp and local dns, you could install dd-wrt on the router. That's what I use, and it has served me very well.

---

### Post by dingue on 2010-09-03
I have Billion 7401VGPR3 and I thought it was supposed to be a DNS server. I have the use router as dns server ticked and I use the fixed host dhcp feature yet when I try tp access a node by its name I get a not found response. Has anyone had any experience with this router that might be able to shed some light on the matter.

---

