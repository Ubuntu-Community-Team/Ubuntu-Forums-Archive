---
title: "Wireless Asst works in Kubuntu not in Xfce"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by RHorse on 2007-08-03
After installing Xubuntu over Kubuntu and logging into the Xfce desktop I found that Wireless Asst will not let me connect to my wireless router.  it displays the available networks, but after I have set up the settings (DHCP, WEP), and try to connect it instantly says *Connection Failed* , i.e. less than 1/2 second.  However after logging out of Xfce and into Kubuntu, everything works normally.  Anyone else have this problem?

Addendum: I finally figured out what was wrong: I have to start wlassistant with *sudo*.  For some reason the prompt to run wlassistant as sudo does not work in Xfce, you have to run it with *sudo* at the command line.

*R* *H*

---

