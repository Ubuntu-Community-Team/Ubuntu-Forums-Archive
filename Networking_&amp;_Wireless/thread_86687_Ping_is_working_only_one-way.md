---
title: "Ping is working only one-way"
date: 2005-11-06
forum: Networking &amp; Wireless
---

### Post by hesee on 2005-11-06
Hi,
I've got two ubuntu machines in home network. I've set up ip addresses: 192.168.0.1 ja 192.168.0.2. I'm trying to connect them, but ping only works to one direction(from 192.168.0.2 to 192.168.0.1). If I try to ping from 192.168.0.1, i get messages like this:

hesee@ubuntu:~$ ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.0.2 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

Could this be some kind of firewall problem? 192.168.0.2-machine is new fresh install, but 192.168.0.1 is machine where i test everything new and interesting, (and sometimes mess things up).

---

### Post by skmassey on 2005-11-06
It could be that for some reason SNMP (Simple Network Management Protocol) packets are blocked in the firewall.  I don't know exactly how to fix that problem though.  IIRC SNMP uses ports 161 and 162.  Maybe those ports are blocked on the 192.168.0.1 machine.

---

### Post by mips on 2005-11-06
Check to see if you have got ICMP filtering enable or not.

Can be found under firestarter preferences.

---

### Post by hesee on 2005-11-06
[QUOTE=mips]Check to see if you have got ICMP filtering enable or not.

Can be found under firestarter preferences.[/QUOTE]


It is not, should it be? Don't know very much about these networking things... And if i enable it, should i also allow Echo request(ping)?

---

### Post by mips on 2005-11-06
If the Enable ICMP filtering box is not checked then it should allow ICMP packets by default.

Try stopping Firestarter on both machines, try the ping again and see if it makes a difference.

---

### Post by hesee on 2005-11-06
Ok, I was pinging own computer, when it was "working"... :(  So, the both directions are not working...

---

### Post by hesee on 2005-11-06
Stopping the firestarter allows me to ping!** Thanks, mips**. Strange thing that it prevents me pinging, it wasn't filtered... Anyway, my final goal is to set up samba server to another computer for file sharing. (The other is xp/ubuntu-dual, so NFS is not suitable, i think). I'll be back if more problems occur.

---

