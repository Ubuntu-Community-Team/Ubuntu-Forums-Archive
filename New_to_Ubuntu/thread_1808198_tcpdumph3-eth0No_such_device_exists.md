---
title: "tcpdump:h3-eth0:No such device exists"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by mmuntaha on 2011-07-20
Hi! i'm working on openflow, i'm new to it and i'm following this tutorial
[COLOR=RoyalBlue]http://www.openflow.org/wk/index.php/OpenFlow_Tutorial#Parsing_Packets_with_the_NOX_packet_libraries[/COLOR]

when i type following command 
[COLOR=RoyalBlue]mininet> xterm h2 h3 h4[/COLOR]

then it is supposed to open three xterms , but it opens only one window in xming server,
and when i type following command
[COLOR=RoyalBlue]# tcpdump -XX -n -i h3-eth0[/COLOR]
then it gives me error
tcpdump:h3-eth0:No such device exists
(SIOCGIFHWADDR:No such device)

PLEASE any help!!:confused:

---

