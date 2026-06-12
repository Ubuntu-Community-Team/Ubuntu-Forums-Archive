---
title: "How to PING with packet size increment?"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by Idzi on 2014-05-16
Hi. 

I'd like some advice on how to accomplish something at the Linux command line that I have been doing at the Windows and OSX command line for years..

Okay, so sometimes it is useful in network administration to carry out a ping sweep that increases the packet size incrementally while pinging a single host.  With the 'do not fragment' bit set, this can be used to quickly determine the maximum MTU between two hosts without faffing about with trial and error.  Or it can be used to test a problematic connection for MTU 'black holes', whereby packets of a certain size - but not necessarily the largest - do not make it across a connection.  

From a Mac OSX terminal you can achieve this with the command:  **[FONT=courier new]ping -g 56 -G 1492 -h 10 -D [ip address][/FONT]**

The -g and -G flags define the minimum and maximum packet size respectively.  While the -h [number] is the amount by which to increment the packet size each time.  The -D specifies 'Do Not Fragment'.   

For example, we might run this ping sweep against Google's public DNS ..

**[FONT=courier new]$ ping -g 56 -G 1492 -h 10 -D 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4): (56 ... 1492) data bytes[/FONT]**
**[FONT=courier new]64 bytes from 8.8.4.4: icmp_seq=0 ttl=58 time=7.815 ms[/FONT]**
**[FONT=courier new]74 bytes from 8.8.4.4: icmp_seq=1 ttl=58 time=8.034 ms[/FONT]**
**[FONT=courier new]84 bytes from 8.8.4.4: icmp_seq=2 ttl=58 time=12.081 ms[/FONT]**
**[FONT=courier new]94 bytes from 8.8.4.4: icmp_seq=3 ttl=58 time=7.721 ms[/FONT]**
**[FONT=courier new]104 bytes from 8.8.4.4: icmp_seq=4 ttl=58 time=7.507 ms[/FONT]**
[B][FONT=courier new]
...[output omitted]... [/FONT][/B]

**[FONT=courier new]1434 bytes from 8.8.4.4: icmp_seq=137 ttl=58 time=11.224 ms[/FONT]**
**[FONT=courier new]1444 bytes from 8.8.4.4: icmp_seq=138 ttl=58 time=17.454 ms[/FONT]**
**[FONT=courier new]1454 bytes from 8.8.4.4: icmp_seq=139 ttl=58 time=8.477 ms[/FONT]**
**[FONT=courier new]1464 bytes from 8.8.4.4: icmp_seq=140 ttl=58 time=8.788 ms[/FONT]**
**[FONT=courier new]1474 bytes from 8.8.4.4: icmp_seq=141 ttl=58 time=8.717 ms[/FONT]**
**[FONT=courier new]ping: sendto: Message too long[/FONT]**
**[FONT=courier new]ping: sendto: Message too long[/FONT]**
**[FONT=courier new]Request timeout for icmp_seq 142[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]144 packets transmitted, 142 packets received, 1.4% packet loss[/FONT]**
**[FONT=courier new]round-trip min/avg/max/stddev = 7.362/9.731/20.369/1.944 ms[/FONT]**


Windows is (as ever) rather more limited with its default command line tools.  But this can be fixed with 3rd party applications; in this case hrPING.  

Once you have hrPING installed you can achieve the same incremental increase in packet size by running something like from the Windows command prompt:  **[FONT=courier new]hrping [ip address] -f -l 36:1500:10 -s 500 -n 148[/FONT]**

The **[FONT=courier new]-l 36:1500:10[/FONT]** specifies packets from 36 to 1500 bytes, with a size increment of 10 bytes each time a ping is sent.  The -f specifies 'Do Not Fragment'.  etc.

Again a ping sweep against Google's public DNS ..

