---
title: "Error while trying to create a NAT rule in IPTABLES"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by h3llh0l3 on 2008-09-23
Hello all,

I am new to Linux and I am trying to setup a webserver. I am running Ubuntu on VMWare, which has 3 interfaces(eth0, eth1 & eth2).
eth0 -> Connected to LAN(IP: 192.168.221.128 )
eth1 -> Internal interface on the firewall(IP: 10.1.1.1)
eth2 -> DMZ(IP: 10.2.1.1, running Apache2)

I am trying to create a rule which would route HTTP traffic on eth1 to port 80 on eth2. When I executed the command to create the rule I got the following error:

```
root@lab:/# iptables -t NAT -A PREROUTING -p tcp --dport http -d 192.168.221.128 -j DNAT --to-destination 10.2.1.1:80
iptables v1.3.8: can't initialize iptables table `NAT': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

When I do uname -a it shows me the following:

```
root@lab:/# uname -a
Linux lab 2.6.24-19-server #1 SMP Wed Aug 20 23:54:28 UTC 2008 i686 GNU/Linux
```

Could someone please point me in the correct direction on how to get it fixed?

Thanks :)

---

### Post by kevdog on 2008-09-23
I'm not an iptables expert but I believe its nat and not NAT

---

### Post by h3llh0l3 on 2008-09-23
> **kevdog said:**
> I'm not an iptables expert but I believe its nat and not NAT

Thanks, that worked. Didn't know that upper and lower case plays vital role :)

---

