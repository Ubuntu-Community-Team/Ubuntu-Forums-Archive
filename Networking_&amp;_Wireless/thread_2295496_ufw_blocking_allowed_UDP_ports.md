---
title: "ufw blocking allowed UDP ports"
date: 2015-09-19
forum: Networking &amp; Wireless
---

### Post by Daniel1975m on 2015-09-19
I have the following ufw settings (for plex).

[COLOR=#000000]```
[/COLOR]
$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
25/tcp                     ALLOW IN    Anywhere
465/tcp                    ALLOW IN    Anywhere
587/tcp                    ALLOW IN    Anywhere
137,138/udp                ALLOW IN    Anywhere
139,445/tcp                ALLOW IN    Anywhere
32469/tcp                  ALLOW IN    Anywhere
**1900/udp                   ALLOW IN    Anywhere**
32410,32412,32413,32414/udp ALLOW IN    Anywhere
32400/tcp                  ALLOW IN    Anywhere
22/tcp (v6)                ALLOW IN    Anywhere (v6)
25/tcp (v6)                ALLOW IN    Anywhere (v6)
465/tcp (v6)               ALLOW IN    Anywhere (v6)
587/tcp (v6)               ALLOW IN    Anywhere (v6)
137,138/udp (v6)           ALLOW IN    Anywhere (v6)
139,445/tcp (v6)           ALLOW IN    Anywhere (v6)
32469/tcp (v6)             ALLOW IN    Anywhere (v6)
1900/udp (v6)              ALLOW IN    Anywhere (v6)
32410,32412,32413,32414/udp (v6) ALLOW IN    Anywhere (v6)
32400/tcp (v6)             ALLOW IN    Anywhere (v6)
[COLOR=#000000]
```[/COLOR]
But in my ufw logs I seeing the following

[COLOR=#000000]```
[/COLOR]
Sep 19 10:44:38 nas-home kernel: [39030.014634]** [UFW BLOCK]** IN=eth0 OUT= MAC=38:ea:a7:a3:**:**:**:**:**:**:**:**:**:** SRC=192.168.0.1 DST=192.168.0.10 LEN=262 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF **PROTO=UDP SPT=1900** DPT=14027 LEN=242
Sep 19 10:44:38 nas-home kernel: [39030.014691] **[UFW BLOCK] **IN=eth0 OUT= MAC=38:ea:a7:a3:**:**:**:**:**:**:**:**:**:** SRC=192.168.0.1 DST=192.168.0.10 LEN=304 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF **PROTO=UDP SPT=1900** DPT=14027 LEN=284
Sep 19 10:45:02 nas-home kernel: [39053.478231]** [UFW BLOCK]** IN=eth0 OUT= MAC=38:ea:a7:a3:**:**:**:**:**:**:**:**:**:** SRC=192.168.0.1 DST=192.168.0.10 LEN=262 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF **PROTO=UDP SPT=1900** DPT=42092 LEN=242
[COLOR=#000000]
```

[/COLOR][COLOR=#000000]```
[/COLOR]
$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr ******************
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3aea:a7ff:fea3:2b2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33738 errors:0 dropped:1 overruns:0 frame:0
          TX packets:26332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10486656 (10.4 MB)  TX bytes:3288070 (3.2 MB)
          Interrupt:18
[COLOR=#000000]
```[/COLOR]


Am I missing something here.  Why is the ufw log showing block for ports that are allowed......  I also have an issue with the following ports as well 32410,32412,32413,32414/udp

[COLOR=#000000]```
[/COLOR]
Sep 19 09:44:30 nas-home kernel: [35423.812088] [UFW BLOCK] IN=eth0 OUT= MAC=38:ea:a7:a3:**:**:**:**:**:**:**:**:**:** SRC=192.168.0.6 DST=192.168.0.10 LEN=364 TOS=0x00 PREC=0x00 TTL=64 ID=8333 PROTO=UDP SPT=32412 DPT=48715 LEN=344
Sep 19 09:44:45 nas-home kernel: [35438.754737] [UFW BLOCK] IN=eth0 OUT= MAC=38:ea:a7:a3:**:**:**:**:**:**:**:**:**:** SRC=192.168.0.6 DST=192.168.0.10 LEN=364 TOS=0x00 PREC=0x00 TTL=64 ID=23803 PROTO=UDP SPT=32412 DPT=48715 LEN=344
[COLOR=#000000]
```[/COLOR]


I have tried restarting ufw, recreating the rules, but still the same issue and the same errors in the ufw logs.

Thanks, Dan.

---

### Post by TheFu on 2015-09-19
Could you please edit the #1 post and use "code tags" so things line up better? Too hard for me to read as it is now.

Whenever troubleshooting, simplify and retest - over and over again until the setting that initially causes the problem is isolated.  I would start by disabling ipv6. I'd also see the results using **sudo iptables -L**. Order matters, though nothing is jumping out at me as incorrect.

BTW - if you aren't running an email server on the same box, there are lots of unwanted rules.  IMHO, having internet-facing email on the same machine with **any** other service is asking to be hacked. In fact, I run a separate email gateway VM just to accept inbound emails and filter out the crap before it gets to the main email server.

Lastly, are you doing a port scan with nmap from a different box?  That would be helpful.

---

### Post by Daniel1975m on 2015-09-19
Thanks for your post, and yes I have updated my post to use code tags.  Will use in the future.

I have not done anything special here, just added the allowed ports using ufw.  Also other allowed ports are working fine, I.e SSH.

```

$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere


Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere
ufw-track-forward  all  --  anywhere             anywhere


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere
ufw-track-output  all  --  anywhere             anywhere


Chain ufw-after-forward (1 references)
target     prot opt source               destination


Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination


Chain ufw-after-output (1 references)
target     prot opt source               destination


Chain ufw-before-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere


Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination


Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere


Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-reject-forward (1 references)
target     prot opt source               destination


Chain ufw-reject-input (1 references)
target     prot opt source               destination


Chain ufw-reject-output (1 references)
target     prot opt source               destination


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-track-forward (1 references)
target     prot opt source               destination


Chain ufw-track-input (1 references)
target     prot opt source               destination


Chain ufw-track-output (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination


Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:urd
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:submission
ACCEPT     udp  --  anywhere             anywhere             multiport dports netbios-ns,netbios-dgm
ACCEPT     tcp  --  anywhere             anywhere             multiport dports netbios-ssn,microsoft-ds
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:32469
ACCEPT     udp  --  anywhere             anywhere             udp dpt:1900
ACCEPT     udp  --  anywhere             anywhere             multiport dports 32410,32412,32413,32414
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:32400


Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination


Chain ufw-user-output (1 references)
target     prot opt source               destination

```

---

### Post by TheFu on 2015-09-19
Thanks for the code tags!  

I'm playing with ufw here trying some of those things on a test machine. Not to the point where things are breaking. I have a plex/kodi/nfs box, but it is busy entertaining for most of the day - so I cannot try any rules directly on it.

I use a default deny inbound policy on most systems here - just not on the plex box because it isn't internet accessible.

---

### Post by Lars Noodén on 2015-09-19
I see things like that a lot in the logs also for TCP.  My guess is that it is not UFW as much as iptables, which UFW is the front end for.  Specifically, I'd guess that the kernel is having trouble tracking the correct state of the UDP packets.

---

