---
title: "Time based firewall"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by reloded on 2008-01-23
Hello.

I've been searching for ways to block traffic according to time of day. 

From 9:00 AM to 1:00pm, I want to block port 80 for http,
Open it from 1:00pm to 2:00pm,
Block it again till 5:00pm,
Then open it till the following day at 9:00 am
This is for weekdays only.

On Weekends, port 80 should be opened.

Can I don this using Monowall? Firehol?

If not, please assist me in setting up the above with Ubuntu 7.04 server.


Thanks.

---

### Post by tehet on 2008-01-23
I would make 2 iptables scripts. One with
iptables -I INPUT -p tcp --destination-port 80  -j ACCEPT
and one with
iptables -I INPUT -p tcp --destination-port 80  -j DROP # or REJECT
and load them with cron.

---

### Post by reloded on 2008-01-23
Thanks for the reply.

Lets just say iptable scripting is not one of my strengths. Thats the reason for using short cuts like Monowall.

I have Googled, read about iptables but can never seem to master them.

Could you sort me out in this regard?

Hey, wait a minute. I see you've provided a sample! Thanks.

I'll try them out.

---

### Post by reloded on 2008-01-23
> **tehet said:**
> I would make 2 iptables scripts. One with
iptables -I INPUT -p tcp --destination-port 80  -j ACCEPT
and one with
iptables -I INPUT -p tcp --destination-port 80  -j DROP # or REJECT
and load them with cron.

Quick question though. All this while, I need port 80  open for at least 4 computers/ip addresses. Manager, Admin etc.

---

### Post by tehet on 2008-01-23
The full script would look something like this (no guarantees):
```
#!/bin/bash

iptables -F

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

iptables -A INPUT   -i eth0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP

iptables -I INPUT -p tcp --destination-port 80  -j ACCEPT

echo 1 > /proc/sys/net/ipv4/ip_forward
```
Let us know if it works.

---

### Post by tehet on 2008-01-23
> **reloded said:**
> Quick question though. All this while, I need port 80  open for at least 4 computers/ip addresses. Manager, Admin etc.
You can add something like this:
```
/sbin/iptables -A INPUT -p tcp -i eth0 -s 1.2.0.0/16 --dport 88 -j ACCEPT
```
where 1.2.0.0 is your subnet.

---

### Post by reloded on 2008-01-23
Thanks for that. I'll have a look at it and report back.


Arigatoo! :)

---

