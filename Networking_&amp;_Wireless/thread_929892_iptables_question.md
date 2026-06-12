---
title: "iptables question"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by wdypdx1 on 2008-09-25
I'm new and learning with this, and in my searches I haven't found an answer to this question yet...

I'm trying to run this code in order to set up InternetConnectionSharing:

-----------------------------------
$sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
$sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$sudo iptables -A POSTROUTING -t nat -j MASQUERADE
-----------------------------------
And I get this error message:

-----------------------------------
iptables v1.3.8: Unknown arg `--state'
Try `iptables -h' or 'iptables --help' for more information.
-----------------------------------

I tried iptables -h and did some searching but haven't come up with an answer yet. :confused:

Thanks.

I'm using Hardy 8.04 LTS updated yesterday

---

