---
title: "Connect to Wireless AND wired LAN at same time??"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by marko_4454 on 2007-04-18
I have this problem:
I have a MASSIVE storage device...its called ReadyNAS. The link provided below:

[ReadyNAS NV]("http://www.infrant.com/products/products_details.php?name=ReadyNAS%20NV")

The problem is that this connects to my computer using my only NIC. I connect to the internet using a wireless network interface. Everything is fine with the internet until I connect the ethernet cable in my NIC. 
I think this is because of priority or something, but when I connect my ethernet cable to NIC, I lose internet. The computer thinks that there is internet coming from my ReadyNAS (which of course isnt) and drops the wireless connection I have with the wireless router.

Is there something I can do to avoid this? Any suggestions?
Please help, I need to solve this!

---

### Post by marko_4454 on 2007-04-19
please someone? anyone? any suggestion even?

---

### Post by spd106 on 2007-04-19
Set the wired interface to static. This will entail editing the /etc/network/interfaces file.

---

### Post by marko_4454 on 2007-04-19
OK, if anyone else has this kind of problem this is what I found to be my solution:
1) I told my wireless router to give out (using DHCP) IP's with the range 10.0.0.*
2) I set my ReadyNAS to get a static IP of 192.168.1.*

So since they are in different networks, they are able to connect without interfering with each other. The problem here is that since they are in different networks, other computers that get IP from router (wirelessly) will have a hard time connecting to the ReadyNAS. Thats a minor problem that can be easily fixed though :)
I am happy with the result.
Thank you spd106!!

---

