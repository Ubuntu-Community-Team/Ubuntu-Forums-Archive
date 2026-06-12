---
title: "Custom Built router causes odd connection problems to certain sites"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by Kirk_Steuber on 2014-05-22
I have built my own router and it has intermittent problems where certain computers have their connection reset when connecting to certain websites. In the course of trying to debug this, I have only become more confused. To clarify, the problem occurs only intermittently and affects different websites on different computers. Additionally, the problem does not seem to occur across browsers, even on the same computer.

The closest to a consistent problem is on my roommate's computer, who usually cannot access tumblr using Chrome. To troubleshoot, I ran wireshark, which shows that her connection starts properly, receives the appropriate syn/ack, but after the local computer transmits the request, the server sends a window update followed by a tcp reset. 

Next, I went to ping tumbr (from the router) and discovered that the ping takes much too long; likely related to the root of the problem. However, pinging the ip address directly does not cause it to take a long time as illustrated below. 
```
> time ping -c 1 tumblr.com
PING tumblr.com (66.6.41.20) 56(84) bytes of data.
64 bytes from 66.6.41.20: icmp_req=1 ttl=54 time=91.5 ms


--- tumblr.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 91.535/91.535/91.535/0.000 ms


real    0m15.120s
user    0m0.004s
sys     0m0.000s
```
```
> time ping -c 1 66.6.41.20
PING 66.6.41.20 (66.6.41.20) 56(84) bytes of data.
64 bytes from 66.6.4+1.20: icmp_req=1 ttl=54 time=91.3 ms


--- 66.6.41.20 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 91.375/91.375/91.375/0.000 ms


real    0m0.095s
user    0m0.004s
sys     0m0.000s
```
The long pause occurs AFTER the "PING tumblr.com (66.6.41.20) 56(84) bytes of data." line and if I increase the count argument, it occurs before every "64 bytes from..." line. This delay is not experienced if I ping from windows computers but is experienced from other Ubuntu machines. 

I would much appreciate it if anyone could point me in the right direction, even just toward the next troubleshooting step since I do not know where to go from here. 

To help get a picture of the situation, these are the main things the router runs:
Software RAID via mdadm
Apache with PHP
Samba
dnsmasq
Dynamic DNS server via inadyn
OpenVPN

This is my iptables configuration. eth1 is my external interface and eth2 is my internal interface. The local network uses 192.168.42.0/24 and the VPN uses 192.168.44.0/24.
```
Chain INPUT (policy DROP 5265 packets, 753K bytes)
 pkts bytes target     prot opt in     out     source               destination
 670K   96M ACCEPT     all  --  eth2   any     anywhere             anywhere
44979   26M ACCEPT     all  --  eth1   any     anywhere             anywhere             ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere             udp dpt:openvpn
  887  377K ACCEPT     icmp --  any    any     anywhere             anywhere
 389K  172M ACCEPT     all  --  lo     any     localhost            localhost
    0     0 ACCEPT     all  --  tun0   any     192.168.44.0/24      anywhere
   26  1472 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:http
    9   436 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:https


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 649K   72M ACCEPT     all  --  eth2   any     192.168.42.0/24      anywhere
 968K 1291M ACCEPT     all  --  eth1   eth2    anywhere             192.168.42.0/24      ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  tun0   any     192.168.44.0/24      anywhere


Chain OUTPUT (policy ACCEPT 1111K packets, 413M bytes)
 pkts bytes target     prot opt in     out     source               destination
```

Thanks in advance!

---

### Post by Doug S on 2014-05-22
Hi and welcome to Ubuntu forums.

Your lo traffic seems unusually high, but I do not have a suggestion as to why.

What time do name server lookups take? Example:```
doug@s15:~/temp$ time nslookup tumblr.com
Server:         192.168.111.1
Address:        192.168.111.1#53

Non-authoritative answer:
Name:   tumblr.com
Address: 66.6.43.20


real    0m0.130s
user    0m0.007s
sys     0m0.006s
```Could you please post your entire iptables. Suggest:```
sudo iptables -t nat -v -x -n -L
sudo iptables -v -x -n -L
```

---

