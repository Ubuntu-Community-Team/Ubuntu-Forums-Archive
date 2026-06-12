---
title: "using static ip through my router"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by eremk on 2007-04-23
Hi,
I have an edgy-installed desktop, which is assigned a static IP address. But due to the weird location of ports in my office, I need to use the ports behind the wireless router to plug my ethernet cable in. Is there any way I can do this, and still use my static IP address?
Thanks,
Erem

---

### Post by Jussi Kukkonen on 2007-04-23
You can always use a static IP, but be aware that the IPs inside your local network are not the same as the 'outside' IP that the rest of the internet sees...

If I didn't answer your question, you may want to explain your problem a bit further (I'm not 100% sure what the problem is).

---

### Post by eremk on 2007-04-23
i basically want to use the port behind the router like a port on the wall. i don't want the router to assign me an ip address; i want to use the static ip address that i am assigned to.
maybe this would make it more explicit: my static address is 130.132.xx.xx, but the router assigns me 192.168.x.x. i would like to be connected to the ports on my router, but still keep 130.132.xx.xx.

---

### Post by Jussi Kukkonen on 2007-04-25
It doesn't work like that. To anyone outside of your LAN it will look like your machine is 130.132.xx.xx, so I don't think you'll have any problems.

If you want to use a static IP inside your LAN and not just pick whatever the router throws at you, that should be possible. Just check your routers manual (or web config) for the allowed IP range and set a static IP.

---

