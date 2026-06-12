---
title: "iptables config question"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by Bjoeboo on 2008-01-08
Not really an Ubuntu question but you guys are usually pretty smart.  This is a  little linksys home router I configured via its builtin web configuration pages.  Its running an open source Linux firmware which applies all your settings you make on the webpage to the iptables.  Anyways, **lines 10 & 18 are kind of scary to me**.  Can anybody explain how this little Linksys home router iptables config could possibly be secure? (Its WAN port is on internet and LAN ports are in use internally)

        ~ # iptables -L
1    Chain INPUT (policy ACCEPT)
2    target     prot opt source               destination
3    ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
4    DROP       udp  --  anywhere             anywhere            udp dpt:route
5    DROP       udp  --  anywhere             anywhere            udp dpt:route
6    ACCEPT     udp  --  anywhere             anywhere            udp dpt:route
7    logaccept  tcp  --  anywhere             Linksys             tcp dpt:ftp-data
8    DROP       icmp --  anywhere             anywhere
9    DROP       igmp --  anywhere             anywhere
10    ACCEPT     all  --  anywhere             anywhere            state NEW
11    logaccept  all  --  anywhere             anywhere            state NEW
12    DROP       all  --  anywhere             anywhere
13    
14    Chain FORWARD (policy ACCEPT)
15    target     prot opt source               destination
16    ACCEPT     gre  --  192.168.0.0/24      anywhere
17    ACCEPT     tcp  --  192.168.0.0/24      anywhere            tcp dpt:1723
18    ACCEPT     all  --  anywhere             anywhere
19    logdrop    all  --  anywhere             anywhere            state INVALID
20    TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1461:65535 TCPMSS set 1460
21    lan2wan    all  --  anywhere             anywhere
22    ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
23    DROP       tcp  --  anywhere             XPBOX01                tcp spt:https
24    DROP       tcp  --  anywhere             XPBOX01                tcp spt:ssh
25    ACCEPT     tcp  --  anywhere             XPBOX01                tcp dpt:59020
26    TRIGGER    all  --  anywhere             anywhere            TRIGGER type:in match:0 relate:0
27    trigger_out  all  --  anywhere             anywhere
28    ACCEPT     all  --  anywhere             anywhere            state NEW
29    DROP       all  --  anywhere             anywhere
30    
31    Chain OUTPUT (policy ACCEPT)
32    target     prot opt source               destination
33    
34    Chain advgrp_1 (0 references)
35    target     prot opt source               destination
36    
37    Chain advgrp_10 (0 references)
38    target     prot opt source               destination
39    
40    Chain advgrp_2 (0 references)
41    target     prot opt source               destination
42    
43    Chain advgrp_3 (0 references)
44    target     prot opt source               destination
45    
46    Chain advgrp_4 (0 references)
47    target     prot opt source               destination
48    
49    Chain advgrp_5 (0 references)
50    target     prot opt source               destination
51    
52    Chain advgrp_6 (0 references)
53    target     prot opt source               destination
54    
55    Chain advgrp_7 (0 references)
56    target     prot opt source               destination
57    
58    Chain advgrp_8 (0 references)
59    target     prot opt source               destination
60    
61    Chain advgrp_9 (0 references)
62    target     prot opt source               destination
63    
64    Chain grp_1 (0 references)
65    target     prot opt source               destination
66    
67    Chain grp_10 (0 references)
68    target     prot opt source               destination
69    
70    Chain grp_2 (0 references)
71    target     prot opt source               destination
72    
73    Chain grp_3 (0 references)
74    target     prot opt source               destination
75    
76    Chain grp_4 (0 references)
77    target     prot opt source               destination
78    
79    Chain grp_5 (0 references)
80    target     prot opt source               destination
81    
82    Chain grp_6 (0 references)
83    target     prot opt source               destination
84    
85    Chain grp_7 (0 references)
86    target     prot opt source               destination
87    
88    Chain grp_8 (0 references)
89    target     prot opt source               destination
90    
91    Chain grp_9 (0 references)
92    target     prot opt source               destination
93    
94    Chain lan2wan (1 references)
95    target     prot opt source               destination
96    
97    Chain logaccept (2 references)
98    target     prot opt source               destination
99    ACCEPT     all  --  anywhere             anywhere
100    
101    Chain logdrop (1 references)
102    target     prot opt source               destination
103    DROP       all  --  anywhere             anywhere
104    
105    Chain logreject (0 references)
106    target     prot opt source               destination
107    REJECT     tcp  --  anywhere             anywhere            tcp reject-with tcp-reset
108    
109    Chain trigger_out (1 references)
110    target     prot opt source               destination

---

### Post by Lostincyberspace on 2008-01-08
Check here to see if the ports are listed if they are not listed then you should close them. If they are then decide if you want to use that port.
[URL="http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers"]
http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers[/URL]

---

