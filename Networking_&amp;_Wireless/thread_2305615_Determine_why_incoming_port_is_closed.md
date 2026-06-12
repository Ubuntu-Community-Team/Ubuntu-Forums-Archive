---
title: "Determine why incoming port is closed"
date: 2015-12-07
forum: Networking &amp; Wireless
---

### Post by spookybathtub on 2015-12-07
Under Ubuntu 14.04, I suspect there is some kind of firewall running, but I don't know why.  From another computer on the same subnet, this command fails.
```
$ nc -zv 192.168.xxx.xxx #####
nc: connectx to 192.168.xxx.xxx port ##### (tcp) failed: Connection refused

```
How can I determine what software is blocking the port (and then open it)?

Backstory: rTorrent reports that this port is closed.  I have already forwarded it correctly on the router, and I'm doing this nc test from within the local network.

---

### Post by newbie-user on 2015-12-07
iptables is the default firewall, so you might want to check that. Otherwise, you might not have any service on the ubuntu box that runs on the port you're trying to test.

---

### Post by QIII on 2015-12-07
Hello.

Have you installed anything that would be *listening* on that port?

---

### Post by SeijiSensei on 2015-12-08
1)  Review any firewall rules with "sudo iptables -L -nv".

2)  What is supposed to be listening on the closed port?  Are you sure the daemon is running?  Is the port closed if you try and access it from the machine itself on the localhost interface?

---

### Post by ch43 on 2015-12-09
Do you have ufw installed?

What is the output of
```
sudo ufw status
```?

---

### Post by spookybathtub on 2015-12-20
rTorrent is supposed to be listening on that port.  In ruTorrent GUI, it shows a red exclamation symbol, saying the port is closed.

```
$ sudo iptables -L -nv 
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
$ sudo ufw status
sudo: ufw: command not found

```

---

