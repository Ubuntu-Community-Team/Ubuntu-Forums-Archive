---
title: "Bittorrent and iptables??"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by RalphSleigh on 2007-06-12
So I have a fresh 07.04 install with rTorrent installed (console BT client run in screen so I can use it over ssh).
 
I am having problems getting it to accept incoming connections, as all of the peers are listed as local. I know the torrent is healthy, and that I have got the port forwarding on my router right as it works on my win XP box. This leads me to believe its a configuration problem.

Running iptables -L gives me:   



Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:webmin:600
00
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:webmin:600
00
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:6881:6999

ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6999


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

from my understanding this should be enough to enable incoming connections (rTorrent says it is running on  port 6921), but no luck, what am I forgetting?

---

### Post by Vil on 2007-07-06
You might need to accept UDP as well, just an idea.

---

### Post by RobMBaker on 2007-10-07
Your default INPUT policy is ACCEPT; so it doesn't matter what those other rules are, the 'firewall' is set up to allow all incoming connections.
Therefore, your issue isn't a firewall one ... I have the same problem, and I don't know how to fix it.

---

