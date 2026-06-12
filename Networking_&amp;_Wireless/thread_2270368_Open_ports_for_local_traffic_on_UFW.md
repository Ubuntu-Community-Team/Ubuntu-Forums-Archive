---
title: "Open ports for local traffic on UFW"
date: 2015-03-22
forum: Networking &amp; Wireless
---

### Post by johnnyslogan on 2015-03-22
Hello,

I have a server with a VPN client-interface. Everything is running fine and dandy. Except when I enable UFW-firewall. I would like it so (almost) nothing goes in or out - except local traffic - when VPN is down. But when UFW is enabled local traffic on other ports than SSH is no good. So no NFS or ping from 192.168.0.3 to 192.168.0.4 for instance. 

Thought I had opened up for all traffic on local network. But that apparently does not include any ports on the local network except for those explicitly mentioned and SSH.

Here's the result of ufw status verbose

```

Status: activeLogging: on (low)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    192.168.0.0/24
192.168.0.0/24             ALLOW IN    Anywhere
53/udp                     ALLOW IN    Anywhere
1194                       ALLOW IN    Anywhere
Anywhere on tun0           ALLOW IN    Anywhere
53/udp (v6)                ALLOW IN    Anywhere (v6)
1194 (v6)                  ALLOW IN    Anywhere (v6)
Anywhere (v6) on tun0      ALLOW IN    Anywhere (v6)


53/udp                     ALLOW OUT   Anywhere
1194                       ALLOW OUT   Anywhere
Anywhere                   ALLOW OUT   Anywhere on tun0
53/udp (v6)                ALLOW OUT   Anywhere (v6)
1194 (v6)                  ALLOW OUT   Anywhere (v6)
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on tun0



```

---

