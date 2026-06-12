---
title: "iptables blocking my network, help"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by Naegling23 on 2007-11-28
ok, so I have two ubuntu computers on a network with a linksys router.  One computer has iptables installed, the other does not (i removed it to confirm that iptables was the problem).  Currently I cannot access my router settings from the computer with iptables, but can with the computer without iptables (the 192.168.1.1 setup).  I also cannot connect using nfs, in fact, I cannot even ping the computers.  So how can I configure iptables to allow all intranet traffic?

---

### Post by bowens44 on 2007-11-28
> **Naegling23 said:**
> ok, so I have two ubuntu computers on a network with a linksys router.  One computer has iptables installed, the other does not (i removed it to confirm that iptables was the problem).  Currently I cannot access my router settings from the computer with iptables, but can with the computer without iptables (the 192.168.1.1 setup).  I also cannot connect using nfs, in fact, I cannot even ping the computers.  So how can I configure iptables to allow all intranet traffic?

What is the output of iptables -L (in a terminal window)

---

### Post by Naegling23 on 2007-11-28
iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
naegling23@naegling23-kubuntu:~$ sudo iptables -L
[sudo] password for naegling23:
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere
MOBLOCK_IN  0    --  anywhere             anywhere            state NEW
ACCEPT     tcp  --  dhcp17.srv.prnynj.cv.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  dhcp17.srv.prnynj.cv.net  anywhere
ACCEPT     tcp  --  dhcp16.srv.prnynj.cv.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  dhcp16.srv.prnynj.cv.net  anywhere
ACCEPT     tcp  --  dhcp18.srv.prnynj.cv.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  dhcp18.srv.prnynj.cv.net  anywhere
ACCEPT     0    --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       0    --  anywhere             255.255.255.255
DROP       0    --  anywhere             192.168.1.255
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    0    --  anywhere             anywhere
INBOUND    0    --  anywhere             192.168.1.102
INBOUND    0    --  anywhere             192.168.1.100
INBOUND    0    --  anywhere             192.168.1.255
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
MOBLOCK_FW  0    --  anywhere             anywhere            state NEW
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU
OUTBOUND   0    --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             192.168.1.0/24      state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             192.168.1.0/24      state RELATED,ESTABLISHED
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere
MOBLOCK_OUT  0    --  anywhere             anywhere            state NEW
ACCEPT     tcp  --  192.168.1.100        dhcp17.srv.prnynj.cv.net tcp dpt:domain
ACCEPT     udp  --  192.168.1.100        dhcp17.srv.prnynj.cv.net udp dpt:domain
ACCEPT     tcp  --  192.168.1.100        dhcp16.srv.prnynj.cv.net tcp dpt:domain
ACCEPT     udp  --  192.168.1.100        dhcp16.srv.prnynj.cv.net udp dpt:domain
ACCEPT     tcp  --  192.168.1.100        dhcp18.srv.prnynj.cv.net tcp dpt:domain
ACCEPT     udp  --  192.168.1.100        dhcp18.srv.prnynj.cv.net udp dpt:domain
ACCEPT     0    --  anywhere             anywhere
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
OUTBOUND   0    --  anywhere             anywhere
OUTBOUND   0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (4 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     0    --  192.168.1.101        anywhere
ACCEPT     tcp  --  192.168.1.106        anywhere            tcp dpt:netbios-dgm
ACCEPT     udp  --  192.168.1.106        anywhere            udp dpt:netbios-dgm
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:netbios-ns:netbios-ssn
ACCEPT     udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds
ACCEPT     udp  --  anywhere             anywhere            udp dpt:microsoft-ds
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:sunrpc
ACCEPT     udp  --  anywhere             anywhere            udp dpt:sunrpc
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nfs
ACCEPT     udp  --  anywhere             anywhere            udp dpt:nfs
LSI        0    --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       0    --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination

Chain OUTBOUND (3 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     0    --  anywhere             anywhere

---

