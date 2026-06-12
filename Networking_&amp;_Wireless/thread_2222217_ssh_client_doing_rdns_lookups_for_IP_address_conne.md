---
title: "ssh client doing rdns lookups for IP address connecting to"
date: 2014-05-05
forum: Networking &amp; Wireless
---

### Post by eclay on 2014-05-05
Hello All,

I'm seeing an issue that I've not seen before.  The problems is that when I attempt to ssh to a private IP address the ssh client attempts to do a rDNS lookup of that IP which is causing our caching name servers logs to fill up with errors related to not being able to locate the PTR.  Everything I've found on google seems to suggest that a configuration change of sshd.  Which would make sense if I was seeing the log entries on the name server showing the request originating from the sshd server.  I've attempted to use -o 'CheckHostIP no' when attempting to connect via ssh but am still seeing the errors on the caching name server.

What am I missing?

---

### Post by sanderj on 2014-05-06
[http://linux-tips.org/article/92/disabling-reverse-dns-lookups-in-ssh](http://linux-tips.org/article/92/disabling-reverse-dns-lookups-in-ssh) ?

---

### Post by SeijiSensei on 2014-05-06
Another solution is to create an entry for the server in /etc/hosts:
```
192.168.1.100     my.network.server
```

---

