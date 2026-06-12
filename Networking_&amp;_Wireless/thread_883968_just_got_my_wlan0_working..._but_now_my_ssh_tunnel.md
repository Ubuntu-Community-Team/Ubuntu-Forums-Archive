---
title: "just got my wlan0 working... but now my ssh tunnels don't work"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by graysky on 2008-08-08
Finally got the new wireless card installed and configured.  I disabled the wired card simply by commenting out the lines for it in the /etc/network/interfaces

My problem is now that the machine is wireless, mysql can't be reached so I issue:

```
# /etc/init.d/mysql restart
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
```

I fixed it by editing the /etc/mysql/my.cnf and changing this line:

```
bind-address = 127.0.0.1
```

To the machine's wireless IP address:

```
bind-address = 192.168.1.3
```

Now everything is working... my question is, why did I have to change this?  It worked fine using the wired NIC without this mod and the IP address is the same [192.168.1.3] :?:
Thanks!

Also, my putty ssh tunnel doesn't work any more.  I used it in the past to via mythweb securely ([http://localhost:20400](http://localhost:20400) in my browser would tunnel mythweb and it no longer works).

---

