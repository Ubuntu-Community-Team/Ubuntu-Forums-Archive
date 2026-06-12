---
title: "QOS Based on interface?"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Xenolard on 2008-06-05
Hello all,

I have setup an Ubuntu-based router. Network setup as below.

eth0 - This is the internal netowrk. 172.16.10.0/24
eth1 - This is the network on which the modem sits. Modem has DHCP and sets the IP for this interface. 192.168.1.0/24 though.
eth2 - This is my DMZ. My xbox lives here. 192.168.2.0/24

My firewall is done via a FWbuilder made script and works well, however I would like the xbox (on eth2, the DMZ) to have priority over all the other traffic. Does anyone know of a method which I would be able to implement this? 

Thanks, Mark.

---

### Post by Xenolard on 2008-06-07
No ideas?

Ok well I suppose I could do it either MAC/IP based or protocol based which I suppose is what QOS is normally done.

This is as I use fwbuilder to make the script; i'm not sure how easy it'd be to make a classification and proritising script to either load after or in with the fwbuilder script.

Hope that made sense - any ideas?

Thanks

---

### Post by SpaceTeddy on 2008-06-07
these are the only pages i know that kind of explain what you want to do. 
The first is an English how-to, the second is a **German** example of how to do something. I don't know how good your German is (or if it even exists), but i though i'd put it in anyways. The Problem is that both solution only control outgoing traffic, not incoming. For ingress traffic shaping, you need something like an [[COLOR="Blue"]intermediate queneing device[/COLOR]]("http://www.linuximq.net/").

here are the howtos:
[[COLOR="Blue"]http://www.linux.com/base/ldp/howto/Traffic-Control-HOWTO/index.htmlt[/COLOR]]("http://www.linux.com/base/ldp/howto/Traffic-Control-HOWTO/index.htmlt")
[[COLOR="Blue"]http://www.kabelverhau.ch/elwms/de_shaping.php[/COLOR]]("http://www.kabelverhau.ch/elwms/de_shaping.php")

---

### Post by Xenolard on 2008-06-11
That's cool. Thankyou for your input. I'll take a look and get back to you.

---

