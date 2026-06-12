---
title: "How to block an ip range using Edgy"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by davesmith on 2006-11-01
Hello
I'd like to know how to close a connection on port 80 manually, and how to filter an ip range connecting on port 80, using 6.10 Edgy. Any info appreciated

---

### Post by kidders on 2006-11-01
Hi there,

I think what you want is a firewall, eg iptables.

---

### Post by NetworkGuy on 2006-11-01
Try firestarter

```
sudo apt-get install firestarter
```

This is a front-end to iptables and should be able to do do the blocking and filtering you want.

---

### Post by matthewstory on 2006-11-01
iptables -A INPUT -p tcp --dport 80 -j DROP -s 192.168.1.0/24

that'll work, after the -s you can specify individual IPs or you can specify a range of IPs, like I have done.  As far as closing an open connection, that I do not know.

---

### Post by kidders on 2006-11-02
That iptables command will interrupt an open connection, with one tiny modification. If you change the "-A" to "-I", this will ensure that no other rule causes packets you want to block to be accepted.

From the other end, it will appear as though your computer suddenly went offline.

---

