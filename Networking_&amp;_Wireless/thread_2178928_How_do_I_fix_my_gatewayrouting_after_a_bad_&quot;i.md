---
title: "How do I fix my gateway/routing after a bad &quot;ip route&quot;?"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by gschoppe on 2013-10-05
I took some advice on how to route traffic by port, using iptables, and I messed up my internet connection.  The full script that I ran was:

```

#!/bin/bash
#ROUTE CERTAIN PORTS THROUGH NON-VPN, BLOCK ALL OTHERS
#get IP address
IP=$(wget https://duckduckgo.com/?q=whats+my+ip -q -O - | grep -Eo '\<[[:digit:]]{1,3}(\.[[:digit:]]{1,3}){3}\>')
#flush iptables
iptables -F
#set drop all policies
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
#allow all tunneled connections
iptables -A INPUT  -i tun+ -j ACCEPT
iptables -A OUTPUT -o tun+ -j ACCEPT
#allow all localhost connections
iptables -A INPUT  -s 127.0.0.0/24 -j ACCEPT
iptables -A OUTPUT -d 127.0.0.0/24 -j ACCEPT
#allow connections to VPN gateway
iptables -A INPUT  -s $IP -j ACCEPT
iptables -A OUTPUT -d $IP -j ACCEPT
#allow all local network
iptables -A INPUT  -s 192.168.0.0/16 -j ACCEPT
iptables -A OUTPUT -d 192.168.0.0/16 -j ACCEPT
# set default gateway for table nonvpn and identify with a mark
ip route add default via 192.168.1.1 dev eth0 table nonvpn
ip rule add fwmark 0x1 table nonvpn
# Mark these packets so that iproute can route them through nonvpn and rewrite source address
# -FTP
iptables -A INPUT  -p tcp --dport 21 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 21 -j ACCEPT
iptables -A OUTPUT -t mangle -o tun0 -p tcp --dport 21 -j MARK --set-mark 1
iptables -A POSTROUTING -t nat -o eth0 -p tcp --dport 21 -j SNAT --to 192.168.1.100
# -Qbittorrent admin
iptables -A INPUT  -p tcp --dport 6886 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 6886 -j ACCEPT
iptables -A OUTPUT -t mangle -o tun0 -p tcp --dport 6886 -j MARK --set-mark 1
iptables -A POSTROUTING -t nat -o eth0 -p tcp --dport 6886 -j SNAT --to 192.168.1.100
# -Subsonic
iptables -A INPUT  -p tcp --dport 4040 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 4040 -j ACCEPT
iptables -A OUTPUT -t mangle -o tun0 -p tcp --dport 4040 -j MARK --set-mark 1
iptables -A POSTROUTING -t nat -o eth0 -p tcp --dport 4040 -j SNAT --to 192.168.1.100
# -Plex TCP
iptables -A INPUT  -p tcp --dport 32400 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 32400 -j ACCEPT
iptables -A OUTPUT -t mangle -o tun0 -p tcp --dport 32400 -j MARK --set-mark 1
iptables -A POSTROUTING -t nat -o eth0 -p tcp --dport 32400 -j SNAT --to 192.168.1.100
# -Plex UDP
iptables -A INPUT  -p udp --dport 32400 -j ACCEPT
iptables -A OUTPUT -p udp --dport 32400 -j ACCEPT
iptables -A OUTPUT -t mangle -o tun0 -p udp --dport 32400 -j MARK --set-mark 1
iptables -A POSTROUTING -t nat -o eth0 -p udp --dport 32400 -j SNAT --to 192.168.1.100

```

It never worked properly as a VPN Killswitch, so I disconnected my VPN to troubleshoot, ran "sudo iptables -F" and set all 3 policies to "ACCEPT"

now, I can access local devices, but cannot access the outside internet.

The only commands I can imagine causing this are:
```

ip route add default via 192.168.1.1 dev eth0 table nonvpn
ip rule add fwmark 0x1 table nonvpn

```

How do I troubleshoot and fix this?

---

### Post by tnt533 on 2014-07-26
Sounds like you need to do a complete reset of the firewall, backup the default config for easy restore and start fresh with a script or manually inputted set of rules that you understand 100% before running. Look [here]("http://www.cyberciti.biz/faq/ubuntu-start-stop-iptables-service/") for a quick tutorial on how to flush the rules, back up the firewall, etc... It's tempting to run a script that people claim will solve your issues but every system is different and not all systems will be able to run a script with the same results.

---

### Post by Bashing-om on 2014-07-26
Well said tnt533; +10 .

[INDENT][INDENT]but it is a process in learning
[/INDENT][/INDENT]

---

