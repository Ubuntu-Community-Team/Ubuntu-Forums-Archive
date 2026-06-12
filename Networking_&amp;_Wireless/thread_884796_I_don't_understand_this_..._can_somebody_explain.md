---
title: "I don't understand this ... can somebody explain?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by johan.alfa on 2008-08-09
Hello all,

Situation:
I have a ubuntu hardy server with a static IP xxx.xxx.xxx.xxx
I opened port 80 for http and another one for ssh.

Problem:
I can not log in to the server or using it's IP xxx.xxx.xxx.xxx

What works:
I used my domain management to give a domain name to the IP adres. Now the server with IP xxx.xxx.xxx.xxx has a name like bla.bla.net

What I do not understand.
I can ssh and use the apache server with name bla.bla.net but not with ip xxx.xxx.xxx.xxx

Who knows how this is possible?

Thank you,

---

### Post by demiurgicdaemon on 2008-08-09
I would try pinging the .net address and see what the DNS ip lookup tells you the true ip address is.

---

### Post by johan.alfa on 2008-08-09
> **demiurgicdaemon said:**
> I would try pinging the .net address and see what the DNS ip lookup tells you the true ip address is.

Ping gives the same IP I gave it.

greetings

---

### Post by johan.alfa on 2008-08-10
Some more info for those who know.

I can not ping to the IP nor to the domain name.
I can use ssh with a name but not with IP.
I can use apache server with name but not with IP.

Why can't I reach the machine by IP.

greetings,

Johan

---

### Post by SpaceTeddy on 2008-08-11
first off - this does not make a whole lot of sense :( 
i will need to do some heavy guessing here, and it is quite possible that i am wrong.

For me, it all looks like a combination of a firewall and apache configuration. Why ?

Well - you cannot ping the ip. This is clearly a problem with a packet filter. Pings always reach their destination in the internet - icmp is vital to it's functionality. So, the internet does not block it. This leaves only a router/firewall in your network or the paket filter on the server itself. Do you have a firewall installed on the server ?

Also, this theory is supported by the fact that you CAN access the web-server running on the machine with it's name, but not with it's ip. This would mean, that in the configuration of the apache the virtual host only answers to the name - NOT the ip. What happens if you telnet to the ip on port 80 ? is a connection established ? is it rejected ? or does it time out ? I would say it is rejected, meaning the apache2 on the server does not want to talk to you, as you are addressing a site that is not runnig there. 
But the fact that you can reach the apache2 and NOT ping the machine also means, that there is some firewall/router in between that blocks the icmp, but lets port 80 pass. Or the machine itself does this.

there have already been a few questions in here, but to debug this further, i would need the ip of the source computer you are connecting from, the ip of the server (or at least the knowledge if they are in the same subnet without any firewall in between them) and the output of the following commands (run on the server)

```
sudo iptables -L
sudo iptables -L --table nat
ifconfig
route -n
```

maybe that helps.
Again, i am guessing here - or rather, writing down my thought on how such a scenario could be created. If i misunderstood anything i am sorry :) also - again - it is quite possible that i am entirely wrong...

hope it helps :)

---

### Post by johan.alfa on 2008-08-11
Hello Thanks for helping,

I don't like to publish the IP on a public forum.

Hardware situation is like this.
My ISP installed a CISCO 800 router.
That router has wan side IP xxx.xxx.xxx.xxx
This is the IP I use to ping.
They do not allow us to control that router so I ask them to open all ports. All data is send to lan side 10.0.0.2 which we can use. My feeling is something in this cisco router is happening beyond my knowledge.

Behind the cisco router I installed another hardware router and that router uses port forwarding for ssh and http. No other ports are open on that router.

Ubuntu is a standard server install with no firewall installed.
SSH and apache2 working fine.

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

sudo iptables -L --table nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:17:d3:15
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe17:d315/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:393033 (383.8 KB)  TX bytes:382841 (373.8 KB)
          Base address:0x1070 Memory:ec820000-ec840000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4572 (4.4 KB)  TX bytes:4572 (4.4 KB)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

When I telnet to the IP on port 80 all i get is a blinking cursor.

Thank you,

---

### Post by SpaceTeddy on 2008-08-11
ok - i would say it is the firewall that is blocking you. Your server itself does not have any paket filter loaded, and your network configuration looks clean and working.
i'd say the cisco machine is blocking your somehwere. Did you tell the administrator that you want all ports open, or did you tell them that you also want all incoming ports open ? 

for the telnet  the blinking cursor indicates that you have an established connection. that is good. so basic connectiviy is given. The pings cannot reach the server as you do not forward them from your own router (or so i think)

can you please try to telnet into port 22 on the server ? see if that gives you something aswell ? also, i assume that the ssh server is running - can you please post the ouput of 
```
sudo netstat -lnp
``` (forgot that in my last request)
Also, can you ssh on the server to itself (i.e. ssh localhost) - see if you can login there. 

If all this is correct, it is either a problem with your own router, or with the cisco machine - the ubuntu works fine.

i am more confused now :confused:

---

### Post by johan.alfa on 2008-08-11
I'm at home and the sever is at school so I do all the testing with ssh. Just to illustrate that it is working fine name based.

sudo netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4094/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4272/apache2

--- I changed the following port number from its real port to ----
tcp6       0      0 :::----                 :::*                    LISTEN      3996/sshd
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     10462    4094/mysqld         /var/run/mysqld/mysqld.sock

I can ssh to localhost

I asked the ISP to open all ports. Don't understand what you mean with incoming ports open.

thank you very much

Never had a more annoying situation.
I can do everything I want name based but I don't understand it.
That does not really give a secure feeling.

greetings,

---

