---
title: "iptables rule to allow pan1 -&gt; bnep0 for bluetooth internet access"
date: 2015-01-02
forum: Networking &amp; Wireless
---

### Post by sector_ on 2015-01-02
Does anyone know how to add a rule in iptables/ufw to allow the following connections that are currently being blocked? 
Jan  2 14:52:55 linux kernel: [13898.434172] [UFW BLOCK] IN=pan1 OUT= PHYSIN=bnep0 MAC=00:00:00 SRC=172.16.10.215 DST=172.16.10.10 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=1864 DF PROTO=UDP SPT=43460 DPT=53 LEN=42 
Jan  2 14:52:55 linux kernel: [13898.951930] [UFW BLOCK] IN=pan1 OUT= PHYSIN=bnep0 MAC=00:00:00 SRC=172.16.10.215 DST=172.16.10.10 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=1865 DF PROTO=UDP SPT=17326 DPT=53 LEN=38 
Jan  2 14:52:56 linux kernel: [13899.415949] [UFW BLOCK] IN=pan1 OUT= PHYSIN=bnep0 MAC=00:00:00 SRC=172.16.10.215 DST=172.16.10.10 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=1866 DF PROTO=UDP SPT=13876 DPT=53 LEN=42 
Jan  2 14:52:56 linux kernel: [13899.949817] [UFW BLOCK] IN=pan1 OUT= PHYSIN=bnep0 MAC=00:00:00 SRC=172.16.10.215 DST=172.16.10.10 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=1867 DF PROTO=UDP SPT=54583 DPT=53 LEN=38 

Basically I'm using my desktop's internet for my phone to use for the internet as I have no reception where I currently am. When I run "ufw disable" it work's and the phone can go onto the internet so it seem to be the above firewall rule that's blocking it. 
I tried adding the below in /etc/ufw/before.rules, but no dice:
-A FORWARD -m physdev --physdev-in pan1 -j ACCEPT
  
and this in /etc/default/ufw:
DEFAULT_FORWARD_POLICY="ACCEPT"

Cheers for any help!

---

