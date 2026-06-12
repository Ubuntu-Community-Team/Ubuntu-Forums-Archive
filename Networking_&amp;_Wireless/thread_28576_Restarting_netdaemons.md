---
title: "Restarting netdaemons"
date: 2005-04-20
forum: Networking &amp; Wireless
---

### Post by ifrflyer on 2005-04-20
Hi,
Ubuntu 5.04 on a Compaq presario centrino V4020; most things work out of the box HOWEVER I have problems switching from one wifi network to another. The gui Network config tool hangs or simply times out, forcing me to restart the network. However I cannot seem to figure out HOW to restart the network on this without restarting the machine (restarting the machine often works to connect to a different network)!! 

To restart the network, I have tried, repeatedly, combinations of:

/etc/init.d/networking restart
/etc/init.d/networking stop
/etc/init.d/networking start

and none seem to affect the issue. I hear tell of a /usr/sbin/netdaemon - could this be what I'm after?

Thanks in advance,
Jack

---

### Post by diebels on 2005-04-20
use ifdown and ifup

---

### Post by ifrflyer on 2005-04-21
Thanks for that. . . .

---

### Post by ifrflyer on 2005-04-21
Nope, i am still having difficulties, though likely my usage of ifdown and ifup. I tried 

```
ifdown eth0
``` 

and was told that eth0 was not configured. 

I tried

```
ifup eth0
``` 

and saw that it was listening for DHCP...BUT on the old network

Can you please help me with the proper syntax? My intent is to completely unload ALL network drivers and then reload them anew, so that I might join a wireless network without having to restart the machine.

---

### Post by diebels on 2005-04-21
[QUOTE=ifrflyer]Nope, i am still having difficulties, though likely my usage of ifdown and ifup. I tried 

```
ifdown eth0
``` 

and was told that eth0 was not configured. 

I tried

```
ifup eth0
``` 

and saw that it was listening for DHCP...BUT on the old network

Can you please help me with the proper syntax? My intent is to completely unload ALL network drivers and then reload them anew, so that I might join a wireless network without having to restart the machine.[/QUOTE]
 eth0 is usually a wired lan card. My wireless is ath0, but there are others I think. "ifconfig" or "iwconfig" should list them.
so something like
"ifdown ath0 && ifup ath0"
should get it restarted
A shame "/etc/init.d/networking restart" does not work.

---

### Post by ifrflyer on 2005-04-23
Thanks for that; I'll give it a shot

---

