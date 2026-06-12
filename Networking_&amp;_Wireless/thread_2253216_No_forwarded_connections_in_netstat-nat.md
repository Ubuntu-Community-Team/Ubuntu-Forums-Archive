---
title: "No forwarded connections in netstat-nat"
date: 2014-11-18
forum: Networking &amp; Wireless
---

### Post by karaluh on 2014-11-18
I have Windows terminal server behind Ubuntu nat. I can connect to it from the Internet without problems, all appropriate ports are correctly forwarded with iptables. I am however unable to display active connections to this server on the Ubuntu box using netstat-nat. I tried -D, -S, -L and -R switches and I don't see the connections on any of the returned lists. I'm running netstat-nat by sudo obviously. What am I doing wrong?

---

### Post by Doug S on 2014-11-18
I have never used netstat-nat, but I might try it if your troubles continue. Are you able to view the connection tracking table directly? Example (a little empty at the moment):```
doug@doug-64:~$ [COLOR=#ff0000]sudo cat /proc/net/ip_conntrack[/COLOR]
tcp      6 5 TIME_WAIT src=192.168.111.101 dst=91.189.89.225 sport=64401 dport=443 src=91.189.89.225 dst=173.180.45.4 sport=443 dport=64401 [ASSURED] mark=0 use=2
tcp      6 431353 ESTABLISHED src=192.168.111.101 dst=192.168.111.1 sport=60339 dport=22 src=192.168.111.1 dst=192.168.111.101 sport=22 dport=60339 [ASSURED] mark=0 use=2
tcp      6 30 TIME_WAIT src=192.168.111.106 dst=192.168.111.1 sport=57535 dport=139 src=192.168.111.1 dst=192.168.111.106 sport=139 dport=57535 [ASSURED] mark=0 use=2
tcp      6 42 TIME_WAIT src=192.168.111.101 dst=207.167.198.20 sport=64404 dport=110 src=207.167.198.20 dst=173.180.45.4 sport=110 dport=64404 [ASSURED] mark=0 use=2
tcp      6 299 ESTABLISHED src=192.168.111.101 dst=192.168.111.1 sport=56326 dport=22 src=192.168.111.1 dst=192.168.111.101 sport=22 dport=56326 [ASSURED] mark=0 use=2
tcp      6 431640 ESTABLISHED src=192.168.111.101 dst=157.56.116.209 sport=54545 dport=12350 src=157.56.116.209 dst=173.180.45.4 sport=12350 dport=54545 [ASSURED] mark=0 use=2
tcp      6 28 TIME_WAIT src=192.168.111.106 dst=192.168.111.1 sport=57534 dport=139 src=192.168.111.1 dst=192.168.111.106 sport=139 dport=57534 [ASSURED] mark=0 use=2
tcp      6 431880 ESTABLISHED src=192.168.111.101 dst=134.170.24.160 sport=54580 dport=443 src=134.170.24.160 dst=173.180.45.4 sport=443 dport=54580 [ASSURED] mark=0 use=2
tcp      6 431845 ESTABLISHED src=192.168.111.101 dst=192.168.111.1 sport=49182 dport=445 src=192.168.111.1 dst=192.168.111.101 sport=445 dport=49182 [ASSURED] mark=0 use=2
tcp      6 431675 ESTABLISHED src=192.168.111.101 dst=157.56.52.46 sport=54544 dport=40025 src=157.56.52.46 dst=173.180.45.4 sport=40025 dport=54544 [ASSURED] mark=0 use=2
tcp      6 79 TIME_WAIT src=192.168.111.106 dst=207.167.198.20 sport=57536 dport=110 src=207.167.198.20 dst=173.180.45.4 sport=110 dport=57536 [ASSURED] mark=0 use=2
```Edit: I installed netstat-nat and tried it. It seems to be working fine for me. Example (content edited, as readers do not need to know my daughters connections, mine are O.K.):```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat-nat[/COLOR]
Proto NATed Address                  Destination Address            State
tcp   doug-xps2.smythies.com:65126   205.250.85.72:http             TIME_WAIT
tcp   doug-xps2.smythies.com:65171   202.177.216.233:https          TIME_WAIT
tcp   doug-xps2.smythies.com:54544   157.56.52.46:40025             ESTABLISHED
tcp   doug-xps2.smythies.com:65152   pe-in-f95.1e100.net:http       TIME_WAIT
```

---

### Post by Hadaka on 2014-11-18
Hi, try inserting a space,,
```
netstat -nat
```
[B]netstat -nat
..........^
[/B]

---

