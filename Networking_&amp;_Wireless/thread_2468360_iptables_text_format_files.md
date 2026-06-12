---
title: "iptables text format files ?"
date: 2021-10-26
forum: Networking &amp; Wireless
---

### Post by evinrude on 2021-10-26
On Ubuntu 20.04/KDE Neon are the iptables kept in text format any where ? All I can find are /etc/alternatives/iptables which is not in text format and cannot be used as input to iptables-restore .

---

### Post by The Cog on 2021-10-26
iptables is the command for configuring the firewall, not a configuration of itself.
iptables configuration files can be created by using iptables-save and writing the output to a file somewhere (but I guess you know that one).

Different firewall configuration utilities store there configuration in different places, but usually somewhere in /etc.
/etc/iptables is a good place to try on Ubuntu
/etc/sysconfig/iftables is a good place to look on Red Hat.
Sorry, I can't be specific about the Ubuntu location because I don't use iptables.

---

### Post by uafmaewo on 2021-11-02
Try this:
sudo apt update && sudo apt install iptables-persistent
Answer yes to save and then edit the files in: /etc/iptables/

```
Sample rules.v6:
*raw
:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
COMMIT
*mangle
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
COMMIT
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:AllowICMPs - [0:0]
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -s ::1/128 -i lo -j ACCEPT
-A INPUT -s fe80::/10 -p ipv6-icmp -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP
-A INPUT -p ipv6-icmp -m limit --limit 360/min -j AllowICMPs
-A INPUT -m conntrack --ctstate INVALID -j DROP
-A INPUT -m conntrack --ctstate NEW -j DROP
-A OUTPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -d ::1/128 -o lo -j ACCEPT
-A OUTPUT -d fe80::/10 -p ipv6-icmp -j ACCEPT
-A OUTPUT -p ipv6-icmp -j AllowICMPs
-A OUTPUT -m conntrack --ctstate NEW -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 1 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 2 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 3 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 4 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 128 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 129 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 130 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 131 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 132 -j ACCEPT
-A AllowICMPs -p ipv6-icmp -m icmp6 --icmpv6-type 143 -j ACCEPT
COMMIT
```

---

