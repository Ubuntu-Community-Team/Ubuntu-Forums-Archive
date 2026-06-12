---
title: "no-reply when tracepath, but connection is fine"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by bristolbadger23 on 2008-07-12
Hi everyone,

I'm pretty good with networks in general but this one has me stumped.

On my Xubuntu and Ubuntu 7.04 machines I get the following output when running tracepath, traceroute etc... but this doesn't happen on my Windoze machine... (see below). I have a Linksys BEFSR41 V3 router which is new to me. This problem didn't happen on my DLink DI-704. My BSD box is currently in bits so can't comment on westher or not i'd have the same issue on that.

All machines and routers have latest updates etc,


> [INDENT]badger@polar:~$ tracepath bbc.co.uk
 1:  10.0.0.2 (10.0.0.2)                                    0.190ms pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply[/INDENT]


> [INDENT]C:\Documents and Settings\bc23>tracert bbc.co.uk

Tracing route to bbc.co.uk [212.58.224.131]
over a maximum of 30 hops:

  1     8 ms     7 ms     7 ms  10.9.0.1
  2    28 ms     8 ms     8 ms  62.30.64.35
  3     9 ms     7 ms     8 ms  aztw-t3core-1b-ge-010-0.inet.ntl.com [80.1.240.129]
  4    10 ms    12 ms     9 ms  bir-bb-b-so-110-0.inet.ntl.com [213.105.175.161]
  5    10 ms     9 ms    11 ms  bir-bb-a-ge-000-0.inet.ntl.com [62.253.185.153]
  6    13 ms    17 ms    12 ms  nth-bb-b-so-220-0.inet.ntl.com [62.253.185.85]
  7    17 ms    13 ms    14 ms  tele-ic-1-as0-0.inet.ntl.com [62.253.184.2]
  8    14 ms    15 ms    15 ms  pos6-1.rt0.thdo.bbc.co.uk [212.58.239.237]
  9    18 ms    13 ms    13 ms  212.58.238.153
 10    19 ms    13 ms    14 ms  rdirwww-vip.thdo.bbc.co.uk [212.58.224.131]

Trace complete.[/INDENT]



Incidentaly, if I ping one of the IPs in the trace I get a reply, but again, trace feeds back as no-reply.

> [INDENT]badger@polar:~$ ping 213.105.175.161
PING 213.105.175.161 (213.105.175.161) 56(84) bytes of data.
64 bytes from 213.105.175.161: icmp_seq=1 ttl=61 time=14.6 ms
64 bytes from 213.105.175.161: icmp_seq=2 ttl=61 time=15.0 ms
64 bytes from 213.105.175.161: icmp_seq=3 ttl=61 time=15.5 ms
64 bytes from 213.105.175.161: icmp_seq=4 ttl=61 time=18.8 ms
64 bytes from 213.105.175.161: icmp_seq=5 ttl=61 time=15.4 ms
64 bytes from 213.105.175.161: icmp_seq=6 ttl=61 time=31.6 ms

--- 213.105.175.161 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5020ms
rtt min/avg/max/mdev = 14.634/18.523/31.601/6.013 ms
badger@polar:~$ [/INDENT]


> [INDENT]badger@polar:~$ tracepath 213.105.175.161
 1:  10.0.0.2 (10.0.0.2)                                    0.206ms pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply[/INDENT]

---

### Post by fwre01 on 2008-07-12
Traceroute's use TTL Expired ICMP packets and Pings use echo request ICMP packets, which may explain why you can ping the hosts but fail the trace.

Its interesting why you dont receive a trace response from 10.0.0.2 (which im assuming is your gateway) when performing a trace in windows. Are the setup in the same way?

---

### Post by bristolbadger23 on 2008-07-12
BTW

Windows is on 10.0.0.3
Ubuntu is on 10.0.0.2

Gateway is 10.0.0.1...

Response times are ok so wouldn't have expected simultaneous traces to fail on different machines...

:(

---

### Post by cpcgm on 2008-10-04
Did you manage to solve the problem?

---

### Post by bristolbadger23 on 2008-10-04
I did, I had the answer from a friend actually who suggested using MTR.

It's real late, so I'll go into how they work differently another time. But MTR does seem to be a very useful tool.

:)

---

### Post by odzx on 2008-11-03
> **bristolbadger23 said:**
> I did, I had the answer from a friend actually who suggested using MTR.

It's real late, so I'll go into how they work differently another time. But MTR does seem to be a very useful tool.

:)

that works for me to,
also  sudo traceroute -I <address> works fine.
I still dont understand why tracepath does not work.:confused:

---

### Post by strider22 on 2009-10-29
I tracked my problem to tracepath as well.
Here are my two posts at dslreports;

