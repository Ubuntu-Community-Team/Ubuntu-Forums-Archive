---
title: "IPTABLES as A router"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-02-17
I have a machine that hosts a web server and I have a few other machines I also want to access from the Internet.
I have configured iptables to act as a router and send traffic to those machines using these commands
```

#-A PREROUTING -d aaa.bbb.ccc.ddd/32 -j DNAT --to-destination 192.168.1.2
#-A POSTROUTING -s 192.168.1.2/32 -j SNAT --to-source aaa.bb.ccc.ddd
```

That works as intended.

I also have some port blocking rules in iptables similar to this one;

```
-A INPUT -p tcp -m tcp --dport 1434 -j DROP
-A INPUT -p udp -m udp --dport 1434 -j DROP
```

I thought this would block any traffic on that port going to any of the routed machines. 

But my ISP sent me an alert that port 1434 was open on the Windows Server's IP address. 

What am I missing?

---

### Post by linuchsan on 2018-02-17
Use nmap from an outside ip, to confirm, that the port is really open.

---

### Post by rsteinmetz70112 on 2018-02-21
I've now done some remote testing and nmap reports the port as "filtered" on the private and public ip addresses. Not what I expected.

Perhaps because I'm using DROP, which causes a time out, rather than REJECT the ISP is interpreting that as open, which is isn't.
nmap apparently realizes the server is up but that the port is not accessible. I tried it with the server down and got a different message about the server being unreachable.

Server down
```
# nmap -p 1434 aaa.bbb.ccc.ddd

Starting Nmap 7.01 ( https://nmap.org ) at 2018-02-21 13:17 EST
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.29 seconds
```

Server up, port blocked from outside the site
```
# nmap -p 1434 aaa.bbb.ccc.ddd

Starting Nmap 7.01 ( https://nmap.org ) at 2018-02-21 10:55 EST
Nmap scan report for aaa.bbb.ccc.ddd
Host is up (0.044s latency).
PORT     STATE    SERVICE
1434/tcp filtered ms-sql-m

Nmap done: 1 IP address (1 host up) scanned in 13.80 seconds
```

Server up from inside the network.
```
# nmap -p 1434 192.168.1.2

Starting Nmap 7.01 ( [https://nmap.org](https://nmap.org) ) at 2018-02-21 09:50 CST
Nmap scan report for shylock (192.168.1.2)
Host is up (0.000088s latency).
PORT     STATE    SERVICE
1434/tcp filtered ms-sql-m
MAC Address: 00:23:54:B7:84:8D (Asustek Computer)
```

This is not the behavior I need. I need the port accessible from the inside but not the outside.
I've modified the IPtables rules to add "-m iprange -dst-range aaa.bbb.ccc.ddd-aaa.bbb.ccc.fff" to the rules. I need to test the new rules.

---

