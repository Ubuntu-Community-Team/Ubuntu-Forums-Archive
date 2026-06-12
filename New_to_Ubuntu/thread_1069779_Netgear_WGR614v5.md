---
title: "Netgear WGR614v5"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-02-14
Strange, using the Check if Already Posted the Netgear WGR614v5 shows nothing. Hmmm?

I have a Netgear WGR614v5 wireless router.

I want to tinker with it. Once it's cabled to the computer all I have to do is the access the modem? Nothing to d/l for Ubuntu?

---

### Post by cerealtx on 2009-02-14
> **Mark_in_Hollywood said:**
> Strange, using the Check if Already Posted the Netgear WGR614v5 shows nothing. Hmmm?

I have a Netgear WGR614v5 wireless router.

I want to tinker with it. Once it's cabled to the computer all I have to do is the access the modem? Nothing to d/l for Ubuntu?

correct the router is completely independent of the comp
open firefox and in the address bar type in 192.168.254.254 (i think its 254.254) can't remember on netgear (go cisco)

---

### Post by superprash2003 on 2009-02-14
sometimes it may not get an ip.. in that case just type sudo dhclient eth0 in the terminal to get an ip.. presuming eth0 is the interface connected to netgear

---

### Post by cerealtx on 2009-02-14
> **superprash2003 said:**
> sometimes it may not get an ip.. in that case just type sudo dhclient eth0 in the terminal to get an ip.. presuming eth0 is the interface connected to netgear

what wont get a ip? the router? it better other wise there is no gateway and TCP/IP IPv4 Wont work...

---

### Post by superprash2003 on 2009-02-15
ubuntu machine wont get an ip!!

---

### Post by Mark_in_Hollywood on 2009-02-15
> **superprash2003 said:**
> ubuntu machine wont get an ip!!

I'm sorry to ask, but WHAT ARE YOU TALKING ABOUT?

---

### Post by cerealtx on 2009-02-15
were you able to get to the routeR?

---

### Post by superprash2003 on 2009-02-16
sometimes your ubuntu machine may not get an ip from your netgear route.r. is such cases all you need to do is use the dhclient command(given on top) to request the router to give the ubuntu machine an ip address so you could connect to your router..

---