**[FONT=courier new]C:\Windows\system32>hrping 8.8.4.4 -f -l 1:1500:10 -s 500 -n 148[/FONT]**
**[FONT=courier new]This is hrPING v5.04 by cFos Software GmbH -- [http://www.cfos.de](http://www.cfos.de)[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]Source address is 192.168.10.18; using ICMP echo-request, ID=0812[/FONT]**
**[FONT=courier new]Pinging 8.8.4.4 [8.8.4.4][/FONT]**
**[FONT=courier new]with 1-1500 bytes data (29-1528 bytes IP):[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]From 8.8.4.4: bytes=29 seq=0001 TTL=58 ID=3961 time=6.667ms[/FONT]**
**[FONT=courier new]From 8.8.4.4: bytes=39 seq=0002 TTL=58 ID=3962 time=6.358ms[/FONT]**
**[FONT=courier new]From 8.8.4.4: bytes=49 seq=0003 TTL=58 ID=3963 time=6.305ms[/FONT]**
**[FONT=courier new]From 8.8.4.4: bytes=59 seq=0004 TTL=58 ID=3964 time=6.598ms[/FONT]**
**[FONT=courier new]From 8.8.4.4: bytes=69 seq=0005 TTL=58 ID=3965 time=6.500ms[/FONT]**
**[FONT=courier new]From 8.8.4.4: bytes=79 seq=0006 TTL=58 ID=3966 time=6.248ms[/FONT]**
**[FONT=courier new]From 8.8.4.4: bytes=89 seq=0007 TTL=58 ID=3967 time=6.263ms[/FONT]**
[B][FONT=courier new]From 8.8.4.4: bytes=99 seq=0008 TTL=58 ID=3968 time=6.599ms

...[output omitted]...

[/FONT][/B][FONT=courier new]**From 8.8.4.4: bytes=1439 seq=008e TTL=58 ID=3984 time=6.935ms**[/FONT]
[FONT=courier new]**From 8.8.4.4: bytes=1449 seq=008f TTL=58 ID=3985 time=7.042ms**[/FONT]
[FONT=courier new]**From 8.8.4.4: bytes=1459 seq=0090 TTL=58 ID=3986 time=6.936ms**[/FONT]
[FONT=courier new]**From 8.8.4.4: bytes=1469 seq=0091 TTL=58 ID=3987 time=6.957ms**[/FONT]
[FONT=courier new]**From 8.8.4.4: bytes=1479 seq=0092 TTL=58 ID=3988 time=6.979ms**[/FONT]
[FONT=courier new]**From 8.8.4.4: bytes=1489 seq=0093 TTL=58 ID=3989 time=7.001ms**[/FONT]
[FONT=courier new]**From 8.8.4.4: bytes=1499 seq=0094 TTL=58 ID=398a time=6.991ms**[/FONT]

[FONT=courier new]**Packets: sent=148, rcvd=148, error=0, lost=0 (0.0% loss) in 73.507403 sec**[/FONT]
[FONT=courier new]**RTTs in ms: min/avg/max/dev: 6.248 / 6.738 / 9.222 / 0.311**[/FONT]
[FONT=courier new]**Bandwidth in kbytes/sec: sent=1.538, rcvd=1.538**[/FONT]
[FONT=courier new]**Correlation: 50.4%, estimated speed: 673.35 kbytes/sec**[/FONT]

Sooo...

My question is:  What command line tool can I use to achieve the same thing in Ubuntu/Linux?

I've had a bloody good rummage around Google but I can't find any examples of how to do the same automatic increment of the packet size upon each ping.  

I know how to search for the maximum MTU manually, using trial and error.  This would look like this...

**[FONT=courier new]$ ping -M do -s 1500 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1500(1528) bytes of data.[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3023ms[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]$ ping -M do -s 1490 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1490(1518) bytes of data.[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2014ms[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]$ ping -M do -s 1480 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1480(1508) bytes of data.[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3023ms[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]$ ping -M do -s 1470 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1470(1498) bytes of data.[/FONT]**
**[FONT=courier new]1478 bytes from 8.8.4.4: icmp_seq=1 ttl=59 time=6.74 ms[/FONT]**
**[FONT=courier new]1478 bytes from 8.8.4.4: icmp_seq=2 ttl=59 time=6.69 ms[/FONT]**
**[FONT=courier new]1478 bytes from 8.8.4.4: icmp_seq=3 ttl=59 time=6.77 ms[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]3 packets transmitted, 3 received, 0% packet loss, time 2003ms[/FONT]**
**[FONT=courier new]rtt min/avg/max/mdev = 6.697/6.740/6.774/0.032 ms[/FONT]**
[B][FONT=courier new]
$ ping -M do -s 1475 8.8.4.4[/FONT][/B]
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1475(1503) bytes of data.[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3024ms[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]$ ping -M do -s 1474 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1474(1502) bytes of data.[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]$ ping -M do -s 1473 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1473(1501) bytes of data.[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]ping: local error: Message too long, mtu=1500[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]$ ping -M do -s 1472 8.8.4.4[/FONT]**
**[FONT=courier new]PING 8.8.4.4 (8.8.4.4) 1472(1500) bytes of data.[/FONT]**
**[FONT=courier new]1480 bytes from 8.8.4.4: icmp_seq=1 ttl=59 time=6.74 ms[/FONT]**
**[FONT=courier new]1480 bytes from 8.8.4.4: icmp_seq=2 ttl=59 time=6.59 ms[/FONT]**
**[FONT=courier new]1480 bytes from 8.8.4.4: icmp_seq=3 ttl=59 time=6.64 ms[/FONT]**
**[FONT=courier new]1480 bytes from 8.8.4.4: icmp_seq=4 ttl=59 time=6.61 ms[/FONT]**
**[FONT=courier new]^C[/FONT]**
**[FONT=courier new]--- 8.8.4.4 ping statistics ---[/FONT]**
**[FONT=courier new]4 packets transmitted, 4 received, 0% packet loss, time 3005ms[/FONT]**
**[FONT=courier new]rtt min/avg/max/mdev = 6.597/6.651/6.744/0.080 ms[/FONT]**




... But I don't want to have to do this manually. 


Please can someone point me to a Linux command line tool that can do the automatic incremental packet size increase? 


Thanks.


Idzi



:confused:

---

### Post by TheFu on 2014-05-16
If ping doesn't do it - check the man page - writing a tiny script would be pretty easy. Check the "ABSG" for howto do this easily. Should be less than 3 lines.

---

### Post by steeldriver on 2014-05-16
You can just put the command in a loop

```

**for size in {1460..1476..4}; do** ping -s $size -c 4 -M do google.com**; done**

```

or if you want to just find the maximum MTU you could check the *exit status* of the ping command and just loop until it fragments e.g.

```

size=1272; while ping -s $size -c1 -M do google.com >&/dev/null; do ((size+=4)); done; echo "Max MTU size: $((size-4+28))"

```

---

