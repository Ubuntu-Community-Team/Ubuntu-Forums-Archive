---
title: "Please help with IPTables rule"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by Jorsher on 2014-06-06
Hello!

I'm currently overseas in a very "rural" area.  Internet is slow and expensive.  My current plan is 15gb and the person sharing it with me is consuming over 1gb a day.  I know how to set speed-based limits using QoS, but I would like to set a hard data cap.  I've been reading around for a while, and trying various scripts and attempted editing them on my own with no luck.  I'm entering the scripts under "WAN Up" section of scripts on the Tomato firmware for my router.

My ultimate goal is that after a specific IP address uses more than 7.5GB, they will not be able to connect except between 3am and 8am.

So far I've not had luck just setting a quota without the time constraints.

I've tried:

```
iptables -A INPUT -d 192.168.1.144 -m quota --quota 2147483648 -j ACCEPT
iptables -A INPUT -j DROP
```

And:

```
iptables -N limit
iptables -A INPUT -d 192.168.1.144 -j limit
iptables -A INPUT -s 192.168.1.144 -j limit
iptables -A limit -m quota --quota 1048576 -j ACCEPT
iptables -A limit -j REJECT
```

Among other things I've since deleted...

Thanks in advance.

---

