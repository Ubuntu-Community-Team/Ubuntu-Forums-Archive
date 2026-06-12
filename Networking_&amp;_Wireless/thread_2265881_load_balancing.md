---
title: "load balancing"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by nima6 on 2015-02-18
hello

I want to know how balancing 2 different link from 2 isp (link1- four meg per second  link2-16 meg per second)  with Ubuntu server

and i want to use link1 permenantly and link2 from 9:00 am-9:00pm 

does it have any way

---

### Post by tgalati4 on 2015-02-18
This could be set up within your router that your server connects to.  If your connections are directly to your server (no router attached) then you might want to "[bond]("https://help.ubuntu.com/community/UbuntuBonding")" the two ethernet connections together and turn off one connection after 9 pm and turn it on at 9 am using a cronjob and the *ifup* command and two different /etc/network/interfaces files.  One file would have two static network interfaces defined.  The second file would only have only one network interface defined.  Use *ifup* to switch between them at the appropriate time.

Welcome to the forums.

---

### Post by nima6 on 2015-02-19
[QUOTE=tgalati4]You are quite welcome![/QUOTE]


hello

another question
when I type 
crontab -e


what command should I type to turn of eth1 in 9:00

---

### Post by tgalati4 on 2015-02-19
Something like:

```
00 9 * * * root ifup -i /etc/network/interfaces_2_wans
```

Assume eth0 runs 24 hours per day and eth1 runs from 9 am to 9 pm:

```
00 21 * * * root ifdown eth1
```

You could edit the standard configuration file /etc/network/interfaces to include both eth0 and eth1 configuration and use a simpler command:

```
00 9 * * * root ifup -a
```

This will bring up all network cards specified in the default /etc/network/interfaces file.

---

