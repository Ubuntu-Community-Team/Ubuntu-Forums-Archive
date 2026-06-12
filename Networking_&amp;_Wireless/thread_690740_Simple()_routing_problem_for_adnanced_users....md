---
title: "Simple(?) routing problem for adnanced users...?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by gargl on 2008-02-07
Hi there.
So I finally set up my routing network (as described here(you dont need to dig into the details):[http://ubuntuforums.org/showthread.php?t=524012](http://ubuntuforums.org/showthread.php?t=524012))
and my only problem left is, I can't connect to my router from my Desktop PC.

Internet works, ping works everything is fine.

Router(192.168.100.1)<===>Desktop(192.168.100.6)<===>(e.g. Laptop)


I assume that I misconfigured some routing command, so that I am not able
to access my router from my Desktop anymore.
But to be honest I didnt got a clue which screw I have to turn to solve my problem.
For advanced users I think this is an easy problem?
So what do I need to do to access my router from my desktop?
I would appreciate your help!!

Desktop#route -n:
```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.100.1   0.0.0.0         UG    100    0        0 eth1

```

If you need further informations please let me know.

Thanks in advance.

---

### Post by gargl on 2008-02-08
anyone please? :(
Really no one??

---

