---
title: "Inserting WRT between PC's"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by DarkW0lf on 2007-12-14
What I am trying to do:

OW <-- ppp0 --> PC <-- eth0 --> WRT54G v3.03 <-- wlan0 --> Laptop

My typical search on the GRC fourms turned up that I may need a IP route to the router because the gateway PC is set to use the dialup as the default route to the internet.

The user posted the Windows command not knowing I was a Linux user, I haven't heard from the Linux users there yet. The question I have is if this right and how to make the route permanent, the windows command has a persistent setting but I can't find a persistent setting in the route man page. He suggested I may need to use a boot script but I don't know where or what such is located for a persistent IP route.

Make sense or am I not clear ?

---

### Post by jflaker on 2007-12-14
Are you looking for something like this?

[http://www.easylivecd.com/english/cdrouter/](http://www.easylivecd.com/english/cdrouter/)

Use an old system.  Unstated in the front page of the site, but since the distro has a DHCP server, you would shut off DHCP on your router.......

---

### Post by DarkW0lf on 2007-12-22
No, I just want to use the WRT to connect the laptop to my LAN and through the gateway pc to the dialup internet access. The gateway will just use ipmasq and dnsmasq. I have done this with a crossover cable between the laptop and pc but I want to use the WRT so I can have the laptop elsewhere.

---

