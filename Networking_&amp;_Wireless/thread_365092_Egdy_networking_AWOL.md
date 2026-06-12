---
title: "Egdy networking AWOL"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by CrowBoy1960 on 2007-02-19
Hi all,

I've been using Ubuntu for around 2 years now and love it. Recenty however my networking has gone missing :(. I'm using Edgy with kernel 2.6.17-11 .If I try and ping my router I get "Destination unreachable". "ifconfig eth0" output looks OK except for a lack of packets. The sis900 module is loaded but dmesg gives "ech0: link not ready". My intefaces file has sensible values for network, gateway, netmask and address. I tried another cable with same result so we can rule the cable out. I have another PC running 'Doze and it's OK so the router is working OK.

Does anyone have any suggestions?

Thanks in advance,

CB

---

### Post by eppoh on 2007-02-19
Try going back to kernel -10. 11 broke network for some cards

---

### Post by CrowBoy1960 on 2007-02-19
Thanks for the tip, unfortunately the previous kernel had the same problem.

Regards,
CB

---

