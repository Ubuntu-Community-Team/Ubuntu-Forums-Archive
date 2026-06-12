---
title: "is this subnet correct?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by darco on 2007-10-30
My ISP is giving me 24.4.232.xxx IP address but I noticed I have a 255.255.255.0 subnet? Is that right? I thought a 24. would be considered a Class A Address and the subnet would be 255.0.0.0?
Been awhile since I took a networking class :(

dr

---

### Post by mpokrywka on 2007-10-31
One should assume his ISP is competent enough to give him correct IP configuration data :-)
Nowadays network classes are not used as in past because IP address shortage, see [http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)
Even if your ISP has /8 subnet (unlikely) they probably divided it on smaller subnets to easier manage broadcast domains and to efficiently route data between geographically and logically divided parts of internal network.
EDIT:
You can check "whois 24.4.232.1" and see networks assigned for your ISP (at least in your closest range, I bet they have more subnets assigned).

---

### Post by airbornemist6 on 2007-10-31
Yup, your ISP is most likely using Variable Link subnetting. Worry not, for your subnet is correct!

---

