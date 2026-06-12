---
title: "How to configure Linux as a Gateway ?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by honey_bee on 2010-10-13
Hi,
           I want to know the configuration steps for building Linux machine as a gateway.
 
 
**Network A** [COLOR=blue]192.168.1.0[/COLOR] .......<...[COLOR=red]Gateway[/COLOR]......> **Network B** [COLOR=green]176.16.0.0[/COLOR]
[COLOR=#008000][/COLOR] 
[COLOR=black]thanks in advance[/COLOR]
[COLOR=black]honey[/COLOR]

---

### Post by alphacrucis2 on 2010-10-13
> **honey_bee said:**
> Hi,
           I want to know the configuration steps for building Linux machine as a gateway.
 
 
**Network A** [COLOR=blue]192.168.1.0[/COLOR] .......<...[COLOR=red]Gateway[/COLOR]......> **Network B** [COLOR=green]176.16.0.0[/COLOR]
[COLOR=#008000][/COLOR] 
[COLOR=black]thanks in advance[/COLOR]
[COLOR=black]honey[/COLOR]

The first thing you have to do is enable ip forwarding to turn the machine into a router. This is a setting in /etc/sysctl.conf which you will need to edit (requires admin rights) e.g gksudo gedit

Namely this bit:

```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1
```

Then you just configure your ethernet interfaces with the addresses and subnet masks you want and add any static routes via the route command.

Forgot to say. I believe the /etc/sysctl.conf file is only read during boot up or network restart. Probably easiest to reboot to make the change effective.

---

