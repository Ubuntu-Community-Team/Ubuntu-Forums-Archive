---
title: "TC traffic control problems with Hardy"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by waltervalderrama on 2008-11-19
Hello guys. I have a problem running TC in Hardy. I have a script implemmented in 2 other PCs running Gutsy, and never had a problem.

The script is as follows, is the same in the other 2 PCs.

#!/bin/bash
iptables -t mangle -A FORWARD -i eth0 -s 0/0 -j MARK --set-mark 2
iptables -t mangle -A FORWARD -i ath0 -s 0/0 -j MARK --set-mark 2
iptables -t mangle -A FORWARD -i ath0 -s 10.10.10.2/32 -j MARK --set-mark 1
iptables -t mangle -A INPUT -i ath0 -p tcp --dport 20 -j MARK --set-mark 3
iptables -t mangle -A INPUT -i ath0 -p tcp --dport 21 -j MARK --set-mark 3
iptables -t mangle -A INPUT -i ath0 -p tcp --sport 20 -j MARK --set-mark 3
iptables -t mangle -A INPUT -i ath0 -p tcp --sport 21 -j MARK --set-mark 3

# Se elimina toda regla previa de tc
tc qdisc del dev ath0 root 2>&1 >/dev/null

# Reglas TC con clases absolutas
tc qdisc add dev ath0 handle ffff: ingress
tc filter add dev ath0 parent ffff: protocol ip prio 4 handle 1 fw flowid 4:1 
tc filter add dev ath0 parent ffff: protocol ip prio 5 handle 1 fw flowid 4:2 
tc filter add dev ath0 parent ffff: protocol ip prio 6 handle 1 fw flowid 4:3
tc filter add dev ath0 parent ffff: protocol ip prio 6 handle 2 fw flowid 4:4
tc filter add dev ath0 parent ffff: protocol ip prio 7 handle 3 fw police rate 20kbit burst 10k drop flowid 4:5

# Reglas TC con clases y velocidades de transmision

tc qdisc add dev ath0 handle ffff: ingress
tc filter add dev ath0 parent ffff: protocol ip prio 4 handle 1 fw police rate 1500kbit burst 90k continue flowid 4:1
tc filter add dev ath0 parent ffff: protocol ip prio 5 handle 1 fw police rate 1500kbit burst 90k continue flowid 4:2
tc filter add dev ath0 parent ffff: protocol ip prio 6 handle 1 fw police rate 1000kbit burst 60k drop flowid 4:3
tc filter add dev ath0 parent ffff: protocol ip prio 6 handle 2 fw police rate 1000kbit burst 60k drop flowid 4:4
tc filter add dev ath0 parent ffff: protocol ip prio 7 handle 3 fw police rate 20kbit burst 10k drop flowid 4:5


And these are the errors

RTNETLINK answers: No such file or directory
RTNETLINK answers: File exists
RTNETLINK answers: File exists
We have an error talking to the kernel
RTNETLINK answers: File exists
We have an error talking to the kernel
RTNETLINK answers: File exists
We have an error talking to the kernel
RTNETLINK answers: File exists
We have an error talking to the kernel
RTNETLINK answers: File exists
We have an error talking to the kernel


Any help please :(

---

