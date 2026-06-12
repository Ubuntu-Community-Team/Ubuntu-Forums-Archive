---
title: "LTSP on Ubuntu 16.04 MAC authentication"
date: 2016-12-08
forum: Networking &amp; Wireless
---

### Post by endi0011 on 2016-12-08
hy,

i setup Ubuntu ltsp following this tutorials
[https://ubuntuforums.org/showthread.php?t=2173749](https://ubuntuforums.org/showthread.php?t=2173749)
[https://ubuntuforums.org/showthread.php?t=2177959](https://ubuntuforums.org/showthread.php?t=2177959)

everithyng is fine i also wrote iptables script to mount filesystem 

```
#!/bin/bash

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

iptables -I INPUT -p tcp -m tcp -m multiport --sports 80,443 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -p tcp -m tcp -m multiport --dports 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -I INPUT -p udp -m udp --sport 53 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -p udp -m udp --dport 53 -m state --state NEW -j ACCEPT

iptables -A INPUT -p tcp --match multiport --sports 30000:56000 -j ACCEPT
iptables -A OUTPUT -p tcp --match multiport --dports 30000:56000 -j ACCEPT

iptables -A INPUT -p udp --match multiport --sports 2070:2076 -j ACCEPT
iptables -A OUTPUT -p udp --match multiport --dports 2070:2076 -j ACCEPT

iptables -A INPUT -p udp --match multiport --sports 49152:56000 -j ACCEPT
iptables -A OUTPUT -p udp --match multiport --dports 49152:56000 -j ACCEPT

iptables -I INPUT -p udp -m udp -m multiport --sports 2049,10809,69,68,67,8099,138,137 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
iptables -I OUTPUT -p udp -m udp -m multiport --dports 2049,10809,69,68,67,8099,138,137 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT


iptables -A INPUT -j LOG
iptables -A OUTPUT -j LOG

```


my problem is i specifay mac address for user this way

```
[00:5d:09:22:10:1e]
LDM_GUESTLOGIN = True
LDM_USERNAME = lab01
LDM_PASSWORD = mypassword

```

but i still can connect from another pc with different mac with this acount. Is something different in 16.04. 

i know that lts.conf get executed beacouse i disable ssh and put LDM_DIRECTX = True in lts.conf, and you can see in iptables ssh port is not allowed. 

or is there another metod to allow user by mac address.

Thanks and prichiated

---