Now to find the tracepath bug report location.
Does anyone know where to report this problem?

---post 1---
What does this tracepath mean?
Why are there 3 lines for my router at the beginning?
They report 2ms but take a long time to be printed.
Why does it timeout at the end? (same results with [www.)](www.))

root@beryllium:/home/chris# tracepath dslreports.com
1: beryllium.local (192.168.1.112) 0.136ms pmtu 1500
1: 192.168.1.2 (192.168.1.2) 1.769ms
1: 192.168.1.2 (192.168.1.2) 1.805ms
2: 192.168.1.2 (192.168.1.2) 1.874ms pmtu 1492
2: bas6-hamilton14_lo0_SYMP.net.bell.ca (64.230.197.21) 62.647ms asymm 3
3: dis8-hamilton14_7-6_106.net.bell.ca (64.230.163.145) 56.864ms
4: core1-hamilton14_GE2-0.net.bell.ca (64.230.236.241) 57.286ms
5: newcore3-toronto12_pos0-9-0-0.net.bell.ca (64.230.131.225) 58.983ms
6: core1-chicago23_pos13-0-0.net.bell.ca (64.230.147.18) 68.642ms
7: bx3-chicagodt_so-0-0-0-0.net.bell.ca (64.230.203.46) 69.126ms asymm 8
8: chi-bb1-link.telia.net (213.248.85.25) 71.180ms asymm 9
9: nyk-bb2-link.telia.net (80.91.248.197) 85.405ms asymm 11
10: nyk-b3-link.telia.net (80.91.248.178) 86.867ms asymm 12
11: netaccess-tic-133837-nyk-b3.c.telia.net (213.248.99.90) 86.609ms asymm 12
12: 0.e1-1.tbr1.ewr.nac.net (209.123.10.129) 91.582ms asymm 13
13: 0.e1-4.tbr1.oct.nac.net (209.123.10.122) 88.417ms asymm 14
14: vlan804.esd1.oct.nac.net (209.123.10.2) 84.880ms
15: no reply
16: no reply
17: no reply
18: no reply
19: no reply
20: no reply
21: no reply
22: no reply
23: no reply
24: no reply
25: no reply
26: no reply
27: no reply
28: no reply
29: no reply
30: no reply
31: no reply
Too many hops: pmtu 1492
Resume: pmtu 1492 

----post 2----

How do I tell if it is Bell's or my router?
My router is the 192.168.1.2

Why does my router's IP show up 3 times?
Hmmm. I'm guessing tracepath retries 3 times to see if can get a name and the router won't give one. -ok we'll skip this part of the questions.

The real problem is why couldn't tracepath find dslreports.com
I could see dslreports.com with the web browser just not with tracepath
I checked with ping and I can ping dslreports.com
It's tracepath that won't complete.

Tried mtr (matt's traceroute) instead and it seems fine as you can see below. Tracepath still times out.

root@beryllium:/home/chris# mtr dslreports.com --report
HOST: beryllium Loss% Snt Last Avg Best Wrst StDev
1. 192.168.1.2 0.0% 10 0.5 0.5 0.5 0.5 0.0
2. bas6-hamilton14_lo0_SYMP.net 0.0% 10 41.1 41.8 41.1 42.6 0.5
3. dis8-hamilton14_7-6_106.net. 0.0% 10 39.7 39.9 39.6 40.3 0.2
4. core1-hamilton14_GE2-0.net.b 0.0% 10 40.3 40.1 39.6 41.3 0.5
5. newcore3-toronto12_pos0-9-0- 0.0% 10 41.8 41.7 40.9 42.5 0.6
6. core1-chicago23_pos13-0-0.ne 0.0% 10 53.5 53.7 53.4 54.4 0.3
7. bx3-chicagodt_so-0-0-0-0.net 0.0% 10 62.6 54.7 53.1 62.6 2.8
8. chi-bb1-link.telia.net 0.0% 10 106.5 71.1 53.5 161.3 35.6
9. nyk-bb2-link.telia.net 0.0% 10 69.0 75.5 66.5 125.9 17.9
10. nyk-b3-link.telia.net 0.0% 10 69.1 69.2 67.9 74.5 1.9
11. netaccess-tic-133837-nyk-b3. 0.0% 10 69.5 71.2 68.9 74.9 2.3
12. 0.e1-4.tbr1.mmu.nac.net 0.0% 10 71.1 71.4 69.9 75.6 1.6
13. 0.e1-1.tbr1.oct.nac.net 0.0% 10 76.2 71.9 69.6 76.2 2.7
14. vlan804.esd1.oct.nac.net 0.0% 10 67.7 69.6 67.7 73.9 2.2
15. [www.dslreports.com](www.dslreports.com) 10.0% 10 90.0 75.3 69.7 90.0 6.1

---