### Post by Kirk_Steuber on 2014-05-22
Name servers seem quick enough:
```
 > time nslookup tumblr.com
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
Name:   tumblr.com
Address: 66.6.43.20


real    0m0.069s
user    0m0.016s
sys     0m0.000s
```

Here is the rest of my iptables:
```
 > iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 57971 packets, 4510389 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain INPUT (policy ACCEPT 20629 packets, 1737202 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 42771 packets, 2774191 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 24757 packets, 1545375 bytes)
    pkts      bytes target     prot opt in     out     source               destination
   45776  3006411 MASQUERADE  all  --  *      eth1    0.0.0.0/0            0.0.0.0/0


```

```
> iptables -v -x -n -L
Chain INPUT (policy DROP 8402 packets, 1169475 bytes)
    pkts      bytes target     prot opt in     out     source               destination
 8452340 908042523 ACCEPT     all  --  eth2   *       0.0.0.0/0            0.0.0.0/0
   52729 27472361 ACCEPT     all  --  eth1   *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:1194
    1816   908387 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
  546606 187737507 ACCEPT     all  --  lo     *       127.0.0.1            127.0.0.1
       0        0 ACCEPT     all  --  tun0   *       192.168.44.0/24      0.0.0.0/0
      45     2520 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
      18      976 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
 1734036 153904309 ACCEPT     all  --  eth2   *       192.168.42.0/24      0.0.0.0/0
 2661689 3608096693 ACCEPT     all  --  eth1   eth2    0.0.0.0/0            192.168.42.0/24      ctstate RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  tun0   *       192.168.44.0/24      0.0.0.0/0

Chain OUTPUT (policy ACCEPT 30038835 packets, 40098590535 bytes)
    pkts      bytes target     prot opt in     out     source               destination


```

You are right about the high lo traffic, I hadn't really noticed that. I think I will try to get some log info to see what it is. Not really sure how to set that up, but I will google it.

---

### Post by Doug S on 2014-05-23
I'm do not have any good idea what the problem is. Someone else might have a suggestion.
For observing what is going on on the lo, have a look with wireshark. I use tcpdump myself, example:```
doug@doug-64:~$ [COLOR=#ff0000]sudo tcpdump -n -nn -tttt -i lo[/COLOR]
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on lo, link-type EN10MB (Ethernet), capture size 65535 bytes
2014-05-23 07:21:26.932788 IP 127.0.0.1.59989 > 127.0.0.1.631: Flags [S], seq 2755579302, win 32792, options [mss 16396,sackOK,TS val 896199349 ecr 0,nop,wscale 6], length 0
2014-05-23 07:21:26.932812 IP 127.0.0.1.631 > 127.0.0.1.59989: Flags [R.], seq 0, ack 2755579303, win 0, length 0
2014-05-23 07:34:27.646828 IP 127.0.0.1.59990 > 127.0.0.1.631: Flags [S], seq 1494381694, win 32792, options [mss 16396,sackOK,TS val 896394528 ecr 0,nop,wscale 6], length 0
2014-05-23 07:34:27.646850 IP 127.0.0.1.631 > 127.0.0.1.59990: Flags [R.], seq 0, ack 1494381695, win 0, length 0
2014-05-23 07:47:28.417286 IP 127.0.0.1.59991 > 127.0.0.1.631: Flags [S], seq 2795214930, win 32792, options [mss 16396,sackOK,TS val 896589720 ecr 0,nop,wscale 6], length 0
2014-05-23 07:47:28.417337 IP 127.0.0.1.631 > 127.0.0.1.59991: Flags [R.], seq 0, ack 2795214931, win 0, length 0
2014-05-23 08:00:29.198240 IP 127.0.0.1.59992 > 127.0.0.1.631: Flags [S], seq 1852867157, win 32792, options [mss 16396,sackOK,TS val 896784916 ecr 0,nop,wscale 6], length 0
2014-05-23 08:00:29.198261 IP 127.0.0.1.631 > 127.0.0.1.59992: Flags [R.], seq 0, ack 1852867158, win 0, length 0
2014-05-23 08:13:29.953738 IP 127.0.0.1.59993 > 127.0.0.1.631: Flags [S], seq 2685676636, win 32792, options [mss 16396,sackOK,TS val 896980105 ecr 0,nop,wscale 6], length 0
2014-05-23 08:13:29.953759 IP 127.0.0.1.631 > 127.0.0.1.59993: Flags [R.], seq 0, ack 2685676637, win 0, length 0
2014-05-23 08:26:30.734962 IP 127.0.0.1.59994 > 127.0.0.1.631: Flags [S], seq 2182737924, win 32792, options [mss 16396,sackOK,TS val 897175300 ecr 0,nop,wscale 6], length 0
2014-05-23 08:26:30.734986 IP 127.0.0.1.631 > 127.0.0.1.59994: Flags [R.], seq 0, ack 2182737925, win 0, length 0
^C
12 packets captured
24 packets received by filter
0 packets dropped by kernel
```

