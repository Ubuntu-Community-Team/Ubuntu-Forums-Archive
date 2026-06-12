---
title: "proftpd after update problem"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by entereczek on 2006-10-17
hi,
i have got problem with proftpd in the newest version 1.3.0
I have even deleted my conf and replace it with standart one, but it didnt help...

```
# /etc/init.d/proftpd start
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
root@pingwinek:/home/entereczek# sudo proftpd
 - IPv6 getaddrinfo 'localhost' error: Name or service not known
localhost - fatal: Socket operation on non-socket

```
i have read README.Debian file and now my hosts file looks like that:
```
127.0.0.1 localhost pingwinek
127.0.1.1 pingwinek
192.168.2.201 laptop
# The following lines are desirable for IPv6 capable hosts

::1 ip6-localhost ip6-loopback pingwinek
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
best Regards
Entereczek

---

### Post by serkanhamarat on 2006-10-17
Try to extract IPv6 address from ifconfig output.
Then put it in the hosts file with a hostname.

---

