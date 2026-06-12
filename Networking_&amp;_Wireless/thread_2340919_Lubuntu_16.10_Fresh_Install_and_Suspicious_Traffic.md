---
title: "Lubuntu 16.10 Fresh Install and Suspicious Traffic"
date: 2016-10-23
forum: Networking &amp; Wireless
---

### Post by buntuluxx on 2016-10-23
Hi!

Yesterday I installed Lubuntu 16.04 to my HDD and discovered  some very strange traffic both incoming and outgoing from the ntp port,  listed under 123/udp. 

After researching the connecting IPs I found out that most of them correspond to local software businesses and IT firms.

I  checked the traffic with iftop, which showed that multiple bytes, in  some cases even +1KB, was sent and received to and from those IPs.

Screenshot: [https://s12.postimg.org/w647skop9/screen.png](https://s12.postimg.org/w647skop9/screen.png)


.)Do I have to be worried, that those services transmitted malware or other harmful code?

.)How can I permanently block those connections or port?

I have tried using the following, unsuccessfully.

-->with the built in firewall
```
sudo ufw deny 123/udp
```
```
sudo ufw deny ntp
```

-->with iptables
```
sudo iptables -A OUTPUT -p udp --dport 123 -j DROP

```

```
sudo iptables -A INPUT -p udp --sport 123 -j DROP

```

Thank you!

---

### Post by TheFu on 2016-10-24
Local IT and SW companies are probably in the NTP volunteer pools.  They are likely providing NTP services for your area.  Blocking them will lead to less accurate time on the system, if that is true.

Check the /etc/ntpd.conf file for which servers are being used and see if those map to the "suspicious IPs".  Running **ntpq -p** might help too.

---

