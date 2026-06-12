---
title: "vpn server and internet problem"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by behzadfu on 2008-09-19
hi to all
we have a two network in two city,so they connected togheter with vpn [pptp]
vpn server in las week was working fine
since installation of iptables and csf the vpn connection not function properly
client can connect to server via pptp vpn connection and ping 172.16.0.1
but no access to internet and company website on 172.16.0.1
server cant ping clients 
I  tried meny iptables rules such as nat and forward
but no success
Can anyone help me to solve problem?

server valid ip 78.110.170.2  eth0
server invalid ip 172.16.0.1
client ip range 172.16.0.10 to 172.16.0.255  with subnet 24
vpn type :pptp on port 1723
server has one network interface (eth0)
os : centos 5 without gui


route table
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.0.10      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.16.0.0      78.110.170.149  255.255.255.0   UG    0      0        0 eth0
78.110.170.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         78.110.170.1    0.0.0.0         UG    0      0        0 eth0


```

**iptables**
```

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     udp  --  .                    anywhere            udp spts:1024:65535 dpt:domain
ACCEPT     tcp  --  .                    anywhere            tcp spts:1024:65535 dpt:domain
ACCEPT     udp  --  .                    anywhere            udp spt:domain dpts:1024:65535
ACCEPT     tcp  --  .                    anywhere            tcp spt:domain dpts:1024:65535
ACCEPT     udp  --  .                    anywhere            udp spt:domain dpt:domain
ACCEPT     udp  --  85.234.133.209       anywhere            udp spts:1024:65535 dpt:domain
ACCEPT     tcp  --  85.234.133.209       anywhere            tcp spts:1024:65535 dpt:domain
ACCEPT     udp  --  85.234.133.209       anywhere            udp spt:domain dpts:1024:65535
ACCEPT     tcp  --  85.234.133.209       anywhere            tcp spt:domain dpts:1024:65535
ACCEPT     udp  --  85.234.133.209       anywhere            udp spt:domain dpt:domain
LOCALINPUT  all  --  anywhere             anywhere
INVALID    tcp  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:telnet
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:imap
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:smtps
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:rndc
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:pop3s
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:pptp
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:cbt
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:interwise
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:24814
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:infowave
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:ftp-data
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:ftp
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:domain
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:rndc
ACCEPT     icmp --  anywhere             anywhere            limit: avg 8/sec burst 5
LOGDROPIN  all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             .                   udp spt:domain dpts:1024:65535
ACCEPT     tcp  --  anywhere             .                   tcp spt:domain dpts:1024:65535
ACCEPT     udp  --  anywhere             .                   udp spts:1024:65535 dpt:domain
ACCEPT     tcp  --  anywhere             .                   tcp spts:1024:65535 dpt:domain
ACCEPT     tcp  --  anywhere             .                   tcp spt:domain dpt:domain
ACCEPT     udp  --  anywhere             85.234.133.209      udp spt:domain dpts:1024:65535
ACCEPT     tcp  --  anywhere             85.234.133.209      tcp spt:domain dpts:1024:65535
ACCEPT     udp  --  anywhere             85.234.133.209      udp spts:1024:65535 dpt:domain
ACCEPT     tcp  --  anywhere             85.234.133.209      tcp spts:1024:65535 dpt:domain
ACCEPT     tcp  --  anywhere             85.234.133.209      tcp spt:domain dpt:domain
LOCALOUTPUT  all  --  anywhere             anywhere
INVALID    tcp  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:auth
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:rndc
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:pptp
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:infowave
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:distinct
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:ftp-data
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:ftp
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:domain
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:auth
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:ntp
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:rndc
ACCEPT     icmp --  anywhere             anywhere            limit: avg 8/sec burst 5
LOGDROPOUT  all  --  anywhere             anywhere

Chain INVALID (2 references)
target     prot opt source               destination
INVDROP    all  --  anywhere             anywhere            state INVALID
INVDROP    tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE
INVDROP    tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG
INVDROP    tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN
INVDROP    tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST
INVDROP    tcp  --  anywhere             anywhere            tcp flags:FIN,RST/FIN,RST
INVDROP    tcp  --  anywhere             anywhere            tcp flags:FIN,ACK/FIN
INVDROP    tcp  --  anywhere             anywhere            tcp flags:PSH,ACK/PSH
INVDROP    tcp  --  anywhere             anywhere            tcp flags:ACK,URG/URG
INVDROP    tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW

Chain INVDROP (10 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere

Chain LOCALINPUT (1 references)
target     prot opt source               destination
ACCEPT     all  --  217.219.140.89       anywhere

Chain LOCALOUTPUT (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             217.219.140.89

Chain LOGDROPIN (1 references)
target     prot opt source               destination
DROP       tcp  --  anywhere             anywhere            tcp dpt:bootps
DROP       udp  --  anywhere             anywhere            udp dpt:bootps
DROP       tcp  --  anywhere             anywhere            tcp dpt:bootpc
DROP       udp  --  anywhere             anywhere            udp dpt:bootpc
DROP       tcp  --  anywhere             anywhere            tcp dpt:sunrpc
DROP       udp  --  anywhere             anywhere            udp dpt:sunrpc
DROP       tcp  --  anywhere             anywhere            tcp dpt:auth
DROP       udp  --  anywhere             anywhere            udp dpt:auth
DROP       tcp  --  anywhere             anywhere            tcp dpts:epmap:netbios-ssn
DROP       udp  --  anywhere             anywhere            udp dpts:epmap:netbios-ssn
DROP       tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds
DROP       udp  --  anywhere             anywhere            udp dpt:microsoft-ds
DROP       tcp  --  anywhere             anywhere            tcp dpt:login
DROP       udp  --  anywhere             anywhere            udp dpt:who
DROP       tcp  --  anywhere             anywhere            tcp dpt:efs
DROP       udp  --  anywhere             anywhere            udp dpt:router
LOG        tcp  --  anywhere             anywhere            limit: avg 30/min burst 5 LOG level warning prefix `Firewall: *TCP_IN Blocked* '
LOG        udp  --  anywhere             anywhere            limit: avg 30/min burst 5 LOG level warning prefix `Firewall: *UDP_IN Blocked* '
LOG        icmp --  anywhere             anywhere            limit: avg 30/min burst 5 LOG level warning prefix `Firewall: *ICMP_IN Blocked* '
DROP       all  --  anywhere             anywhere

Chain LOGDROPOUT (1 references)
target     prot opt source               destination
LOG        tcp  --  anywhere             anywhere            limit: avg 30/min burst 5 LOG level warning prefix `Firewall: *TCP_OUT Blocked* '
LOG        udp  --  anywhere             anywhere            limit: avg 30/min burst 5 LOG level warning prefix `Firewall: *UDP_OUT Blocked* '
LOG        icmp --  anywhere             anywhere            limit: avg 30/min burst 5 LOG level warning prefix `Firewall: *ICMP_OUT Blocked* '
DROP       all  --  anywhere             anywhere


```


thanks

---

