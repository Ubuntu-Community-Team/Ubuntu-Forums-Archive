---
title: "wireless issues with desktop computer"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by nikdemon on 2011-04-20
hello i am very new to all of this i saw ubuntu and its stability and i liked it so i decided to install it to one of my computers tho the issue here is i am receiving wifi from my friend next door via wireless dongle i have it connected via usb to the computer with ubuntu and then i had it bridge the connection to a router etc...the issue is i believe i have the wireless driver working it shows networks and such but i cant really connect to them i had it connected to the network i wanted it to it said signal strength 56% etc...but i tried to go on the web and it just wont work can someone help getting it bridged is a matter that i will tackle after i get the internet working

---

### Post by spikoley on 2011-04-21
When you are connected try to ping and check to see if you are receiving an IP address.

1.  Applications
2.  Accessories
3.  Terminal

Check for an IP address
```
ifconfig
```
Ping the router - replace with your router's IP
```
ping 192.168.1.1
```
Ping something on the internet
```
ping ubuntuforums.org
```
or by IP
```
ping 91.189.94.12
```

Let us know what you get.

---

