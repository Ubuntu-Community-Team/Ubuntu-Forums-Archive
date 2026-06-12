---
title: "[SOLVED] Not getting a network adress after every boot"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by GSMX on 2008-11-28
Hey,

I got my Acer Aspire 7520 working immediately with ndiswrapper on x68-64, but something very strange happens: in +/- 1 out of 10 boots, the network applet says it keeps on trying getting a network address (dhcp), but fails to, sometimes one reboot is sufficient to get a connection, sometimes it takes 3-4 reboots.

Any thoughts?

I found out that if I don't see the blue bars of a connection after login, I know it's time to reboot again :p

---

### Post by GSMX on 2008-12-02
*bump*

Today I had to reboot 7 times! It becomes very annoying

---

### Post by superprash2003 on 2008-12-02
well.. im not sure exactly why.. do you have multiple machines on your network?? have you given a decent DHCP range?? use static ip

---

### Post by GSMX on 2008-12-02
the DHCP range is 10.0.0.150-170, but i think the problem is in ubuntu, because the other machines on the network have no problems getting an address. (windows machines) I already gave myself a static ip, but that didn't help...

---

### Post by superprash2003 on 2008-12-03
when you entered static ip , did you mention gateway ip etc .. post output of /etc/network/interfaces

---

### Post by GSMX on 2008-12-03
hmmm... It looks like it's solved... I got into the configuration of our router and gave my MAC-address a static ip (or "locked it" as it's called in the routerconfig)

Have had no troubles since

Thanks anyway to everybody :popcorn:

---

