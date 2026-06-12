---
title: "I can not disable ipv6"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by davholla on 2007-08-30
[http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html)

I followed the instructions as above but ipv6 is still running

```
 ip a | grep inet6
    inet6 ::1/128 scope host
    inet6 fe80::208:c7ff:fec5:dafc/64 scope link

```

I have added these modified lines in /etc/modprobe.d/aliases
```
 ip a | grep inet6
    inet6 ::1/128 scope host
    inet6 fe80::208:c7ff:fec5:dafc/64 scope link
#alias net-pf-10 ipv6

```

---

### Post by linuxwizard on 2007-08-30
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by davholla on 2007-08-31
Thanks I will try that.

---

### Post by davholla on 2007-09-01
Thanks that worked and it seems faster.

---

