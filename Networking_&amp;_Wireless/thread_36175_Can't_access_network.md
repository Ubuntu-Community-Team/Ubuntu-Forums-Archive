---
title: "Can't access network"
date: 2005-05-22
forum: Networking &amp; Wireless
---

### Post by igor4u on 2005-05-22
It's about 3 weeks I have no access to Inet. I have only Knoppix 3.7 to get network. Strange but it founds net automatically without settings.

I have Davicom ethernet card, static Ip & ISDN cable connection, without DHCP.
But Ubuntu doesnt see my network. I tryed disable IPv6, DHCP, replace tulip but nothing worked. I dont understand, It seems to me I can receive packets but cant send. Settings OK. I cant ping gatway etc.


Please see my attachements, maybe you can get my net work.  :roll: 
 ](*,)

---

### Post by nad on 2005-05-22
You have a bad network address in your routing table. How did you set the static network parameters?

Please make sure that the network address line in the config file /etc/network/interfaces shows a valid address. Or add a network address line.

---

### Post by igor4u on 2005-05-23
No I have a right network address line in the config file /etc/network/interfaces
I verifed it and it's OK.  :neutral:

---

