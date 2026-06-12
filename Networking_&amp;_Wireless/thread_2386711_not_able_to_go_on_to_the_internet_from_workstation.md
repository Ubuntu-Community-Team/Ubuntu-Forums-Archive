---
title: "not able to go on to the internet from workstation"
date: 2018-03-09
forum: Networking &amp; Wireless
---

### Post by delfiler on 2018-03-09
now i am building a firewall with iptables and my code/script is built as followed:
```
IPTABLES="/sbin/iptables"echo "-   Flush momentele in- & output"
$IPTABLES -F
$IPTABLES -F INPUT
$IPTABLES -F OUTPUT
$IPTABLES --delete-chain

echo "-   Flush nat"
$IPTABLES -F -t nat

echo "-   Loading of Modules"
/sbin/depmod -a
/sbin/modprobe ipt_LOG
/sbin/modprobe ipt_MASQUERADE
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe ip_nat_irc
/sbin/modprobe ipt_state
/sbin/modprobe iptable_nat
#/sbin/modprobe ipt_MIRROR
#/sbin/modprobe ip_queue
/sbin/modprobe nfnetlink_queue
/sbin/modprobe ipt_REDIRECT
/sbin/modprobe ipt_TCPMSS
/sbin/modprobe ipt_length
/sbin/modprobe ipt_mark
/sbin/modprobe ipt_MARK
#/sbin/modprobe ip_conntrack_sip
#/sbin/modprobe ip_nat_sip
#/sbin/modprobe ipt_ipp2p
echo "-   Modules loaded"

echo "-   allow ONLY ping to the outside"
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT
$IPTABLES -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT
$IPTABLES -A FORWARD -p icmp --icmp-type echo-reply -j ACCEPT

echo "-   allow loopback"
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT
$IPTABLES -A INPUT -i lo -p all -j ACCEPT

echo "-   Input van bekende machines toestaan"
$IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

echo "-   Forward to networkadress"
$IPTABLES -t nat -A POSTROUTING -s 10.10.10.50 -o eth2 -j SNAT --to 192.168.1.142
$IPTABLES -t nat -A POSTROUTING -s 10.10.10.50 -o eth1 -j SNAT --to 192.168.1.142
**$IPTABLES -A FORWARD -i eth1 -j ACCEPT**
$IPTABLES -t nat -A PREROUTING -i eth1 -p tcp -m multiport --dports 80 -d 192.168.1.142 -j DNAT --to 10.10.10.50:8000
$IPTABLES -t nat -A PREROUTING -i eth1 -p tcp -m multiport --dports 3389 -d 192.168.1.142 -j DNAT --to 10.10.10.50

#echo "-   Drop ICMP"
#$IPTABLES -A INPUT -p icmp --icmp-type any -j ACCEPT
#$IPTABLES -A OUTPUT -p icmp -j ACCEPT
echo "-   Toestaan ssh van bepaadlde IP'S"
$IPTABLES -A INPUT -i eth1 -p tcp -s 192.168.1.105 --dport 220 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPTABLES -A OUTPUT -o eth1 -p tcp --sport 220 -m state --state ESTABLISHED -j ACCEPT

echo "-   Open poorts"
$IPTABLES -A INPUT -p tcp -m tcp --dport 20 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -p udp -m udp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -p udp -m udp --dport 69 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -p udp -m udp --dport 123 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 3389 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 8000 -j ACCEPT
$IPTABLES -A INPUT -p udp -m udp --dport 8000 -j ACCEPT

echo "-   DHCP open for eth2"
$IPTABLES -A INPUT -p udp -i eth2 -m multiport --dports 67,68 -j ACCEPT
$IPTABLES -A OUTPUT -p udp -o eth2 -m multiport --dports 67,68 -j ACCEPT

echo "-   closed poorts"
$IPTABLES -A INPUT -p udp -m udp --dport 67 -j DROP
$IPTABLES -A INPUT -p udp -m udp --dport 68 -j DROP
$IPTABLES -A OUTPUT -p udp -m udp --dport 67 -j DROP
$IPTABLES -A OUTPUT -p udp -m udp --dport 68 -j DROP

echo "-   closed poorts checker"
$IPTABLES -A INPUT -j DROP

#echo "-   Drop eth1"
#$IPTABLES -A INPUT -i eth1 -j DROP

echo "-   Default policies builder"
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT

echo "-   everything loaded"
```
now i know this is a VERY basic-ish script, but it works. the problem i am having (and can't figure out) is how i can let get DNS working for eth2 as that is my LAN and my eth1 is my internet acces

edit: added a line that being the one that is set in bold

edit2: found out what was long by looking around for solutions apparently the gateway it picked wasn't the one for the web but to the LAN

edit3: well after a reboot it is back to the wrong setting so now my problem has changed from being not being able to get on the internet to keeping a setting stuck i do the following to fix the problem:
```
route del default gw 192.168.1.1
route add default gw 192.168.1.1 
```
so yeah how do i keep the changes?

edit4: found out that thanks to a line in nano etc/network/interfaces my wan was lan was selected and everything is solved now

---

### Post by slickymaster on 2018-03-09
Thread moved to **Networking & Wireless** for a better fit

---

