---
title: "Gre tunnel"
date: 2017-06-27
forum: Networking &amp; Wireless
---

### Post by rudger2 on 2017-06-27
Im trying to setup gre tunnel according to: 

[https://wiki.buyvm.net/doku.php/gre_tunnel](https://wiki.buyvm.net/doku.php/gre_tunnel)

When I enter: 

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf
sysctl -p
iptunnel add gre1 mode gre local xxxip remote test.sytes.net ttl 255
ip addr add 192.168.168.1/30 dev gre1
ip link set gre1 up

I get: cannot find device gre1

---

### Post by QIII on 2017-06-27
*Moved to **Networking & Wireless***.

This a networking issue, so let's see if you don't get better visibility here.

---

### Post by rudger2 on 2017-06-28
Anyone knows?

I saw this: [https://www.lowendtalk.com/discussion/23683/using-another-vpss-ip-for-a-vps](https://www.lowendtalk.com/discussion/23683/using-another-vpss-ip-for-a-vps)

Someone said to get the provider to do modprobe ip_gre.

---

