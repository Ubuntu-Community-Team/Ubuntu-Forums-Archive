---
title: "Can't change IP Address on VM"
date: 2015-12-14
forum: Networking &amp; Wireless
---

### Post by jesse43 on 2015-12-14
I'm trying to set up one interface (eth1) to have multiple IP addresses. The host has eth1 set up as a host-only connection and all I'm trying to do right now is set the IP addresses of both machines and prove that I can ping one from the other. I originally was changing /etc/networking/interfaces and adding in the IP addresses that way. Reset the with 'sudo /etc/init.d/networking restart' and no luck. Then moved on and found this [https://help.ubuntu.com/14.04/serverguide/serverguide.pdf](https://help.ubuntu.com/14.04/serverguide/serverguide.pdf). It seems that you need ethtool installed. I tried this and still no luck. On page 35 of that manual it says you can use 'sudo ifconfig eth0 10.0.0.100 netmask 255.255.255.0' to temporarily add an IP address to an interface. This doesn't even work. I have no idea where else to go with this and have scoured the net but can't find anything. Any ideas?

---

### Post by jesse43 on 2015-12-14
Also note that I tried going through the network settings GUI in Ubuntu to add the IP address. This had no effect and the IP address was still set to 192.168.56.104.

---

### Post by jesse43 on 2015-12-14
I switched to 12.04 (was in 14.04) and now it works. If someone wants to post a suggestion or if it's a known bug for future people looking into this same problem go ahead. For me, 12.04 will work.

---

