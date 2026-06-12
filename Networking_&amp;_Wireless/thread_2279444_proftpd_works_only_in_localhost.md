---
title: "proftpd works only in localhost"
date: 2015-05-23
forum: Networking &amp; Wireless
---

### Post by vanili on 2015-05-23
Good time of the day!

Today I've installed proftpd and gadmin-proftpd on Ubuntu 14.04 LTS (conf in attach). It works fine on the localhost, but ftp can not be accessed from any other PC.

Here's the output of netstat
```
sudo netstat -npl | grep :21
tcp6       0      0 :::21                   :::*                    LISTEN      28779/proftpd: (acc

```

```
netstat -l | grep proftpd
unix  2      [ ACC ]     STREAM     LISTENING     1187348  /var/run/proftpd.sock
unix  2      [ ACC ]     STREAM     LISTENING     1187365  /var/run/proftpd.sock

```

Any suggestions how to make it work? Thanks inadvance

---

