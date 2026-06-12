---
title: "What do I use to set up my wireless router in Linux?"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by i8bugs on 2007-06-18
My wireless router is working fine, but it is only broadcasting and receiving.  It is a Belkin wireless "G".  Since I cannot use the setup CD sent with my router (windoze only), I do not know how to name the router and how to setup security (and whether it uses WEP, WPA,  or what.).  I want to be able to set my password and encryption key, and remove it if necessary.  I'm using Fiesty 7.04.

I looked at networkmanager, but didn't see the controls I thought I should see.  I'm sure there is an easy solution, just don't know where.

i8bugs

---

### Post by Sand Lee on 2007-06-18
Lucky for you i've got the same router (belkin54g)? To access the settings enter 192.168.2.1 into your browser.

---

### Post by p_quarles on 2007-06-18
Actually, the exact address of the router depends on your network setup. Mine, for instance, is 10.0.0.1. In any case, Sand Lee's guess is probably right, but if that doesn't work, you should be able to find the address by going to System > Administration > Network, and then hitting the DNS tab. It should show the router's address there.

Basically, most routers and gateways have built-in "web" sites that allow you to administer them from your network. That's why you type in the local network address for the router.

---

### Post by i8bugs on 2007-06-20
Perfect.  Worked as advertised!
Sand Lee was correct on the address.
I love quick easy fixes!!
i8bugs

---

