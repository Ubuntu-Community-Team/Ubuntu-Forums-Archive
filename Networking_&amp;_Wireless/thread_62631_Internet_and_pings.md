---
title: "Internet and pings"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by Mozzer on 2005-09-05
Having finally sorted out my wireless card using Ndiswrapper, I find I can ping my router, open up it's configuration page and ping other computers on the network. However, when it comes to internet pages, no can do.

Firefox always says "xxx could not be found. Please check the name and try again." And when I try to ping somewhere like google it just tells me unknown host or something like that (which I assume means it can't resolve the IP).

I've tried changing my Firefox connection settings to auto detect but obviously this is more of a general problem as Terminal cannot ping either.

Any suggestions/solutions will be much appreciated.

Mozzer

---

### Post by s_p_a_r_k_y on 2005-09-05
it seems like its not "resolving" other internet addresses. Do you have a static or DHCP ip address? What does ```
 host yahoo.com
``` give you? Also try ```
traceroute google.com
```. That helps you figure out where the packets are getting stuck

---

### Post by cwaldbieser on 2005-09-05
[QUOTE=Mozzer]Having finally sorted out my wireless card using Ndiswrapper, I find I can ping my router, open up it's configuration page and ping other computers on the network. However, when it comes to internet pages, no can do.

Firefox always says "xxx could not be found. Please check the name and try again." And when I try to ping somewhere like google it just tells me unknown host or something like that (which I assume means it can't resolve the IP).

I've tried changing my Firefox connection settings to auto detect but obviously this is more of a general problem as Terminal cannot ping either.

Any suggestions/solutions will be much appreciated.

Mozzer[/QUOTE]

If you can't resolve the host name, you probably need to correct you /etc/resolv.conf file.

If your router is IP address 192.168.0.1, then /etc/resolv.conf probably needs to contain:
```
nameserver 192.168.0.1
```

---

### Post by Mozzer on 2005-09-05
Cheers, cwaldbieser. Editing resolv.conf did the trick. It was completely blank, so I just put in nameserver and the router IP address and bam, it works straight away!

I am now on the internet using linux for the first time ever. Hooray!

---

