---
title: "Unusual problem with ufw"
date: 2017-07-21
forum: Networking &amp; Wireless
---

### Post by kylefromintegra on 2017-07-21
Hi all,

I'm having issues with ufw blocking incoming connections to Tomcat. Here is the result of ufw status:

```
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
8080                       ALLOW       Anywhere
443                        ALLOW       Anywhere
80                         ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
8080 (v6)                  ALLOW       Anywhere (v6)
443 (v6)                   ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)
```

Tomcat is listening on port 8080. However, when I try to connect to it, my connection is rejected, and I see the following in dmesg:

```
[  322.588784] [UFW BLOCK] IN=eth0 OUT= MAC=[REDACTED] SRC=[REDACTED] DST=[REDACTED] LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=29303 DF PROTO=TCP SPT=61308 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0
```

Even though port 8080 is explicitly allowed, ufw is still blocking it. However, once I run ufw disable, incoming connections succeed. In addition, even after I run ufw enable to turn it back on again, incoming connections STILL succeed. Only after rebooting does it go back into the broken state of denying the connections. This happens whether I reboot with the firewall disabled OR enabled. In addition, running ufw reload immediately after startup tells me the firewall is inactive, even though ufw status tells me it is active.

So, long story short, ufw seems to be in a weird invalid state immediately after reboot. Disabling ufw in /etc/ufw/ufw.conf doesn't help. Can someone please help me figure out what's going on here? Is there a daemon that's not getting started when it should be, even though the ufw iptables rules are added?

---

### Post by kylefromintegra on 2017-07-21
I figured out the problem. There was a garbage set of rules in /etc/iptables, and both iptables-persistent and ufw were enabled at the same time. I ran the following to disable iptables-persistent and enable ufw only:

```

sudo update-rc.d iptables-persistent disable
sudo ufw enable

```

Now everything is working as expected.

---

