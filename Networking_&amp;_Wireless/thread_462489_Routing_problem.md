---
title: "Routing problem"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by ivek on 2007-06-02
Hi!
Im trying to setup my ubuntu server (6.10) as a simple router.
I have two network cards. eth0 and wlan0. 
I've set up  subnets and IP-s.
I've made a new file in /etc/network/ called options and it contains:
ip_forward=yes
spoofprotect=yes
syncookies=yes

I also made this change:
$echo 1 > /proc/sys/net/ipv4/ip_forward

After a restart /proc/sys/net/ipv4/ip_forward value goes back to 0 and there is no routing between interfaces.

Is there any other place where I should enable routing? Maby the problem is that there was no "options" file until I made one and when configuring interfaces nothing checks it's values...

Anyway, help is needed!

Thanks

---

### Post by ivek on 2007-06-03
^Bump^

If you coud just tell me why /proc/sys/net/ipv4/ip_forward value is changing back to 0 after I change it to 1...
I don't get it...

---

### Post by marcd on 2007-06-15
I have the same problem- for the lifeof me I cannot get IP_FORWARD to stay 1. Anyone?

---

### Post by marcd on 2007-06-15
finally- 
put line net.ipv4.conf.all.forwarding=1 in /etc/sysctl.conf

---

