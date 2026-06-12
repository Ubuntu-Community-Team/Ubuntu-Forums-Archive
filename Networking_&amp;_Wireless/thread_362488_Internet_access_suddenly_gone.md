---
title: "Internet access suddenly gone"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Minyaliel on 2007-02-15
Okay, so here's the problem. After a session on Kubuntu Edgy where I upgraded the system and installed a few other things (nothing serious, Songbird and things like that) I've not been able to access the internet at all on this installation. This, of course, is very bad. I'm using a normal speed adsl line (not sure if you call them so in English, sorry), so no dial- up. I'm writing from the Edgy live CD on the same computer now, and the same line works on all the other computers in the house. Well, I have no idea how to fix it. Anyone?

---

### Post by Floppyjoe on 2007-02-15
The recent kernel update broke wireless for a lot of people. I don't know what steps you took to get your wifi working in the first place but you may have to reinstall some things or look for a solution other people may have found already.

---

### Post by avfangel on 2007-02-15
What do you mean by 'not connecting'? is the connection dropped? you should post the logs.

try:
#this should give the basic ppp log
~$ plog

#this should give a list of active interfaces and their addresses
~$ip addr

#additional logs:
~$ tail /var/log/ppp-connect-errors
~$ grep ppp  /var/log/syslog | tail

post the results, and hopefully the problem will be in plain sight.

---

### Post by Minyaliel on 2007-02-15
Ah, but my wifi's never worked, so that's not much of a loss... I was talking about a normal network cable. I've looked around, but can't seem to find much on how to fix this particular problem. I'm sure I've overlooked something, but I really can't seem to find it... :/

Self- edit: sim post, sorry. Will try to do that =) somehow, anyway... prolly have to boot out of the live cd and back again afterwards, though. Ah well.

---

### Post by avfangel on 2007-02-15
sorry haven't noticed the 'no dialup' part...

---

### Post by Minyaliel on 2007-02-15
Alright... this is what I ended up with. Mind you, I had to type it out from a handwritten copy, so any all caps or similar has been lost.

$plog
$

$ip addr

1: lo: <loopback,up,10000> mtu 16436 qdisc noqueue
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.01/8 scope host lo
inet6 :: !/128 slope host
valid_lft forever preferred_lft forever

2: eth0: <broadcast,multicast,up,10000> mtu 1500 qdisc pfifo_fast qlen 10000
link/ether 00:c0:9f:a6:8b:67 brd ff:ff:ff:ff:ff:ff
inet 84.202.211.255 scope global eth0
inet6 fe80 :: 2c0:9fff:fca6:8b67/64 scope link
valid_lft forever preferred_lft forever

3: sit0: <noarp> mtu 1480 qdisc noop
link/sit 0.0.0.0 brd 0.0.0.0


On the tail .... etc thing I got the message that it couldn't be read because there was no such file or directory

gep ... etc: "command not found"

---

### Post by Floppyjoe on 2007-02-15
can you ping internet domains?
ie google.com
and if not then 64.233.167.99 ?

---

### Post by Minyaliel on 2007-02-15
What do you mean by ping? (Yeah, go laugh as much as you like)

I can't access any websites, I've tried mozilla/ google/ other major sites several times, there's nothing else than error pages. "Couldn't find server..." bleh.

---

### Post by Floppyjoe on 2007-02-15
Click on System/Administration/Network Tools then try to ping google.com and if that doesn't work try to ping 64.233.167.99 which is also google.com.


Edit for Kubuntu that would be under All applications-->Settings/Network Tools

---

### Post by Minyaliel on 2007-02-15
Umm... I can't find it...

---

### Post by Floppyjoe on 2007-02-15
Klick on k-menu then under All Applications-->Settings/Network Tools
                                              or All Applications-->System/Network Tools
[IMG]http://www.mts.net/~iwiebe2/images/ping1.png[/IMG]
[IMG]http://www.mts.net/~iwiebe2/images/ping2.png[/IMG]

---

