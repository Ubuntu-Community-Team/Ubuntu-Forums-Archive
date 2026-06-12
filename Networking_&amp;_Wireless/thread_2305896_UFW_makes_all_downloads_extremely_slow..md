---
title: "UFW makes all downloads extremely slow."
date: 2015-12-10
forum: Networking &amp; Wireless
---

### Post by henrik12 on 2015-12-10
Hi,

when I have ufw enabled all downloads seem to get throttled. I run a teamspeak with music bots (runs locally, connects to 127.0.0.1 and gets music from various sources like youtube, shoutcast, etc) and the music will stutter/buffer and sometimes skip to a new song by itself. When I download updates through steamcmd the first part will go fine, but it will after a very short while go to a crawl giving me 0.01% every few seconds, which would translate to something like a 1-2 kB/s. If I disable ufw everything works smoothly. 

I've tried commenting out the limits in /lib/ufw/user.rules, but they get activated when i enable ufw. Not sure if that's even my issue, but I wanted to try it. 

I'm using Ubuntu 15.10.

My current iptables -L with ufw enabled:
```

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8087
ACCEPT     udp  --  anywhere             anywhere             udp dpt:8087
ACCEPT     udp  --  anywhere             anywhere             udp dpts:2302:2305
ACCEPT     tcp  --  anywhere             anywhere             tcp dpts:2302:2305
ACCEPT     udp  --  anywhere             anywhere             udp dpts:27000:27030
ACCEPT     tcp  --  anywhere             anywhere             tcp dpts:27000:27030
ACCEPT     tcp  --  anywhere             anywhere             tcp dpts:26900:26905
ACCEPT     udp  --  anywhere             anywhere             udp dpts:26900:26905
ACCEPT     udp  --  anywhere             anywhere             udp dpt:4242
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:4242
ACCEPT     udp  --  anywhere             anywhere             udp dpt:27015
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:27015
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:7776
ACCEPT     udp  --  anywhere             anywhere             udp dpt:7776
ACCEPT     udp  --  anywhere             anywhere             udp dpt:27015
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:27015
ACCEPT     udp  --  anywhere             anywhere             udp dpt:40025
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:40025
ACCEPT     udp  --  anywhere             anywhere             udp dpt:7777
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:7777
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:27015
ACCEPT     udp  --  anywhere             anywhere             udp dpt:27015
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:32330
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:7778
ACCEPT     udp  --  anywhere             anywhere             udp dpt:7778
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:27016
ACCEPT     udp  --  anywhere             anywhere             udp dpt:27016
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:9987
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:10011
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:30033
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     icmp --  anywhere             anywhere             icmp echo-reply
ACCEPT     udp  --  anywhere             anywhere             udp spts:27000:27030 dpts:1025:65355
ACCEPT     udp  --  anywhere             anywhere             udp spt:4380 dpts:1025:65355
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED


Chain FORWARD (policy DROP)
target     prot opt source               destination



Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere             udp dpt:4380
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:4380
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:27095
ACCEPT     udp  --  anywhere             anywhere             udp dpt:27095
ACCEPT     tcp  --  anywhere             anywhere             tcp dpts:27000:27030
ACCEPT     tcp  --  anywhere             anywhere             tcp dpts:7776:7778
ACCEPT     udp  --  anywhere             anywhere             udp dpts:7776:7778
ACCEPT     udp  --  anywhere             anywhere             udp dpts:27000:27030
ACCEPT     icmp --  anywhere             anywhere             icmp echo-reply
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED


Chain ufw-after-forward (0 references)
target     prot opt source               destination


Chain ufw-after-input (0 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             LOG level warning prefix "[UFW ALLOW] "


Chain ufw-after-output (0 references)
target     prot opt source               destination


Chain ufw-before-forward (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere


Chain ufw-before-input (0 references)
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


Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW AUDIT] "


Chain ufw-before-logging-input (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW AUDIT] "


Chain ufw-before-logging-output (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW AUDIT] "


Chain ufw-before-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere

Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             ctstate INVALID LOG level warning prefix "[UFW AUDIT INVALID] "
LOG        all  --  anywhere             anywhere             LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere


Chain ufw-reject-forward (0 references)
target     prot opt source               destination


Chain ufw-reject-input (0 references)
target     prot opt source               destination


Chain ufw-reject-output (0 references)
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


Chain ufw-track-forward (0 references)
target     prot opt source               destination


Chain ufw-track-input (0 references)
target     prot opt source               destination


Chain ufw-track-output (0 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination


Chain ufw-user-input (1 references)
target     prot opt source               destination


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

I am fairly new to all of this and have tried finding a solution for 3 days with no luck, so I really hope someone here might have a solution for me.

---

### Post by ian-weisser on 2015-12-10
Well, if you believe ufw is the culprit, uninstall it. Or simply don't run it.

ufw, despite the name, is NOT your firewall.
iptables, part of the Linux kernel, is your firewall.
ufw is simply a frontend application that controls the iptables configuration. Other applications (and simple shell commands) do the job just as well.

---