### Post by karaluh on 2014-11-19
> **Doug S said:**
> I have never used netstat-nat, but I might try it if your troubles continue. Are you able to view the connection tracking table directly? Example (a little empty at the moment):```
doug@doug-64:~$ [COLOR=#ff0000]sudo cat /proc/net/ip_conntrack[/COLOR]
tcp      6 5 TIME_WAIT src=192.168.111.101 dst=91.189.89.225 sport=64401 dport=443 src=91.189.89.225 dst=173.180.45.4 sport=443 dport=64401 [ASSURED] mark=0 use=2
tcp      6 431353 ESTABLISHED src=192.168.111.101 dst=192.168.111.1 sport=60339 dport=22 src=192.168.111.1 dst=192.168.111.101 sport=22 dport=60339 [ASSURED] mark=0 use=2
tcp      6 30 TIME_WAIT src=192.168.111.106 dst=192.168.111.1 sport=57535 dport=139 src=192.168.111.1 dst=192.168.111.106 sport=139 dport=57535 [ASSURED] mark=0 use=2
tcp      6 42 TIME_WAIT src=192.168.111.101 dst=207.167.198.20 sport=64404 dport=110 src=207.167.198.20 dst=173.180.45.4 sport=110 dport=64404 [ASSURED] mark=0 use=2
tcp      6 299 ESTABLISHED src=192.168.111.101 dst=192.168.111.1 sport=56326 dport=22 src=192.168.111.1 dst=192.168.111.101 sport=22 dport=56326 [ASSURED] mark=0 use=2
tcp      6 431640 ESTABLISHED src=192.168.111.101 dst=157.56.116.209 sport=54545 dport=12350 src=157.56.116.209 dst=173.180.45.4 sport=12350 dport=54545 [ASSURED] mark=0 use=2
tcp      6 28 TIME_WAIT src=192.168.111.106 dst=192.168.111.1 sport=57534 dport=139 src=192.168.111.1 dst=192.168.111.106 sport=139 dport=57534 [ASSURED] mark=0 use=2
tcp      6 431880 ESTABLISHED src=192.168.111.101 dst=134.170.24.160 sport=54580 dport=443 src=134.170.24.160 dst=173.180.45.4 sport=443 dport=54580 [ASSURED] mark=0 use=2
tcp      6 431845 ESTABLISHED src=192.168.111.101 dst=192.168.111.1 sport=49182 dport=445 src=192.168.111.1 dst=192.168.111.101 sport=445 dport=49182 [ASSURED] mark=0 use=2
tcp      6 431675 ESTABLISHED src=192.168.111.101 dst=157.56.52.46 sport=54544 dport=40025 src=157.56.52.46 dst=173.180.45.4 sport=40025 dport=54544 [ASSURED] mark=0 use=2
tcp      6 79 TIME_WAIT src=192.168.111.106 dst=207.167.198.20 sport=57536 dport=110 src=207.167.198.20 dst=173.180.45.4 sport=110 dport=57536 [ASSURED] mark=0 use=2
```

Yes, I can see the connections there.

> **Doug S said:**
> 
Edit: I installed netstat-nat and tried it. It seems to be working fine for me. Example (content edited, as readers do not need to know my daughters connections, mine are O.K.):```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat-nat[/COLOR]
Proto NATed Address                  Destination Address            State
tcp   doug-xps2.smythies.com:65126   205.250.85.72:http             TIME_WAIT
tcp   doug-xps2.smythies.com:65171   202.177.216.233:https          TIME_WAIT
tcp   doug-xps2.smythies.com:54544   157.56.52.46:40025             ESTABLISHED
tcp   doug-xps2.smythies.com:65152   pe-in-f95.1e100.net:http       TIME_WAIT
```

Correct me if I'm wrong, but it looks like those are connections from behind nat to the Internet. I can see those fine, the problem is with the opposite: connections from the Internet to a server behind nat. netstat-nat doesn't display those.

> **Hadaka said:**
> Hi, try inserting a space,,
```
netstat -nat
```
[B]netstat -nat
..........^
[/B]

netstat and netstat-nat are two different utilities. You are suggesting using netstat with -nat switches instead of netstat-nat, which would display only connections made to the Ubuntu box directly.

---

### Post by Doug S on 2014-11-19
> **karaluh said:**
> Correct me if I'm wrong, but it looks like those are connections from behind nat to the Internet. I can see those fine, the problem is with the opposite: connections from the Internet to a server behind nat. netstat-nat doesn't display those.Oh, I missed that detail in your original post. I can test that scenario, but it will take awhile...

Edit: I tested an incoming connection where I had a DNAT rule to forward to an internal test server. netstat-nat worked fine for me in this situation.```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat-nat -D -n[/COLOR]
Proto NATed Address                  Destination Address            State
tcp   173.180.45.3:39425             192.168.111.112:22             ESTABLISHED
tcp   173.180.45.3:39424             192.168.111.112:22             TIME_WAIT
``````
doug@doug-64:~$ [COLOR=#ff0000]sudo iptables -t nat -v -x -n -L[/COLOR]
Chain PREROUTING (policy ACCEPT 876 packets, 74414 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       2      120 [COLOR=#ff0000]DNAT[/COLOR]       all  --  *      *       173.180.45.3         173.180.45.4         to:192.168.111.112
...
```

---

### Post by karaluh on 2014-11-21
> **Doug S said:**
> Oh, I missed that detail in your original post. I can test that scenario, but it will take awhile...

Edit: I tested an incoming connection where I had a DNAT rule to forward to an internal test server. netstat-nat worked fine for me in this situation.```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat-nat -D -n[/COLOR]
Proto NATed Address                  Destination Address            State
tcp   173.180.45.3:39425             192.168.111.112:22             ESTABLISHED
tcp   173.180.45.3:39424             192.168.111.112:22             TIME_WAIT
```


I'm glad it works for you :) When I issue the above command I get empty list.

> **Doug S said:**
> 
```
doug@doug-64:~$ [COLOR=#ff0000]sudo iptables -t nat -v -x -n -L[/COLOR]
Chain PREROUTING (policy ACCEPT 876 packets, 74414 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       2      120 [COLOR=#ff0000]DNAT[/COLOR]       all  --  *      *       173.180.45.3         173.180.45.4         to:192.168.111.112
...
```

Yup, my rules are also listed here. I can also see the connections on the target servers (I have www and rdp redirected to two different boxes). Any idea why netstat-nat doesn't display them? I see you're using Precise, I'm using Lucid. Could that be the reason? I'll try to install the package from Precise, hopefully it's not a dependency hell. Thank you for investigating the issue.

[COLOR="#FF0000"]EDIT:[/COLOR] Yup, that was the case, installing the package from precise solves the issue.

---

### Post by Doug S on 2014-11-21
Glad you got it sorted out.

---

