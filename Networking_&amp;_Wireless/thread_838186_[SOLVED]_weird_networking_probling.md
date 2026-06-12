---
title: "[SOLVED] weird networking probling"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by oli_ on 2008-06-23
My lan looks like this:
192.168.1.1 = FritzBox - my router and internet gateway, also does dhcp, ips are static (remembers mac addresses)
192.168.1.26 = small server, running ubuntu server
192.168.1.20 = desktop computer, running kubuntu

on the server i run several services, such as webserver, printserver, fileserver, etc.. they all work fine. Now i installed munin (the system graph tool) on the server, which works also fine - at least for the server. i also installed the munin-node on the desktop computer, that was when i discovered my problem: the server doesnt seem to be able to connect to the desktop computer (yes, munin is confed correctly so that it should work).
So, remember the ip addresses i wrote above and look at this:

```
oli@server:~$ ping -c4 192.168.1.20
PING 192.168.1.20 (192.168.1.20) 56(84) bytes of data.
64 bytes from 192.168.1.20: icmp_seq=1 ttl=64 time=0.431 ms
64 bytes from 192.168.1.20: icmp_seq=2 ttl=64 time=0.554 ms
64 bytes from 192.168.1.20: icmp_seq=3 ttl=64 time=0.585 ms
64 bytes from 192.168.1.20: icmp_seq=4 ttl=64 time=0.543 ms

--- 192.168.1.20 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.431/0.528/0.585/0.060 ms
```

ok, looks fine, now this:
```
oli@server:~$ traceroute -m6 192.168.1.20
traceroute to 192.168.1.20 (192.168.1.20), 6 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
```
hm, "funny" - normally it should go through 192.168.1.1 (router) to 192.168.1.20 (desktop).


Since the services work fine i tried it the other way round - from the desktop:
```
oli@Oli-Desktop:~$ traceroute 192.168.1.26
traceroute to 192.168.1.26 (192.168.1.26), 30 hops max, 40 byte packets
 1  oli.homeunix.net (192.168.1.26)  1.309 ms  1.269 ms  1.256 ms
```
ok works, but shouldnt be my router in that list?
I didnt touch iptables on both of hosts (or installed firewalls which would do that), only changes i made for the routing is an entry in the /etc/hosts for the desktop computer:
192.168.1.26    oli.homeunix.net

any ideas?
ps: my only problem atm is that munin doesnt work since it cant connect to the desktop, which isnt too important. But i'd like to understand whats going on here...

---

### Post by lloyd_b on 2008-06-23
> **oli_ said:**
> My lan looks like this:
192.168.1.1 = FritzBox - my router and internet gateway, also does dhcp, ips are static (remembers mac addresses)
192.168.1.26 = small server, running ubuntu server
192.168.1.20 = desktop computer, running kubuntu

on the server i run several services, such as webserver, printserver, fileserver, etc.. they all work fine. Now i installed munin (the system graph tool) on the server, which works also fine - at least for the server. i also installed the munin-node on the desktop computer, that was when i discovered my problem: the server doesnt seem to be able to connect to the desktop computer (yes, munin is confed correctly so that it should work).
So, remember the ip addresses i wrote above and look at this:

```
oli@server:~$ ping -c4 192.168.1.20
PING 192.168.1.20 (192.168.1.20) 56(84) bytes of data.
64 bytes from 192.168.1.20: icmp_seq=1 ttl=64 time=0.431 ms
64 bytes from 192.168.1.20: icmp_seq=2 ttl=64 time=0.554 ms
64 bytes from 192.168.1.20: icmp_seq=3 ttl=64 time=0.585 ms
64 bytes from 192.168.1.20: icmp_seq=4 ttl=64 time=0.543 ms

--- 192.168.1.20 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.431/0.528/0.585/0.060 ms
```

ok, looks fine, now this:
```
oli@server:~$ traceroute -m6 192.168.1.20
traceroute to 192.168.1.20 (192.168.1.20), 6 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
```
hm, "funny" - normally it should go through 192.168.1.1 (router) to 192.168.1.20 (desktop).


Since the services work fine i tried it the other way round - from the desktop:
```
oli@Oli-Desktop:~$ traceroute 192.168.1.26
traceroute to 192.168.1.26 (192.168.1.26), 30 hops max, 40 byte packets
 1  oli.homeunix.net (192.168.1.26)  1.309 ms  1.269 ms  1.256 ms
```
ok works, but shouldnt be my router in that list?
I didnt touch iptables on both of hosts (or installed firewalls which would do that), only changes i made for the routing is an entry in the /etc/hosts for the desktop computer:
192.168.1.26    oli.homeunix.net

any ideas?
ps: my only problem atm is that munin doesnt work since it cant connect to the desktop, which isnt too important. But i'd like to understand whats going on here...

First off, your router may or may not show in that traceroute.  Many home routers act like simple switches when routing between computers on the local network.  It depends on the specific router...

Second - You've probably got the port used by traceroute's probe packets blocked in the firewall on 192.168.1.20.  Try "traceroute -I -m6 192.168.1.20" to force it to use the "ICMP Echo Request" packets that are used by "ping", since you know that the machine will respond to those.

Lloyd B.

---

### Post by oli_ on 2008-06-25
Thanks for the tip, traceroute really does work with those params, but that doesnt solve my problem :( i still cant access the desktop computer from the server through other services (ssh or telnet how munin does it)

i was curious about the iptables stuff though and was surprised that there seems to be confed quite a bit even though i never touched it - unfortunately i can't read it (dont understand what that stuff means)
```
oli@Oli-Desktop:~$ sudo iptables -L
[sudo] password for oli:
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  fritz.box            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  fritz.box            anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             192.168.1.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  noname               fritz.box           tcp dpt:domain
ACCEPT     udp  --  noname               fritz.box           udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
```


i see a lot of DROPs in the input part. does this have anything to do with it?

**Edit:** I did install a firewall once (firestarter) - on the desktop, but removed it again. is it possible that it created these entries and didnt clean up when i removed it?
iptables of the server look (a tiny) bit simpler:
```
oli@server:~$ sudo iptables -L
[sudo] password for oli:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by oli_ on 2008-06-25
Ok, PROBLEM SOLVED

apparently firestarter really created rules and didnt remove them upon removal.
i reset the iptables -> (it's german [http://www.linuxforen.de/forums/archive/index.php/t-225681.html](http://www.linuxforen.de/forums/archive/index.php/t-225681.html)), its just a few iptables cmds as described there:

```
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X
iptables -t nat -X
iptables -t mangle -X
```
now iptables -L looks exactly like on the server and everything works again. Stupid me :(

---

