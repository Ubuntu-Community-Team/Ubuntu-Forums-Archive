---
title: "Router Trouble?"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by torgo4life on 2007-07-06
[My problem.]("http://forum.myspace.com/index.cfm?fuseaction=messageboard.viewThread&entryID=38444125&adTopicID=6&categoryID=0&IsSticky=0&groupID=100000292&Mytoken=ECEE1EAB-AD2E-4A61-AE2EB6924BA8D0B530692312")

I've tried all given solutions, but they haven't worked. Any new ideas?

---

### Post by spd106 on 2007-07-06
When you tried pinging the external hostname did it resolve the address even though the replies failed?

Can you check that the routing table has the default gateway set?
```
ip route
```
It should look something like this
```
:~$ ip r
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.8 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0 

```

---

