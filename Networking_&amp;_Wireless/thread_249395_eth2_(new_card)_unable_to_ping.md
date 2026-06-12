---
title: "eth2 (new card): unable to ping"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by WesleyWex on 2006-09-02
I want to set up my Xubuntu so it can be a router with QoS enabled. I've set up it first as a usual machine with just one network card, and my modem was being the router in my network.

Now I've installed a working network card but even configure through the network-admin interface and change the cable that is connected to the switch, the network stops.

Look what happens when I try to ping the router:

```
root@servidor:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
```

This might be useful:
```
root@servidor:~# iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning
DROP       all  --  127.0.0.0/8          anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  anywhere             servidor
ACCEPT     all  --  anywhere             192.168.1.255
DROP       all  --  anywhere             224.0.0.1
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
DROP       all  --  anywhere             224.0.0.1
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  servidor             anywhere
ACCEPT     all  --  192.168.1.255        anywhere
DROP       all  --  anywhere             224.0.0.1
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere
```

Where can I set up this new network card?

---

