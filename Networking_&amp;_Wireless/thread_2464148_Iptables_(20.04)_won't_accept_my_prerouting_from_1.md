---
title: "Iptables (20.04) won't accept my prerouting from 18.04"
date: 2021-06-25
forum: Networking &amp; Wireless
---

### Post by jobe77x on 2021-06-25
I've just installed a clean Ubuntu server 20.04, and was going to add some pre/post routing rules, but I can't get them to be added.

I've tried

[B] iptables -A PREROUTING -i enp0s3 -p tcp -m tcp --dport 49620 -j DNAT --to-destination 192.168.2.53:22222
[/B]
but getting the response:

[B]iptables: No chain/target/match by that name.
[/B]
This worked without any issues on my older 18.04 server.
I've searched for answer how to add a chain, but can't find anything about it..

---

### Post by Tadaen_Sylvermane on 2021-06-25
I'm mediocre at best with iptables but it looks like you aren't passing a table to it.

[https://my.esecuredata.com/index.php?/knowledgebase/article/49/how-to-redirect-an-incoming-connection-to-a-different-ip-address-on-a-specific-port-using-iptables/](https://my.esecuredata.com/index.php?/knowledgebase/article/49/how-to-redirect-an-incoming-connection-to-a-different-ip-address-on-a-specific-port-using-iptables/)

Notice the -t flag.

---

### Post by jobe77x on 2021-06-25
that made the error message go away, but when I'm checking with "iptables -L" it's not there.

[B]Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/B]

---

