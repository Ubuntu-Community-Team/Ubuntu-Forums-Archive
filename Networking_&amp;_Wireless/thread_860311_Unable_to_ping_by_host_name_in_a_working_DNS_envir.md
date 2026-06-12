---
title: "Unable to ping by host name in a working DNS environment"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by asaf.lahav on 2008-07-15
Hello everybody,
I am a newbie. so bear with me ;)
I just recently installed Ubuntu 8.0.4 on a fresh and new machine.

The machine is connected to LAN network (via ethernet) which includes several windows based computers and a windows 2003 domain with a windows 2003 DNS server.

The problem is that even though I configured my Ubuntu machine with the static IP of the network DNS ip address, a ping command fails with the following message:
*ping: unknown host lap-asaf*

Any ideas?
Thanks in advance,
Asaf

---

### Post by Loukisgr on 2008-07-15
you ping using ip or host? i have the same problem is you are trying with host. The DNS is not working properly ;(. I have tryied many thinks but i haven't found a solution yet. Xp can ping your hostname only if you disable firestarter.

---

### Post by asaf.lahav on 2008-07-15
The situation I'm in is where I can ping (using host name) from a windows based workstation, but CANNOT ping from the Ubuntu to any other workstation (using host names).

Anyhow,
This is very frustrating... 
I found many threads using Google about that issue exactly with no resolution (yet).

---

### Post by Loukisgr on 2008-07-15
y i ave another post for the same think open ;) "DNS problem"

---

### Post by Loukisgr on 2008-07-15
I have found a solution!!!! Try and tell me it worked fine to me ;)

gedit /etc/nsswitch.conf

and alter 
hosts:          files wins bcast dns mdns4_minimal [NOTFOUND=return] mdns4

Let me explain here. I added wins for windows clients and bcast because every network card has it's own resolution table ;)

It worked for me because they are in the same domain.

---

### Post by Iowan on 2008-07-15
[Another]("http://ubuntuforums.org/showthread.php?t=778898") option.

---