---

### Post by Kirk_Steuber on 2014-05-23
I have used wireshark to look at this. The part that I believe to be the relevant section looks like this:
```
12:36:21.878823 IP 192.168.42.17.65318 > 66.6.41.20.http: Flags [S], seq 3366735154, win 8192, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
12:36:21.964838 IP 66.6.41.20.http > 192.168.42.17.65318: Flags [S.], seq 1724582626, ack 3366735155, win 14600, options [mss 1460,nop,nop,sackOK,nop,wscale 9], length 0
12:36:22.084106 IP 192.168.42.17.65319 > 66.6.41.20.http: Flags [S], seq 3206054628, win 8192, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
12:36:22.087975 IP 192.168.42.17.65318 > 66.6.41.20.http: Flags [.], ack 1, win 256, length 0
12:36:22.089082 IP 192.168.42.17.65318 > 66.6.41.20.http: Flags [.], seq 1:557, ack 1, win 256, length 556
12:36:22.089151 IP 192.168.42.17.65318 > 66.6.41.20.http: Flags [P.], seq 557:979, ack 1, win 256, length 422
12:36:22.155707 IP 192.168.42.17.65287 > a23-208-235-46.deploy.static.akamaitechnologies.com.http: Flags [.], seq 884639403:884639404, ack 2701453309, win 256, length 1
12:36:22.167700 IP 66.6.41.20.http > 192.168.42.17.65319: Flags [S.], seq 1758090136, ack 3206054629, win 14600, options [mss 1460,nop,nop,sackOK,nop,wscale 9], length 0
12:36:22.171338 IP a23-208-235-46.deploy.static.akamaitechnologies.com.http > 192.168.42.17.65287: Flags [.], ack 1, win 8372, options [nop,nop,sack 1 {0:1}], length 0
12:36:22.171822 IP 192.168.42.17.65319 > 66.6.41.20.http: Flags [.], ack 1, win 256, length 0
12:36:22.176840 IP 66.6.41.20.http > 192.168.42.17.65318: Flags [.], ack 1, win 29, options [nop,nop,sack 1 {557:979}], length 0
12:36:22.177758 IP 66.6.41.20.http > 192.168.42.17.65318: Flags [R], seq 1724582627, win 0, length 0
```

