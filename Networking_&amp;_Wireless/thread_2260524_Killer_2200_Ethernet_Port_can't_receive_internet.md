---
title: "Killer 2200 Ethernet Port can't receive internet"
date: 2015-01-12
forum: Networking &amp; Wireless
---

### Post by freemind2 on 2015-01-12
-

---

### Post by chili555 on 2015-01-12
Your device has a driver, alx, and there is an interface, eth0. Let's consult the logs and see what's happening:```
dmesg | grep -e alx -e eth0
cat /var/log/syslog | grep -e eth0 -e etwork | tail -n25
```Thanks.

---

### Post by freemind2 on 2015-01-12
-

---

### Post by chili555 on 2015-01-12
Interesting. It sees the router, it tries for an IP address by DHCP and fails. We see nothing wrong; that is, fixable, to adjust. The driver offers no parameters we may manipulate. 

I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)

Let's see if it will connect at 100 Mb/s speeds first and then negotiate Gigabit:```
sudo ethtool eth0 -s speed 100
```Any change? Any signs of life?```
cat /var/log/syslog | grep etwork | tail -n10
```

---

### Post by freemind2 on 2015-01-13
-

---

