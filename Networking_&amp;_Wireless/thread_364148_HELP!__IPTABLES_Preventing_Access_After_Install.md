---
title: "HELP!  IPTABLES Preventing Access After Install"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by bsahm on 2007-02-17
Hello,

After a fresh install of Ubuntu 6.10 I am unable to access Ubuntu from my router or other XP box.  What I found was that if I flush iptables, I am able to access it just fine from both router and XP.  However, flushing iptables seems a security risk.  Does anyone have an idea why?  I have included my iptables -L output for your review.  A iptables for dummies tutorial would be great for this guy.  Thanks!

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
in_world   all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED 
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'IN-unknown:'' 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED 
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'PASS-unknown:'' 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       tcp  --  anywhere             localhost           tcp dpt:3128 ! OWNER UID match dansguardian 
ACCEPT     all  --  anywhere             anywhere            
out_world  all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED 
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'OUT-unknown:'' 
DROP       all  --  anywhere             anywhere            

Chain in_world (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            state INVALID 
pr_world_fragments  all  -f  anywhere             anywhere            
pr_world_nosyn  tcp  --  anywhere             anywhere            state NEW tcp flags:!FIN,SYN,RST,ACK/SYN 
pr_world_icmpflood  icmp --  anywhere             anywhere            icmp echo-request 
pr_world_synflood  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
pr_world_malxmas  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG 
pr_world_malnull  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,ACK,URG 
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG 
in_world_all_c1  all  --  anywhere             anywhere            
in_world_irc_c2  all  --  anywhere             anywhere            
in_world_ftp_c3  all  --  anywhere             anywhere            
in_world_cups_s4  all  --  anywhere             anywhere            
in_world_webcache_s5  all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED 
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `''IN-world':'' 
DROP       all  --  anywhere             anywhere            

Chain in_world_all_c1 (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED 

Chain in_world_cups_s4 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:ipp state NEW,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ipp dpt:ipp state NEW,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:65535 dpt:ipp state NEW,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            udp spt:ipp dpt:ipp state NEW,ESTABLISHED 

Chain in_world_ftp_c3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp dpts:32768:61000 state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp-data dpts:32768:61000 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:32768:61000 state ESTABLISHED 

Chain in_world_irc_c2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd dpts:32768:61000 state ESTABLISHED 

Chain in_world_webcache_s5 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:webcache state NEW,ESTABLISHED 

Chain out_world (1 references)
target     prot opt source               destination         
out_world_all_c1  all  --  anywhere             anywhere            
out_world_irc_c2  all  --  anywhere             anywhere            
out_world_ftp_c3  all  --  anywhere             anywhere            
out_world_cups_s4  all  --  anywhere             anywhere            
out_world_webcache_s5  all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED 
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `''OUT-world':'' 
DROP       all  --  anywhere             anywhere            

Chain out_world_all_c1 (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state NEW,ESTABLISHED 

Chain out_world_cups_s4 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ipp dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ipp dpt:ipp state ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            udp spt:ipp dpts:1024:65535 state ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            udp spt:ipp dpt:ipp state ESTABLISHED 

Chain out_world_ftp_c3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpt:ftp state NEW,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpt:ftp-data state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpts:1024:65535 state RELATED,ESTABLISHED 

Chain out_world_irc_c2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpt:ircd state NEW,ESTABLISHED 

Chain out_world_webcache_s5 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:webcache dpts:1024:65535 state ESTABLISHED 

Chain pr_world_fragments (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'PACKET FRAGMENTS:'' 
DROP       all  --  anywhere             anywhere            

Chain pr_world_icmpflood (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            limit: avg 100/sec burst 50 
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'ICMP FLOOD:'' 
DROP       all  --  anywhere             anywhere            

Chain pr_world_malbad (4 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'MALFORMED BAD:'' 
DROP       all  --  anywhere             anywhere            

Chain pr_world_malnull (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'MALFORMED NULL:'' 
DROP       all  --  anywhere             anywhere            

Chain pr_world_malxmas (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'MALFORMED XMAS:'' 
DROP       all  --  anywhere             anywhere            

Chain pr_world_nosyn (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'NEW TCP w/o SYN:'' 
DROP       all  --  anywhere             anywhere            

Chain pr_world_synflood (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            limit: avg 100/sec burst 50 
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'SYN FLOOD:'' 
DROP       all  --  anywhere             anywhere            
bob@ubuntu:~$ sudo iptables -L

---

### Post by bnuytten on 2007-02-18
A very very short tutorial:
there are three tables, amongst FILTER is the one you will interest the most. You are not even aware of the other two tables, and you shouldn't for now ;-) Each table contains chains, some or always there and cannot be removed. Other "chains" are user-defined. Mosty of them are created by Ubuntu when you installed it. A chain in turn, is simply a sequence of rules.

Enough theory, now practice. You have the FILTER **table **with the INPUT, FORWARD and OUTPUT **chains**. All the other chains you see are user-defined. The first chains is for incoming packets, the last one for outgoing packets. Read carefully: packets, not connections. For a connection you need packets in both directions. Luckily for us, iptables knows something called "connection tracking".

Well, that doesn't solve your problem, but I hope you'll have the basics of what iptables is about. There may as well be some kind of GUI for ease of use... See also [http://en.wikipedia.org/wiki/Netfilter]("http://en.wikipedia.org/wiki/Netfilter")

---

### Post by bsahm on 2007-02-18
Thanks, I will have a look see where it goes from there.

---

### Post by bsahm on 2007-02-20
Nt

---

