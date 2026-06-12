---
title: "Changing current iptables script to share internet"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by dimovich on 2008-01-18
Hello!

I want to share my internet connection with a PDA through WiFi. I attached the network diagram. It works perfectly if I set iptables like this:
```
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE 
```

But I would like to modify my current iptables script to allow internet connection sharing... So, how should I merge this new command into my current iptables script (provided below):

```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

echo 1 > /proc/sys/net/ipv4/ip_forward

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL

# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow SSH
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 22 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 41775:41776 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

Thanks.

---

