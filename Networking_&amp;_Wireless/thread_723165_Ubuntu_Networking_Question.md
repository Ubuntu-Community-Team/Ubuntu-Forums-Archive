---
title: "Ubuntu Networking Question"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by ubuntoexpert on 2008-03-13
I'm using Ubuntu 5.10.  I would like to have both my wired and wireless network interfaces load automaticly at startup, but since I am not always connected to both at the same, I need them to be able to time out realitivly quickly so the system boots faster. Right now they both are loaded at startup, but it takes about 3 minutes to load due to the wired connection not being available. I would also like to have it automaticly pick the faster of the two connections (11Mb/sec vs. 100Mb/sec) if both wireless and wired connections are present, very similar to the way Mac OS X works. I have a feeling this may be automatic and not require additional configuration, but I'm not sure. If anyone has any idea, please let me know!

---

### Post by rklauco on 2008-03-13
The slowdown is caused by DHCP probably.
The interfaces try to connect and obtain adresses and wait for the reply from DHCP server. If not received, they try again for few times.
If possible, set the IP/DNS adresses manualy and that should fix the problem - at least the time delay.

---

### Post by larry007 on 2008-03-13
You don't mention what Dhcp server you are using.  My gut feeling is that ip address delivery is poor - this could be many things.  I would urge you to set static IPs, which is really easy to do in the network manager provided in Ubuntu.  Once you are satisfied with the result, have a look at your Dhcp server.  I assign IPs to the MAC, which is really useful.  Also, you could set the expiry date to be a bit longer, say a day or two, even a week is fine at home use.

---

### Post by rklauco on 2008-03-13
I believe there's nothing wrong with DHCP - the problem is, that the user seems to be roaming between two connection types and since e.g. wireless is out of reach, but still active in networking setup, it will wait for the DHCP server reply - and it won't come, because the wireless is not there.

---

### Post by ubuntoexpert on 2008-03-13
> **rklauco said:**
> The slowdown is caused by DHCP probably.
The interfaces try to connect and obtain adresses and wait for the reply from DHCP server. If not received, they try again for few times.
If possible, set the IP/DNS adresses manualy and that should fix the problem - at least the time delay.
hi
thanks for ur replay
i will try that
Regards

---

