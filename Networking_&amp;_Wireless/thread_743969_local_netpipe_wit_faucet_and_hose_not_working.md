---
title: "local netpipe wit faucet and hose not working"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by bacante on 2008-04-03
Hi there!

I'm trying to communicate 2 processes in the same machine using *netpipes*. First I launch *faucet *and afterwards *hose*:

```
faucet 9999 --daemon --in sh -c "cat"
hose localhost 9999 --out sh -c "echo 'hola'"
```
I've tested this in _Debian and in Ubuntu_ and it works perfectly, but my problem is with _***Xubuntu***_. It's something related to *faucet *not responding to the hose TCP synchronization request.

I know that because if I do *netstat -a | grep 9999* I get:

```
tcp    0    0        *:9999        *:*                LISTEN
tcp    0    1    <miIP>:59821    localhost:9999    SYN_SENT
```
The state SYN_SENT means that an application has made a request for a TCP session, but has not yet received the return SYN+ACK packet.

Any clue?
Why I'm having differences when executing this in Debian/Ubuntu and in Xubuntu?

Thank you very much in advance!
B.

---

### Post by devurandom77 on 2008-04-15
Wow.  I haven't used faucet and hose since I started using netcat about 7 or 8 years ago...

The only thing that I can think of is that iptables may be enabled and causing problems.  You're clearly on the right path in terms of diagnosis.  As a slight sanity check though, make sure localhost isn't doing something funky (ie: look in /etc/hosts and/or do a netstat -n).  Also, make sure your loopback interface is actually up.

If iptables is running, make sure that all traffic coming from the localhost interface is accepted by default.  Sometimes folks leave that out...

---

### Post by bacante on 2008-04-16
I have just solved the problem. I had no loopback Internet address configured. Once configured it started to work propertly.

Thank you very much for your help!
B.

---

