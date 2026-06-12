---
title: "No internet at startup until I run dhclient..."
date: 2009-08-24
forum: New to Ubuntu
---

### Post by theicyj on 2009-08-24
I am running Ubuntu 9.04 x64 with the kernel 2.6.29.  I set up a static IP address on my network interface (for a home ssh server).  All works fine, however, when I restart my computer I do not have any Internet access until I run *sudo dhclient*.  Once I run that all is fine again until the next reboot. Is there any way I can fix this so I don't have to run dhclient to access the internet?  

Some extra info:
My IPv4 settings for the network interface are:
Method: Manual
Address: 192.168.1.112
Netmask: 255.255.255.0
Gateway: 0.0.0.0
DNS Servers: (empty)
Search Domains: (empty)

I have a Linksys router running the latest version of Tomato and assigns a static dhcp IP address of 192.168.1.112 to the MAC address of the network interface.  The subnet mask on the router is set to 255.255.255.0

---

### Post by gali98 on 2009-08-24
Please give the output of 
cat /etc/network/interfaces

Kory

---

### Post by bodhi.zazen on 2009-08-24
From what you posted you did not set a gateway.

enter your router's IP address as the gateway.

---

### Post by Iowan on 2009-08-24
If you have the router set up to issue a static lease, you should be able to use DHCP (which is what **dhclient** does). In fact, **Auto eth0** should get you the same address. **dhclient** may be filling in the DNS servers, too.

BTW, is "connect automatically" checked?

---

### Post by gali98 on 2009-08-24
You'll probably want to set dns too... Most likely it will also be your router.
Kory

---

### Post by cariboo on 2009-08-24
+1 for setting the dns addresses in the IPv4 tab manually.

---

### Post by theicyj on 2009-08-24
Thanks everyone for the replies.  I set the dns manually to match that of my router as gali98 and cariboo907 suggested and all is now well!

---

