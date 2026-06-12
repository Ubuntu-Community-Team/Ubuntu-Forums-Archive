---
title: "Creating a bridge from ppp0 to wlan0"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by n0ts0s00l on 2008-09-23
Hello everyone!
Im trying to set up a laptop that will take a GPRS modem set up under ppp0 and act as a wireless access point on wlan0. 
Basically
GPRS Modem -> Laptop (w/ DHCP Server) -> Wireless card (In Master Mode)-> Wireless Clients

I need help setting up a DHCP server and bridging the two connections. I already have both connections set up and I can connect to sites from the laptop through PPP0 but any clients connecting cant ping or see anything.
Thanks for any help you can give,
n0ts0c00l

---

### Post by n0ts0s00l on 2008-09-24
bump :(

---

### Post by superprash2003 on 2008-09-24
you would have to club these two tutorials for this to work
1)ICS - [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
2)laptop as AP - [http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html)
  remember with laptop as AP only one pc can access the laptop's connection via wlan0 at a time.. you would be setting up a adhoc wifi network

---

