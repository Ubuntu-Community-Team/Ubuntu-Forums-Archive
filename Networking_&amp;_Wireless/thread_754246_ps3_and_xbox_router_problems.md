---
title: "ps3 and xbox router problems"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by z662 on 2008-04-13
Hello, I recently set up a router running Ubuntu 7.10 server edition as my gateway.  I have a few issues that i have been unable to resolve though.  The first issue is that anytime i try to get on xbox live, i must test the connection from the xbox360 dashboard before it will connect to the internet...2nd, the ps3 will not connect at all and complains of a failed dns.  however, i provided the same two ip addresses for the ps3 as are specified in my resolv.conf file on my router.  Lastly, i am unable to forward ports for my webserver...here is my iptables script and my ip masquerading script....I hope someone can help


#eth0 = lan
#eth1 = wan
   1 #!/bin/bash
 sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
 sudo iptables -A FORWARD -s 24.144.129.1/1 -o eth1 -j ACCEPT
 sudo iptables -A FORWARD -d 192.168.0.0/24 -m state --state ESTABLISHED,RELATED -i eth1 -j ACCEPT
 sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.0.101:80
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 80 -m state --state NEW -j ACCEPT


##################################
#!/bin/bash
      2 FWVER= 0.76
      3 
      4 echo -e "\n\n\Loading simple rc.firewall-iptables version $FWVER..\n"
      5 
      6 IPTABLES=/sbin/iptables
      7 DEPMOD=/sbin/depmod
      8 MODPROBE=/sbin/modprobe
      9 
     10 EXTIF="eth0"
     11 INTIF="eth1"
     12 
     13 echo "  External Interface:  $EXTIF"
     14 echo "  Internal Interface:  $INTIF"
     15 
     16 EXTIP="24.144.129.48"
     17 echo "  External IP:  $EXTIP"
     18 
     19 echo -en "  loading modules: "
     20 
     21 $DEPMOD -a
     22 
     23 echo ".........................................."
 echo -en "ip_tables, "
     25 $MODPROBE ip_tables
     26 echo -en "ip_conntrack, "
     27 $MODPROBE ip_conntrack
     28 
     29 echo -en "ip_conntrack_ftp, "
     30 $MODPROBE ip_conntrack_ftp
     31 
     32 echo -en "ip_conntrack_irc, "
     33 $MODPROBE iptable_nat
     34 
     35 echo -en "ip_nat_ftp, "
     36 $MODPROBE ip_nat_ftp
     37 
     38 echo ".........................................."
     39 echo -e "  Done loading modules.\n"
     40 
     41 echo "  Enable forwarding..."
     42 echo "1" > /proc/sys/net/ipv4/ip_forward
     43 
     44 echo "  Enabling DynamicAddr..."
     45 echo "1" > /proc/sys/net/ipv4/ip_dynaddr
echo "  Clearing any existing rules and setting default policy..."
     48 $IPTABLES -P INPUT ACCEPT
     49 $IPTABLES -F INPUT
     50 $IPTABLES -P OUTPUT ACCEPT
     51 $IPTABLES -F OUTPUT
     52 $IPTABLES -P FORWARD DROP
     53 $IPTABLES -F FORWARD
     54 $IPTABLES -t nat -F
     55 
     56 echo "  FWD:  Allow all connections out and only existing and related on
        es in"
     57 $IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RE
        LATED -j ACCEPT
     58 $IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
     59 $IPTABLES -A FORWARD -j LOG
     60 $IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
     61 
     62 echo "  Enabling SNAT (MASQUERADE) functionality on $EXTIF"
     63 $IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
     64 
     65 echo -e "\nrc.firewall-iptables v$FWVER done.\n"

---

### Post by update_manager on 2008-04-13
> 
#eth0 = lan
#eth1 = wan
   1 #!/bin/bash
 sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
 sudo iptables -A FORWARD -s 24.144.129.1/1 -o eth1 -j ACCEPT
 sudo iptables -A FORWARD -d 192.168.0.0/24 -m state --state ESTABLISHED,RELATED -i eth1 -j ACCEPT
 sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.0.101:80
sudo iptables -A FORWARD -d 192.168.0.101 -i eth0 -p tcp --dport 80 -m state --state NEW -j ACCEPT


Try 
iptables -A FORWARD -i WAN_port -p tcp --dport 80 -m state --state NEW -j ACCEPT
iptables -t nat -A PREROUTING -i WAN_port -p tcp --dport 80 -j DNAT --to 192.168.0.101


to get your webserver reachable.

---

### Post by z662 on 2008-04-13
do those 2 lines replace any previous lines, or are they in addition to the others?


thanks

---

