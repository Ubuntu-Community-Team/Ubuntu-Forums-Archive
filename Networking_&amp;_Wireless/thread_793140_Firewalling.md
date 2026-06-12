---
title: "Firewalling"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by larso164 on 2008-05-13
Hello!

I am used to OpenBSD's pf and found that ufw is alright for extremely simple setups. Started with Linux server whith Ubuntu Server 8.04

I have a block-list that keeps a lot of hackers out and it looks something like this:
table <HACKERS> const { 172.16.0.0/12, 10.0.0.0/8, 169.254.0.0/16, 192.0.2.0/24, 0.0.0.0/8, 240.0.0.0/4, 12.183.101.0/24, 134.86.0.0/16, 140.186.152.0/23, 142.46.146.0/24, 155.230.0.0/16, 157.181.177.131, 162.105.0.0/16, 165.194.0.0/16, 165.243.0.0/16, 165.244.0.0/16, 168.126.0.0/16, 168.160.0.0/16, 192.116............

How do I put that in Linux packet filter?

---

### Post by koenn on 2008-05-13
The packet filter in Linux is called netfilter and is usually managed with iptables

man iptables:
```
DESCRIPTION
       Iptables  is  used  to  set  up, maintain, and inspect the tables of IP
       packet filter rules in the Linux kernel.  Several different tables  may
       be  defined.   Each  table contains a number of built-in chains and may
       also contain user-defined chains.

```
The common way of using iptables is by creating an init script with iptables statements, but there are also GUI frontends to iptables.

I don't know what the usual method is for blocking a list of addresses, but you could probably just do something like the following (in an init script) :
```

HACKERS="172.16.0.0/12 10.0.0.0/8 169.254.0.0/16 19...... "
for ADDR in $HACKERS; do
    iptables -A INPUT -s $ADDR -j DROP    #block traffic from $ADDR
    iptables -A OUTPUT -d $ADDR -j DROP   #block traffic towards $ADDR
done

```

If you prefer to maintain a list of addresses in a separate file, you can do
```

cat list_of_scriptkiddie_addresses | while read ADDR ; do
    iptables ...  $ADDR ...... 
    .....
done

```

---