I just discovered this thread: [http://ubuntuforums.org/showthread.php?t=1357310](http://ubuntuforums.org/showthread.php?t=1357310)
I have confirmed that the response is quick for ping -n. Perhaps the problem is that my router is causing some sort of problem for reverse DNS lookups. Not sure if that could even cause the problems that I am experiencing, but I am getting desperate because I have had this problem for a year now and feel no closer to tracking it down.

I am a bit busy right now, but I will try to look into it this weekend.

---

### Post by Doug S on 2014-05-23
Good find on that link you provided. On my system, using tcpdump, I can observe the reverse dns lookups for each ping packet. So what do you get for a reverse lookup by itself?```
doug@s15:~/temp$ [COLOR=#ff0000]time nslookup 66.6.43.20[/COLOR]
Server:         192.168.111.1
Address:        192.168.111.1#53

** server can't find 20.43.6.66.in-addr.arpa: NXDOMAIN


[COLOR=#ff0000]real    0m0.045s[/COLOR]
user    0m0.007s
sys     0m0.003s
```

---

### Post by Kirk_Steuber on 2014-05-23
Time is quick, but it fails
```
> time nslookup 66.6.43.20
Server:        127.0.0.1
Address:    127.0.0.1#53

** server can't find 20.43.6.66.in-addr.arpa: SERVFAIL


real    0m0.173s
user    0m0.004s
sys    0m0.004s

```

Interetingly though, some of tumblr's IPs seem to give different errors when I try to look them up. Not sure what this means.

```
> time nslookup 66.6.41.20
Server:        127.0.0.1
Address:    127.0.0.1#53

** server can't find 20.41.6.66.in-addr.arpa: FORMERR


real    0m0.096s
user    0m0.004s
sys    0m0.000s

```

Does my quick reverse dns (failure) mean that this is not what is causing things to hang in ping?

---

### Post by Kirk_Steuber on 2014-05-24
I have been trying some troubleshooting more. I really thought dnsmasq was somehow related, but I turned it off and experienced the same problem, which seems to confirm that it is not. I captured a packet trace of the ping problem. This shows the problem ping of tumblr, then the successful ping of google:
```
> tcpdump -n -r tumblr_ping_problem
reading from file tumblr_ping_problem, link-type EN10MB (Ethernet)
13:54:52.575932 IP 71.237.222.143.37483 > 75.75.75.75.53: 45951+ A? tumblr.com. (28)
13:54:52.575971 IP 71.237.222.143.37483 > 75.75.76.76.53: 45951+ A? tumblr.com. (28)
13:54:52.591325 IP 75.75.75.75.53 > 71.237.222.143.37483: 45951 2/0/0 A 66.6.44.20, A 66.6.43.20 (60)
13:54:52.591868 IP 71.237.222.143 > 66.6.44.20: ICMP echo request, id 17111, seq 1, length 64
13:54:52.630759 IP 75.75.76.76.53 > 71.237.222.143.37483: 45951 2/0/0 A 66.6.41.20, A 66.6.42.20 (60)
13:54:52.630806 IP 71.237.222.143 > 75.75.76.76: ICMP 71.237.222.143 udp port 37483 unreachable, length 96
13:54:52.677034 IP 66.6.44.20 > 71.237.222.143: ICMP echo reply, id 17111, seq 1, length 64
13:54:52.677452 IP 71.237.222.143.46253 > 75.75.75.75.53: 36260+ PTR? 20.44.6.66.in-addr.arpa. (41)
13:54:52.688368 IP 75.75.75.75.53 > 71.237.222.143.46253: 36260 ServFail 0/0/0 (41)
13:54:52.688456 IP 71.237.222.143.46253 > 75.75.76.76.53: 36260+ [b2&3=0x182] PTR? 20.44.6.66.in-addr.arpa. (41)
13:54:52.688498 IP 71.237.222.143.46253 > 75.75.75.75.53: 36260+ [b2&3=0x182] PTR? 20.44.6.66.in-addr.arpa. (41)
13:54:52.702150 IP 75.75.75.75.53 > 71.237.222.143.46253: 36260 FormErr [0q] 0/0/0 (12)
13:54:52.738842 IP 75.75.76.76.53 > 71.237.222.143.46253: 36260 FormErr [0q] 0/0/0 (12)
13:54:52.738892 IP 71.237.222.143 > 75.75.76.76: ICMP 71.237.222.143 udp port 46253 unreachable, length 48
13:54:52.790196 IP 71.237.222.143.55975 > 75.75.75.75.53: 48167+ A? accounts.google.com. (37)
13:54:52.806234 IP 75.75.75.75.53 > 71.237.222.143.55975: 48167 2/0/0 CNAME accounts.l.google.com., A 74.125.28.84 (78)
13:54:52.898724 IP 71.237.222.143.8487 > 75.75.75.75.53: 13185+ A? www.googleapis.com. (36)
13:54:52.910022 IP 75.75.75.75.53 > 71.237.222.143.8487: 13185 2/0/0 CNAME googleapis.l.google.com., A 74.125.28.95 (86)
13:54:57.679992 IP 71.237.222.143.27027 > 75.75.75.75.53: 63525+ PTR? 20.44.6.66.in-addr.arpa. (41)
13:54:57.697003 IP 75.75.75.75.53 > 71.237.222.143.27027: 63525 ServFail 0/0/0 (41)
13:54:57.697197 IP 71.237.222.143.27027 > 75.75.76.76.53: 63525+ [b2&3=0x182] PTR? 20.44.6.66.in-addr.arpa. (41)
13:54:57.697216 IP 71.237.222.143.27027 > 75.75.75.75.53: 63525+ [b2&3=0x182] PTR? 20.44.6.66.in-addr.arpa. (41)
13:54:57.710812 IP 75.75.75.75.53 > 71.237.222.143.27027: 63525 FormErr [0q] 0/0/0 (12)
13:54:57.747325 IP 75.75.76.76.53 > 71.237.222.143.27027: 63525 FormErr [0q] 0/0/0 (12)
13:54:57.747399 IP 71.237.222.143 > 75.75.76.76: ICMP 71.237.222.143 udp port 27027 unreachable, length 48
13:55:02.780046 IP 71.237.222.143.5353 > 224.0.0.251.5353: 0 PTR (QM)? 20.44.6.66.in-addr.arpa. (41)
13:55:03.781815 IP 71.237.222.143.5353 > 224.0.0.251.5353: 0 PTR (QM)? 20.44.6.66.in-addr.arpa. (41)
13:55:03.977455 IP 71.237.222.143.54059 > 173.194.79.125.5222: Flags [.], seq 524802121:524802122, ack 3124557591, win 16404, length 1
13:55:04.000041 IP 173.194.79.125.5222 > 71.237.222.143.54059: Flags [.], ack 1, win 1343, options [nop,nop,sack 1 {0:1}], length 0
13:55:05.784509 IP 71.237.222.143.5353 > 224.0.0.251.5353: 0 PTR (QM)? 20.44.6.66.in-addr.arpa. (41)
13:55:07.684051 IP 71.237.222.143.17240 > 75.75.75.75.53: 60813+ A? google.com. (28)
13:55:07.694719 IP 75.75.75.75.53 > 71.237.222.143.17240: 60813 11/0/0 A 173.194.33.102, A 173.194.33.98, A 173.194.33.99, A 173.194.33.104, A 173.194.33.100, A 173.194.33.97, A 173.194.33.110, A 173.194.33.101, A 173.194.33.105, A 173.194.33.96, A 173.194.33.103 (204)
13:55:07.695095 IP 71.237.222.143 > 173.194.33.102: ICMP echo request, id 17582, seq 1, length 64
13:55:07.709591 IP 173.194.33.102 > 71.237.222.143: ICMP echo reply, id 17582, seq 1, length 64
13:55:07.710107 IP 71.237.222.143.5867 > 75.75.75.75.53: 57495+ PTR? 102.33.194.173.in-addr.arpa. (45)
13:55:07.720669 IP 75.75.75.75.53 > 71.237.222.143.5867: 57495 1/0/0 PTR sea09s16-in-f6.1e100.net. (83)
```

I am more familiar with wireshark than tcpdump, so I find what I posted to be a bit confusing. What I can see in wireshark is this:
DNS query made to 2 DNS servers regarding tumblr.com
DNS response from both servers
ICMP Destination Unreachable (port unreachable) sent from my router to one of the DNS servers
ICMP ping request and response
Reverse DNS query on tumblr's IP to one DNS server, response is Server Failure
Reverse DNS query to both DNS servers, response from both is Format Error
ICMP Destination Unreachable (port unreachable) sent from my router to same DNS server it was sent to before.
Repeat of all three reverse DNS queries, responses, and ICMP message.
Three multicast DNS queries; no response
DNS query and response regarding google.com
ICMP ping request and response
Reverse DNS query and response on google's IP

I cannot explain why these things happen the way they do. Particularly, why my server sends a destination unreachable message. Also, why the same request first gets a server error, then a format error. It would be useful if someone could replicate my results so I know what problem I am trying to solve. 

If anyone can suggest the next troubleshooting step from here, I would be very grateful.

---

### Post by Doug S on 2014-05-25
You definitely have some weirdness going on.
Additionally, I am finding it a little difficult to correlate your tcpdump information to your original post, since I do not observe a 15 second gap or delay or whatever.

You mention "Dynamic DNS server via inadyn". Can you try without it running?

Did you ever look into why you have so much lo traffic?

It is odd to send DNS requests to two servers at the same time. And notice the google lookup request only sent one request to one server.

The second reverse lookup after the ServFail response, doesn't seems right, hence the FormErr response. Looking back over my own traffic for the last couple of months I do see that particular version of a FormErr, but it quite rare and not initiated by my system.

Your broadcast DNS stuff on port 5353 is odd, and I wonder if it is due to the inadyn thing mentioned above. As a side note, I have filter rules in my iptables rule set to prevent spewing of such packets onto internet.

I suspect, but am not sure, that the "port unreachable" response is because the request was already filled from the other name server, and your system has already forgotten about the connection. However, things are a mess in that area, so who knows.

You asked for an example of the same thing. First for "ping -c 1 tumblr.com"```
doug@doug-64:~$ sudo tcpdump -n -tttt -i eth1
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
2014-05-25 06:55:40.406244 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2014-05-25 06:55:42.603909 IP 173.180.45.4.32024 > 192.48.79.30.53: 14827 [1au] A? tumblr.com. (39)
2014-05-25 06:55:42.763751 IP 192.48.79.30.53 > 173.180.45.4.32024: 14827- 0/12/7 (833)
2014-05-25 06:55:42.764306 IP 173.180.45.4.43200 > 204.74.109.1.53: 23074 [1au] A? tumblr.com. (39)
2014-05-25 06:55:42.818342 IP 204.74.109.1.53 > 173.180.45.4.43200: 23074*- 2/10/1 A 66.6.41.20, A 66.6.44.20 (325)
2014-05-25 06:55:42.818983 IP 173.180.45.4 > 66.6.44.20: ICMP echo request, id 24474, seq 1, length 64
2014-05-25 06:55:42.912415 IP 66.6.44.20 > 173.180.45.4: ICMP echo reply, id 24474, seq 1, length 64
2014-05-25 06:55:42.912994 IP 173.180.45.4.56006 > 208.78.71.3.53: 64030 [1au] PTR? 20.44.6.66.in-addr.arpa. (52)
2014-05-25 06:55:42.947776 IP 208.78.71.3.53 > 173.180.45.4.56006: 64030 NXDomain*- 0/6/1 (889)
```

Second for ping -c 1 google.com```
doug@doug-64:~$ sudo tcpdump -n -tttt -i eth1
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
2014-05-25 06:58:35.506921 IP 173.180.45.4.56738 > 216.239.36.10.53: 4600 [1au] A? google.com. (39)
2014-05-25 06:58:35.547528 IP 216.239.36.10.53 > 173.180.45.4.56738: 4600*- 11/0/0 A 173.194.33.135, A 173.194.33.131, A 173.194.33.132, A 173.194.33.137, A 173.194.33.134, A 173.194.33.129, A 173.194.33.130, A 173.194.33.142, A 173.194.33.133, A 173.194.33.128, A 173.194.33.136 (204)
2014-05-25 06:58:35.548105 IP 173.180.45.4 > 173.194.33.142: ICMP echo request, id 24477, seq 1, length 64
2014-05-25 06:58:35.581238 IP 173.194.33.142 > 173.180.45.4: ICMP echo reply, id 24477, seq 1, length 64
2014-05-25 06:58:35.581923 IP 173.180.45.4.12184 > 203.119.86.101.53: 8488 [1au] PTR? 142.33.194.173.in-addr.arpa. (56)
2014-05-25 06:58:35.720055 IP 203.119.86.101.53 > 173.180.45.4.12184: 8488- 0/10/1 (400)
2014-05-25 06:58:35.720437 IP 173.180.45.4.19978 > 199.212.0.63.53: 21454 [1au] PTR? 142.33.194.173.in-addr.arpa. (56)
2014-05-25 06:58:35.832662 IP 199.212.0.63.53 > 173.180.45.4.19978: 21454- 0/6/1 (358)
2014-05-25 06:58:35.833020 IP 173.180.45.4.11540 > 216.239.36.10.53: 37738 [1au] PTR? 142.33.194.173.in-addr.arpa. (56)
2014-05-25 06:58:35.873496 IP 216.239.36.10.53 > 173.180.45.4.11540: 37738*- 1/0/0 PTR sea09s17-in-f14.1e100.net. (84)
```

---

### Post by Kirk_Steuber on 2014-05-26
I tried it without inadyn running; no change.
I'm not sure what is causing all the lo traffic or how to even figure it out. I have tried stopping services and seeing if the traffic decreases with no success. There is one thing that I have not tried and need to wait a bit before I can do so. 
To make a long story short, I am doing a somewhat unusual backup. To do it I am compressing 1.2TB of data and transferring a drive on another computer via a mounted CIFS drive. The compression is taking a long time (many days). I don't know the specifics, but maybe a mounted network drive uses lo at some point?

I do not really understand what is wrong with the second set of reverse lookups. I can see the [b2&3=0x182] difference in tcpdump, but I don't see what it means. In wireshark I cannot find any difference.

I agree with your analysis that the unreachable is because the request was already filled. That seems reasonable. 

Also, any idea why you get an NXDOMAIN response to your reverse lookup request? If the DNS query succeeds, shouldn't the reverse query succeed as well?

Thanks!

---

### Post by Doug S on 2014-05-26
> **Kirk_Steuber said:**
> Also, any idea why you get an NXDOMAIN response to your reverse lookup request? If the DNS query succeeds, shouldn't the reverse query succeed as well?Only if the reverse zone has been setup, which and this case, apparently it has not.

---

### Post by Kirk_Steuber on 2014-05-30
So because this problem is proving so annoying and so hard to track down, I plan to take somewhat drastic steps. I plan to back up the disk, reformat and reinstall Ubuntu, then reinstall each system, testing for problems after each step. It seems like surely this will allow me to fix the problem. I think it is also possible that the problem is due to something I installed at some point and am no longer using or some bad data resulting from a power failure.

The only issue is actually checking for the problem between installation steps. The problem that I actually want to fix is the failure of random websites to load. This, however, is extrememly hard to test for since the problem is intermittant. The problem pinging tumblr is the only testable thing I have found that might be related. I am unsure that they actually result from the same problem though, since other websites including Google have had intermittant problems and tumblr is the first thing I have found with this ping problem. 

Any ideas for how to more reliably test for this problem? Thanks!

---

### Post by Kirk_Steuber on 2014-05-31
Well I reformatted to Ubuntu Server 13.10. I installed no extras. The problem still occurs, but now it is intermittant. I tried with two network cards, a PCIe Realtek and a PCI Intel. I plugged another machine into the modem and it experienced no problems. 

My only remaining ideas for fixing it are to replace the motherboard and maybe even the processor. They seem like the last things I haven't been eliminated as suspects. I do not particularly want to do this as it is a bit pricy. Does anyone have any other ideas? Does it seem like the motherboard is at fault? I would really appriciate any input.

---

### Post by Kirk_Steuber on 2014-06-01
Hmm. I believe I was incorrect in my previous analysis. To test that it was not a connection problem, I used ping -a on a windows machine. I thought that before ping -a previously demonstrated the same problem, but now I am not sure. I used the windows machine because my only other linux machine does not have a functional wired network card. Now, having connected a spare router while I work on my custom one, I tried it on my other linux box and got the same problem. This leads me to believe that this odd delay is a result of some network problem. 

I believe that the website loading problem does not occur on the replacement router. I therefore conclude that the ping problem is unfortunately not related to the website loading problem. I guess I will try to create the router from scratch again and see if the problem persists. That will at least tell me if the problem was some weird fluke or if there is something wrong with my setup. 

As before, any ideas are very welcome. I would appriciate any help.

---

### Post by Kirk_Steuber on 2014-06-07
Well, I think I fixed it. I did two things and I am not sure what fixed the problem, but I have my suspicions. As mentioned, I decided to reformat the router and start from the ground up. I ended up sort of messing around, trying different distros, different install settings, etc. During this process I noticed that that when installing using the Intel NIC, the timezone was autodetected whereas when installing with the Realtek NIC it was not. This made me think. It would not be the first time that a Realtek NIC didn't work on Linux properly (it would be the third in fact). I therefore bought another Intel NIC and reinstalled. I am not totally sure if the reinstall or removing the Realtek NIC solved the problem, but it does seem to be solved.

I have officially sworn off Realtek network devices and suggest that anyone else using Linux do the same. Maybe I am missing something, but they just do not seem to work for me (even using the official driver on their website). 

Thank you for your help Doug.

---

