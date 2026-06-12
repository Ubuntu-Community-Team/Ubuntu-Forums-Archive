---
title: "Removing Bluetooth, Synaptic wants to remove Network-Mgr"
date: 2020-05-10
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2020-05-10
Couldn't find an answer to this one ....

Don't have BlueTooth on my Desktop system, so wanted to remove the software due to a security flaws identified in an update. Have UbuntuStudio v18.04.

Using Synaptic Pkg Mgr, I search Bluetooth. It wants to Remove Ardour, Guitarix, network-manager to name a few. Concerned about removing Network-Manager. What are the repurcussions of removing it? Will I lose network access? What other program can I use instead? What happened to "IFUP" and "net-tools"???

```

~$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 44:8a:5b:97:f6:c1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.20.55/24 brd 192.168.20.255 scope global dynamic noprefixroute eth0
       valid_lft 84434sec preferred_lft 84434sec
    inet6 fe80::19a3:cf90:ba0c:6ad3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


```

Thought I would post this before I, or someone else, makes a mistake. Cooler heads will prevail.

Thanks!

---

### Post by crip720 on 2020-05-10
Bluetooth might be baked into NM, can't remove one without the other.  Should be possible to disable bluetooth.  Removing NM without having another way of connecting first, does leave you without internet.  Say you don't have bluetooth on system, so my thinking is that it can't do anything, would need to have it and update should have fixed problem.  Some one else will probably have better advice.

---

### Post by chili555 on 2020-05-10
> Say you don't have bluetooth on system, so my thinking is that it can't do anything, I agree entirely.

Unless the security flaw you read about can be exploited when you have no bluetooth device turned on and, in fact, no bluetooth hardware at all, then you are safe.

I suggest that you ignore it.

---

