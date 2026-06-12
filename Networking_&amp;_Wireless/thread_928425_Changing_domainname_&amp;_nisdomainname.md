---
title: "Changing domainname &amp; nisdomainname"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Nitewalker on 2008-09-24
I am trying to change my domainname and not having any luck, I have tried reading different posts but noting lets me fix it.  It is "xxx-laptop" now and I am wanting to change it to just "xxx".  I changed everything in "etc/hostconfig" to "xxx.homeip.net", and when I do a "hostname" I get the correct "xxx" but if I do a "domainname or a nisdomainname or ypdomainname I get "xxx-laptop".  When I do a dnsdomainname I get the "homeip.net".  How do I change the ones that are still showing xxx-laptop:confused:

---

### Post by Iowan on 2008-09-24
Anything in **man hostname** helpful? It mentions the **/etc/hosts** file.

---

