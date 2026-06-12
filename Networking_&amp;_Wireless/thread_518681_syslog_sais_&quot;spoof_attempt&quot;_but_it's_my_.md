---
title: "syslog sais: &quot;spoof attempt&quot; but it's my own machine over NFS!"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by isync on 2007-08-06
I've got a machine (m1) which connects to a share on machine 2 (m2), now the syslog on m2 sais:
Aug  6 10:29:59 localhost nfsd[30756]: spoof attempt by <ip of m1>: pretends to be localhost! 
Aug  6 10:29:59 localhost mountd[30758]: spoof attempt by <ip of m1>: pretends to be localhost! 

What does that mean?? My NFS shares so far have been working 99%fine, but it appears there are still some issues left... Any help??

---

### Post by misconfiguration on 2007-08-06
show the output by doing this.

```
sudo cat /etc/hosts
```

```
cat /etc/resolv.conf
```

Check your system logs in /var/log/*

also check the output of /var/log/message by running command

```
dmesg
```

Give us an update, show more info if possible, thanks.

---

### Post by isync on 2007-08-06
cat /etc/resolv.conf: two properly working nameservers.

cat /etc/hosts
127.0.0.1 localhost machine2
127.0.1.1 machine2

nothing interesting on the rest...

---

