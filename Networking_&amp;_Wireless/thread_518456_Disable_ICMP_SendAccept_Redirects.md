---
title: "Disable ICMP Send/Accept Redirects"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by landonjh on 2007-08-05
Just installed OpenSwan... having the following error. Surfed all the forums, etc. Can't get the failed errors to go away. Any help?

> NETKEY detected, testing for disabled ICMP send_redirects       [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!

NETKEY detected, testing for disabled ICMP accept_redirects     [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!


---

### Post by noob12 on 2007-08-05
As root, you can just write 0 into each of those files. 

For persistence across reboots you can you can put these settings in **/etc/sysctl.conf**

Running 
```

sudo sysctl -a | grep 'ipv4.conf.*redirect'

```
should list the variables you need to set.  (Note: set them all to 0).

Running **sudo sysctl -p** will process it.

---

### Post by landonjh on 2007-08-07
Thanks! Got it working... now I have to get Pluto running...

---

### Post by kbu on 2007-11-04
Hi

have the same problem ....
How to get Pluto running ?

Kbu

---

