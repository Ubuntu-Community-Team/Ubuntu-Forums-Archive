---
title: "Drops Internet"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by catch2two on 2008-09-01
After x amount of time my computer drops its internet connection. All my other computers are running fine so it is not the modem or router. If i restart my computer it comes back. Any ideas to how to get it back without restarting and how to fix this so it does not happen?

---

### Post by nicedude on 2008-09-01
Please give everyone some more info so we can all help.

Type of connection wired or wireless?


If wireless type of adapter and driver you used to configure it?


Version of Ubuntu you are using?


Whether or not you are using ubuntu from a full install or by using Wubi from within windows?


That will help as your problem could be several things that even I can think of and I am by far not the smartest person around here :-)

---

### Post by catch2two on 2008-09-01
Sorry just dealing wit all my woes at the moment. Really regretting my decision to move back to Ubuntu from a working install of fedora. I only use this comp for a few different things and they seem to be things that do not work.

Anyways i will give it a week.

I am using ubuntu studio. Clean install. Wired connection. Linksys router.

---

### Post by nicedude on 2008-09-01
Ok I think I might know what your problem is, your adapter in your PC is being configured to use IPv6 and your router does not support it and instead wants IPv4 to be used. This is getting to be a common problem and will only increase until everyone is forced to buy new routers within a few years that support IPv6. 

You can set this with "sudo ifconfig eth0 inet" assuming eth0 is your ethernet

You may have to run a dhcp command to get your connection up as well.

This problem will affect Fedora as well as soon as they make it the default type of IP address assignment, although I do not even know what was updated in Ubuntu to cause this I had the same problem with this a while back so something did. I don't see why they would do it yet as it will be at least another year or two before this is required and surely anyone who wanted to use IPv6 and has the equipment could just enable it.


Hope that helps and welcome back to Ubuntu

---

