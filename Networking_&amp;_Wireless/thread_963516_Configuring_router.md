---
title: "Configuring router"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by h3llh0l3 on 2008-10-30
Hello all,

I am not sure if this should be posted here or not but I could use some help.
I have installed ubuntu hardy and for some testing I have configured postfix.
I have a router facing the internet and I am having hard time configuring the router to allow traffic on port 25 to my server. I have a BCM96338 ADSL Router. I have set iptable rules to allow the traffic on port 25 on the router. When I do a telnet localhost 25 it connects to the smtp server, but if I try telnet xxx.xxx.xxx.xxx 25 from another computer on the LAN or from different network it does not connect.
Here is how my iptables rule look like:
xxx.xxx.xxx.xxx -> IP Address of my linux machine

```

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             xxx.xxx.xxx.xxx        tcp dpt:smtp

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             anywhere            tcp dpt:smtp to:xxx.xxx.xxx.xxx

```

Could some one please point into the right direction to fix this.

Thanks :)

---

### Post by h3llh0l3 on 2008-10-31
Anyone any ideas?
Help would be really appreciated.

Thanks.

---

