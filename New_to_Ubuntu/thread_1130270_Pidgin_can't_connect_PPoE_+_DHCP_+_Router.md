---
title: "Pidgin can't connect: PPoE + DHCP + Router"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Veehmot on 2009-04-19
I have 3 machines connected to a Router ( Noganet TEI6608 ).
* 1 Windows XP x32 SP3
* 1 Windows XP x64 SP2
* 1 Ubuntu Intrepid 8.10 x32

The thing is, I couldn't run Windows Live Messenger in XP Machines, but I downloaded a program called TCP Optimizer ([http://www.speedguide.net/downloads.php](http://www.speedguide.net/downloads.php)) and I selected PPoE checkbox and selected my correct Network Card, clicked ok, reboot, and Messenger connected.

Now, I can't have that program in Ubuntu, so I was wondering there's a trick I could do to make pidgin run. HTTP is working, since I'm writing this in Ubuntu machine, problem maybe comes from ports, and I don't think it comes from router config, since Windows machines are running OK, and i'm not explicitly opening Windows Live Messenger port in the config.

---

### Post by Veehmot on 2009-04-20
Any help? :P

---

### Post by Veehmot on 2009-04-22
I just resolved this:

```
sudo ifconfig eth0 mtu 1492
```

---

