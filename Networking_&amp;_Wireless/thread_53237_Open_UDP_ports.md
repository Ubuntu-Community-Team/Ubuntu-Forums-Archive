---
title: "Open UDP ports?"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by Aero-Z on 2005-07-30
I need to open UDP port for Azureus. I already did 
/sbin/iptables -I INPUT -p udp --destination-port 6900:6900 -j ACCEPT

The question is how to save the configuration?

Thanks for any reply O:)

---

### Post by bored2k on 2005-07-30
[QUOTE=Aero-Z]I need to open UDP port for Azureus. I already did 
/sbin/iptables -I INPUT -p udp --destination-port 6900:6900 -j ACCEPT

The question is how to save the configuration?

Thanks for any reply O:)[/QUOTE]
 What router do you have ? You can do this following the guide on [http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm) .

---

### Post by Aero-Z on 2005-07-30
I don't have a router. 
And sorry, this topic should be in Hedgehog 5.04

---

