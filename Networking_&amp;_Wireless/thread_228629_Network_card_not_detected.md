---
title: "Network card not detected"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by kthakore on 2006-08-03
My network card is set up on eth0 with static ip address, and my internet works but, several programs can detect it for example:

1)NetworkManager Applet
2)arp
3)bitorrent
4)unreal 2004

please help!

---

### Post by kthakore on 2006-08-03
also when i run pppoeconf I get this error

```
Timeout waiting for PADO packets
```

and 

```
Sorry, I scanned 1 interface, but the Access  Concentrator of your provider did not respond. Please  check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.    
```

I googled the error and I found this solution but I have no idea how to carry it out 

```
this may not be a solution for everybody, but it took me a long time to realize:
i get that message, when i use rp-pppoe under a kernel different from the one it was compiled against.this is true at least if it comes down to the 2.4 opposed to a 2.6 kernel, but may be even among 2.4 kernels? just thought i'd point it out, since the message does not exactly have "kernel problem" written all over it :)
good luck, conrausch
```

and synaptics can't download anything. Also I am behind a router

---

### Post by kthakore on 2006-08-03
update:

ettercap can't even fine the interface. HELP!!!!

---

