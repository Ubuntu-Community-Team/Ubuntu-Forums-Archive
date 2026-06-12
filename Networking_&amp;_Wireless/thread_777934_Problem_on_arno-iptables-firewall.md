---
title: "Problem on arno-iptables-firewall"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by kelvinjb on 2008-05-01
Hello, 
i setup a router as below
 
1) System: ubuntu 7.10-server edition
2) DHCP3-server
3) Arno-iptables-firewall from apt-get install and configure the config file, using ppp0
4) with 3 NICs (internet=eth1, eth0=192.168.1.1, eth2=192.168.2.1)
 
Everything is working great but i have 2 problems that need helps
1) can I configure the 2 internal NIC to serve only 192.168.1.x (both eth0 and eth2 using 192.168.1.1) instead of having 2 network 192.168.1.X and 192.168.2.x? How?
 
2) Not able to access my server connected and portforwarded from this router by using my.server.com from LAN. i googgle and read through many many posts for the last whole weeks and understand that this problem is inhirent with iptables scripts and one of the solutions is adding the rule below:
 
$IPTABLES -t nat -A PREROUTING -i $INT_IF -d $EXT_IP -j DNAT --to-destination $SERVER_IP
 
This works with one SERVER_IP but i have 2 servers running different task. it does not work if i add both rules below:
 
$IPTABLES -t nat -A PREROUTING -i $INT_IF -d $EXT_IP -j DNAT --to-destination $[COLOR="Red"]SERVER_IP1[/COLOR]
$IPTABLES -t nat -A PREROUTING -i $INT_IF -d $EXT_IP -j DNAT --to-destination $[COLOR="blue"]SERVER_IP2[/COLOR]
 
I need my servers to be accessible from LAN with public (my.server.com) from the LAN and without conflicting arno-iptables-firewall ruleset. 
 
Is there anywhere to fix this? 
 
THanks for your time looking into this.......Kelvin

---

