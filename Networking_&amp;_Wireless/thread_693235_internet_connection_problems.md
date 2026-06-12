---
title: "internet connection problems"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by turnerpond on 2008-02-10
I am unable to get on the internet (wired or wireless) with Ubuntu 7:10 on a lenovo T61, dual boot with WIN XP.  I've tried advice of threads to add default "gw" with the result of "could not resolve."  I also tried  sudo iptables-F with no result.  My wireless card is Intel pro...3945ABG.

I woud appreciate any help.

turnerpond

---

### Post by nickoli_02 on 2008-02-10
Let's work on your wired connection first. I'm assuming you're connecting through a router. Make sure your ethernet cable is connected and your router is on. Now open a terminal and post the output of:

```
ifconfig
```

If the second line of the interface paragraph is something like "inet addr:192.168.x.xxx" then your router gave you an IP address. Now see if you can ping your router:

```
ping 192.168.1.1
```

I'm assuming your router IP is 192.168.1.1. If you don't have an IP address assigned you can do this:

```
sudo killall dhclient
sudo dhclient eth0
```

where eth0 is the wired interface connected to your router. Hope this helps

---

### Post by turnerpond on 2008-02-14
Thanks for all your help.  I tried your suggestions and was ultimately successful.

Thanks again!    turneround

---

