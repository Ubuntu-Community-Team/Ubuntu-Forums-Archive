---
title: "No internet connection with static ip at start - have to switch to automatic"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by randalotto on 2008-04-05
I'm sure there is a simple explanation to this, but I don't know what it is...

I want to use a static IP address. When I boot up the computer, it won't connect if I have the static IP manually configured.

If II go to the internet settings and change it over to automatic, it will work. After that, I can change back to my static ip and it will also work.

What do I need to do so that the static IP will work without having to go back and forth every time? What's happening during that automatic, DHCP assignment that I'm missing?

---

### Post by alan34 on 2008-04-05
It might be that your router is set up as a nameserver so that will not accept a static IP address.
I would have a look at the settings on the router.

I have used the live CD on a network with static IP addresses and that worked fine.

---

### Post by superprash2003 on 2008-04-05
yes, disabling DHCP on the router and then entering static ip may help

---

