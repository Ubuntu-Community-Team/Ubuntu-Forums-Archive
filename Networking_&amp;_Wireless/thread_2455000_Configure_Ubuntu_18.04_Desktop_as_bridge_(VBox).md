---
title: "Configure Ubuntu 18.04 Desktop as bridge (VBox)"
date: 2020-12-10
forum: Networking &amp; Wireless
---

### Post by rparadam on 2020-12-10
Hi, 

[COLOR=#242729][FONT=Arial]I have the following system (upper diagram) which edge nodes send UPD dataframes to the central node, however, I want to the central node to forward them to the rest of nodes (bottom diagram). I don't know how to configure the iptables to get it.[/FONT][/COLOR]

[IMG]https://i.stack.imgur.com/SKFKq.png[/IMG]

[COLOR=#242729][FONT=Arial]I have the following chain rule but it doesn't work[/FONT][/COLOR]
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ufw-track-forward  all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  192.168.1.60         192.168.1.63         udp spt:8947 dpt:8947
[COLOR=#242729][FONT=Arial]I've doing the following at the "server" VBox:[/FONT][/COLOR]
sysctl net.ipv4.ip_forward=1

sudo iptables -t nat -A PREROUTING -p udp -d 192.168.1.60 --dport 8947 -j DNAT --to-destination 192.168.1.63:8947

sudo iptables -t nat -A POSTROUTING -j MASQUERADE

---

