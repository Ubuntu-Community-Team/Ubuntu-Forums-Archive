---
title: "error message on boot up."
date: 2017-02-22
forum: Networking &amp; Wireless
---

### Post by macstl on 2017-02-22
I got a ubuntu 14.04 laptop and a 16.04 laptop and both are doing the same error on boot up.  the only other computer is a tower with window 10.
error on bootup ubuntu:
Network service discovery disabled
:Your current network has a .local domain 
which is not recommended and incompatalle
with the AVAHI network service discovery 
the service has been disabled.

It is getting annoying and may affect some future usage 
Any help would be appreciated
Is there  a setting on the win 10 causing this since both ubuntu computers are showing same error?

---

### Post by chili555 on 2017-02-23
Please see: [http://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me](http://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me)

---

### Post by macstl on 2017-02-23
Tried all those suggestions, the only one that worked was the very last suggestion on that page.
I added google dns servers 8.8.8.8 8.8.4.4 to my interfaces file and it got rid of the message. \
Must have to do with isp changing nameservers.
Many thanks for the help!

---

