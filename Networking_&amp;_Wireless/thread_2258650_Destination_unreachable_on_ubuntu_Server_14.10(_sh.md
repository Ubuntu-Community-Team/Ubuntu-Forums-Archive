---
title: "Destination unreachable on ubuntu Server 14.10( share internet to virtualbox)"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by n3wguys on 2014-12-29
Dear All,

I have one machine server (ubuntu server 14.10) on virtual box:
1. two card with setting : 
    a. Adapter 1: setting to bridged Adapter, remotely based internet sharing Device
    b. Adapter 2: internal network,intnet
2. eth0 - setting inet dhcp (IP internet get from Modem), and eth1, setting with static IP
3. ping to google.com from terminal, system reply From  myserver(192.168.10.1) icmp_seq=1 destination host unreacheable.

Please help me.

thank you

---

### Post by TheFu on 2014-12-29
It is probably a routing priority issue.
Please post the output from **route** with each configuration you want. Notice the differences.  To get this working, your network-fu (understanding of networking) will need to be strong.

---

### Post by n3wguys on 2014-12-29
Here the route

[ATTACH]258879[/ATTACH]

---

### Post by n3wguys on 2014-12-30
Dear All,

my problem is solved...

in the eth1 card on virtualbox, I have to include dns-nameserver ip_address_from_eth0

---

### Post by TheFu on 2014-12-30
Great.  BTW, you can copy/paste text instead of using images. That is much more preferred.

---

### Post by n3wguys on 2015-01-16
Like this i configure but only for one pc virtual.

[http://bojalinuxer.blogspot.com/2012/09/setting-network-di-virtualbox.html](http://bojalinuxer.blogspot.com/2012/09/setting-network-di-virtualbox.html)

---

