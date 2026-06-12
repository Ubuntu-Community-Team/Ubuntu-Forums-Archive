---
title: "NetworkManager connects but doesn't allow access"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by apriest on 2006-07-29
Hi,

I'm using NetworkManaager to connect to a Cisco VPN at my office. NetworkManager is definitely connected but I cannot ssh into anything and I don't even have internet access. As soon as I disconnect, I have full access for eveything but the VPN of course.

Any help would be greatly appreciated.

P.S. I checked with the vpn admin at my company and he verifies that I am connecting to the vpn.

---

### Post by balak on 2006-08-10
Can you post the output of your ifconfig and/or iwconfig?

I also had starting troubles with NM. However, after some tweaking the vpn works fine though there is a problem with /etc/resolv.conf

When you ssh, did you try using the full IP of the m/c you are sshing into? (rather than the name)


> **apriest said:**
> Hi,

I'm using NetworkManaager to connect to a Cisco VPN at my office. NetworkManager is definitely connected but I cannot ssh into anything and I don't even have internet access. As soon as I disconnect, I have full access for eveything but the VPN of course.

Any help would be greatly appreciated.

P.S. I checked with the vpn admin at my company and he verifies that I am connecting to the vpn.

---

### Post by theonlyandy on 2007-05-02
Hello there.

I got the same problem - I can connect to the University's VPN, but then I can't acces anything.

When I connect to the same VPN via "vpnc-connect", everything works fine.

Thanks for your help in advance.

---

