---
title: "iptables routing command"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by ultralame on 2008-02-06
I have a system which is physically connected to 192.168.1.1.  I have a piece of software that was written to listen only on 172.16.1.1 (long story).

So I created a virtual ethernet adapter (eth0:0; 172.16.1.1) and I want to forward all packets with a destination of 192.168.1.1:1234 to 172.16.1.1:1234.

I have tried several different iptables rules by modifying these, but I can't get it to work:
> /sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 -d 192.168.1.1 --dport 1234 -j DNAT --to 172.16.1.1:1234
/sbin/iptables -A FORWARD -p tcp -i eth0 -d 172.16.1.1 --dport 1234 -j ACCEPT

Any ideas?

---

### Post by mpokrywka on 2008-02-06
Your rule should work (I removed interface matching):
```
iptables -t nat -A PREROUTING -p tcp -d 192.168.1.1 --dport 1234 -j DNAT --to 172.16.1.1:1234
```
You can check this by running for example netcat server (nc -l -p 1234 -s 172.16.1.1) and try to connect from other machine (telnet 192.168.1.1 1234, use CTRL+] then "quit" to close telnet).
If netcat works but your software do not, then probably this software do not like other ip addresses and you will need some other network magic to rewrite source ip addresses.

---

### Post by ultralame on 2008-02-06
I just ran your iptables command:
> $ sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             ziggy.local         tcp dpt:1234 to:172.16.1.1:1234

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

I can connect to my SW via a telnet on 172.16.1.1 1234, but not on 192.168.1.10.

I also tried the nc command, same thing.  Able to connect directly to 172.16.1.1 but not on 192.168.1.10.

I don't think I have to do anything once I add the iptables rule, do I?  No reloading of the server, etc?

---

### Post by ultralame on 2008-02-06
Um, is this supposed to have something else:

> $ cat /proc/sys/net/ipv4/ip_forward
0

---

### Post by joebeasley on 2008-02-06
ip_forward should = 1.

---

### Post by ultralame on 2008-02-06
Yeah- after I posted I looked that up.  I used sysctl to set it, and changed the conf file.

So now the parameter comes up as "1", but the forwrd is still not working.

(Was sysctl something they changed for Gutsy?  I don't remember doing this before)

---

### Post by joebeasley on 2008-02-06
Don't know if the sysctl has changed.  

Is ziggy.local listed as 192.168.1.10 in your /etc/hosts file?  I noticted the nat listing refers to ziggy.local.  

Also if your default INPUT is set to DROP, you need to add a rule allowing access to 192.168.1.10 on port 1234.

I tested this and I could not connect from the machine running the nat, but I could connect from another machine on the network.

---

### Post by ultralame on 2008-02-07
OK.  Now I am confused.  Why is there a second loopback listed in my hosts?  Where did that come from?  Why did ziggy.local get substituted when I created the rule with:
> sudo iptables -t nat -A PREROUTING -p tcp -d 192.168.1.10 --dport 1234 -j DNAT --to 172.16.1.1:1234

FYI, it's not forwarding from the ziggy.local address either.


More info...


/etc/hosts
> 127.0.0.1 localhost
127.0.1.1 ziggy

/etc/network/interfaces
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0:0
iface eth0:0 inet static
address 172.16.1.1
netmask 255.255.255.0

ifconfig
> eth0      Link encap:Ethernet  HWaddr XXXXXX
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXXXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18420380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19738013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2986745221 (2.7 GB)  TX bytes:3375058300 (3.1 GB)
          Interrupt:18

eth0:0    Link encap:Ethernet  HWaddr 00:0F:B5:8D:74:F3
          inet addr:172.16.1.1  Bcast:172.16.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1697843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1697843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:578126078 (551.3 MB)  TX bytes:578126078 (551.3 MB)

iptables -t nat -L
> Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             ziggy.local         tcp dpt:1234 to:172.16.1.1:1234

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by ultralame on 2008-02-07
OK- After making the sysctl changes,  it seems that the forward is working when I connect from another machine on the network.

But it does not work from the localhost.  This is not a huge problem, since locally I can just direct to 172.16.1.1; but why won't this work locally?

---

