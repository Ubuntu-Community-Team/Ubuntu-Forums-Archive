---
title: "Coova Chilli Trouble"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by emufambirwi on 2008-10-28
I have installed the desktop version of ubuntu 8.04 LTS with the intention of using coova-chilli. I installed coova chilli according to the guide at [https://help.ubuntu.com/community/WifiDocs/CoovaChilli]("https://help.ubuntu.com/community/WifiDocs/CoovaChilli"). The DHCP in coova chilli works fine but if I try to ping the clients assigned IP addresses by the same dhcp, I get no replies, only timeouts. 

I suspect that my routing is not ok. Is there a guide on routing or NATing for coova-chilli?

Thanks in advance

---

### Post by j.bunce on 2008-10-28
Have you entered ```
echo 1 > /proc/sys/net/ipv4/ip_forward
```?

---

### Post by emufambirwi on 2008-10-29
> **j.bunce said:**
> Have you entered ```
echo 1 > /proc/sys/net/ipv4/ip_forward
```?

Yes I did enter that code

---

