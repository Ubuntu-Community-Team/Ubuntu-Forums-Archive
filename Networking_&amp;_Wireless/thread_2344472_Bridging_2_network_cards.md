---
title: "Bridging 2 network cards"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by wp.rauchholz on 2016-11-25
Hi trying to setup my linux server and getting stuck right atthe beginning (newbie...)
My server has two ethernet cards:
eth0: External Network Device
eth 1: Internal Network Device

Need to configure a bridge so that the server is configured with as a gateway device.  Any packet of information that will not be delivered locally to eth1, will be transferred to eth0.

Who can point me to a good tutorial how to set them up correctly and especially how to bridge them?

Thanks, Wolfgang

---

### Post by Doug S on 2016-11-27
If I understand correctly, you want your server to also be a router. It isn't really called "Bridging". You will need an iptables rule set to implement Network Address Translation (NAT) between your LAN (Local Area Network) and the external WAN (Wide Area Network). You can, and should, also implement firewall functionality in the same iptables rule set. Most basically, you need:```
# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
# iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
```And you need to enable packet forwarding, either:```
# echo "1" > /proc/sys/net/ipv4/ip_forward
```or edit /etc/sysctl.conf and uncomment this:```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

```You will need to expand from there, for example you can find my iptables rule set at (note: my rule set is excessively complicated for where you are at the moment, it is just an example of what can be done):
double u double u double u dot smythies dot com /~doug/network/iptables_notes/doug_firewall.current.txt

---

