---
title: "IPTABLES not blocking port 1720"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by psyncho on 2014-03-21
Hi, 

I just setup ubuntu in the cloud, did an upgrade, setup iptables, then to verify did an nmap scan - and port 1720 stays open persistently. I don't get it. 

Here's what's in my iptables right now: 
```
iptables -L -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 4024  171K ACCEPT     all  --  lo     any     anywhere             anywhere            
 4208 4572K ACCEPT     all  --  any    any     anywhere             anywhere             ctstate RELATED,ESTABLISHED
    1    64 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:65222
   46  2800 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:3333
    3   152 DROP       tcp  --  any    any     anywhere             anywhere             tcp dpt:1720
 109K 6385K DROP       all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 5/min burst 5 LOG level debug prefix "iptables denied: "

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 6699 packets, 739K bytes)
 pkts bytes target     prot opt in     out     source               destination     
```

In fact, I drop anything that doesn't have an explicit accept rule, so the drop for port 1720 is redundant, but I manually put it in there because this port is not showing up as filtered.

here's the output of an nmap scan on the ip:

```
nmap -APn <some ip address>

Starting Nmap 6.40 ( http://nmap.org ) at 2014-03-21 17:08 EDT
Nmap scan report for ...
Host is up (0.49s latency).
Not shown: 988 filtered ports
PORT     STATE  SERVICE      VERSION
1720/tcp open   H.323/Q.931?
3333/tcp closed dec-notes
6000/tcp closed X11
6001/tcp closed X11:1
6002/tcp closed X11:2
6003/tcp closed X11:3
6004/tcp closed X11:4
6005/tcp closed X11:5
6006/tcp closed X11:6
6007/tcp closed X11:7
6009/tcp closed X11:9
6059/tcp closed X11:59
```

So I did a netstat and greped for port 1720, nothing is actually open and using that.

I found out the port is often used for voip. However, this is a sever in the cloud that most definitely is not (and could not be) used for that, and I never installed that, and can't find anything on it that would indicate that. 

I'm at a loss, any ideas?

O.k., a little new info - a friend testing it from a linux box is getting different results. Is it possible nmap has a bug or diff output? Seems really weird now

---

### Post by SeijiSensei on 2014-03-22
Are you scanning the machine from the machine itself when you find 1720 open?  That won't tell you anything since it will be scanning from the localhost interface which is permitted by the first line of your rules.  Scanning from an external machine is the only sure way to know what a possible intruder can see.

That still doesn't answer why 1720 is open though.  What kind of banner do you see if you run "telnet localhost 1720"?

---

### Post by psyncho on 2014-03-22
Hi, 

This was a vm at digital ocean that I was testing from my laptop. I couldn't figure it out so just destroyed it. 
Netstat should have revealed anything listening. I strated to try telnet but couldn't remember the command.

---

