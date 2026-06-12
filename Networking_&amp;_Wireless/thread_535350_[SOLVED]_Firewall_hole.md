---
title: "[SOLVED] Firewall hole ?"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by cygnus81 on 2007-08-26
Can it be that my firewall lets DHCP request pass through although they are supposed to be dropped ?

my INPUT chain (first rule sends NEW packets to a "macfilter" chain):
```

# iptables -L INPUT
Chain INPUT (policy DROP)
target     prot opt source               destination         
macfilter  0    --  anywhere             anywhere            state NEW 
...
...

```

the "macfilter" chain (for testing proposes blocks everything. at least supposed to..):
```

# iptables -L macfilter
Chain macfilter (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning prefix `**MAC FILTER** ' 
DROP       0    --  anywhere             anywhere

```

and a portion of the syslog (while trying to acquire an IP address):
```

Aug 26 19:06:05 [kernel] [168317.491058] **MAC FILTER** IN=ra0 OUT= MAC=00:0e:2e:5c:ff:8a:00:14:a5:1c:77:c0:08:00 SRC=192.168.0.199 DST=192.168.0.1 LEN=334 TOS=0x00 PREC=0x00 TTL=128 ID=7706 PROTO=UDP SPT=68 DPT=67 LEN=314 
Aug 26 19:06:05 [dhcpd] DHCPREQUEST for 192.168.0.199 from 00:14:a5:1c:77:c0 (LAPTOP1) via ra0
Aug 26 19:06:05 [dhcpd] DHCPACK on 192.168.0.199 to 00:14:a5:1c:77:c0 (LAPTOP1) via ra0

```

As you can see in the log, it seems like iptables drops the packet (at least it logs it), but then the dhcp daemon replies.
Which one is wrong - my configuration or my understanding ? or both ?

---

### Post by cygnus81 on 2007-08-28
Well, that was my understanding which was wrong of course. Computers don't lie :-D

DHCP is transmitted over UDP which is a connectionless protocol. Therefore it has no states. So DHCP packets never match the rule "state NEW", and therefore are never passed to the "macfilter" chain.

---

