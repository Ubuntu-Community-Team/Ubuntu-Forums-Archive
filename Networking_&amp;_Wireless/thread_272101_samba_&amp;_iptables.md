---
title: "samba &amp; iptables"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by rigor on 2006-10-05
Hi...after some experiments with guardog, now i try to configure my iptables script.

```

        $IPTABLES -A INPUT -p  tcp -i $IFEXT -m state -s 0/0 --state ESTABLISHED,RELATED -j ACCEPT
        $IPTABLES -A INPUT -p icmp -i $IFEXT -m state -s 0/0 --state ESTABLISHED,RELATED -j ACCEPT
        $IPTABLES -A INPUT -p  udp -i $IFEXT -m state -s 0/0 --state ESTABLISHED,RELATED -j ACCEPT
	
	$IPTABLES -A INPUT -p udp -s 192.168.0.0/24 --dport 137:138 -j ACCEPT
	$IPTABLES -A INPUT -p udp --dport 137:138 -j DROP
	$IPTABLES -A INPUT -p tcp -s 192.168.0.0/24 --dport 139 -j ACCEPT
	$IPTABLES -A INPUT -p tcp -s 192.168.0.0/24 --dport 445 -j ACCEPT
	$IPTABLES -A INPUT -p tcp -m multiport --dports 139,445 -j DROP

```

When ubuntu is on, the other winxp PCs, access to samba network, whereas ubuntu no.
Then i stop firewall, and the network is ok on ubuntu too.
At the end, if i restart the firewall script, the samba network goes.

Please, can you help me?

---

### Post by crokett on 2006-10-05
You need to add a rule to allow incoming connections for NetBIOS.  On my system it is port 4873.    

Also suggested you install a program called Firestarter.  It is GUI front-end to iptables

---

