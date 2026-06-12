---
title: "Shorewall help"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by petdog on 2008-07-04
Hey guys,
I am trying to get shorewall to allow access only to my ssh port, i managed that, however my next issue is i want only certain machines on my network to bypass the firewall completely so they have full samba and ssh connectivity, can anyone help me with doing this?
Thanks,
PetDoG

---

### Post by sonicb00m on 2008-07-04
> 
ACCEPT net:192.168.0.0-192.168.255.255 fw tcp
ACCEPT net:192.168.0.0-192.168.255.255 fw udp
ACCEPT net fw tcp 2222
 


In the rules file you can specify the IP range for your local network and leave all ports open.

The last line leave the specified ports open for the entire internet.

---

### Post by petdog on 2008-07-06
Hey Thanks for responding, okay will try thanks hey! :D

---

### Post by petdog on 2008-07-06
Final Solution for anyone that needs to know out of interest,
please specify the top line first!!!!
ACCEPT net:192.168.0.0-192.168.255.255 all
ACCEPT net fw tcp 2222


Once again thank the man above for giving the solution!! :D

---

### Post by sonicb00m on 2008-07-07
Thanks for that. I will adjust my config accordingly since yours is optimised.

---

