---
title: "eth0 not autostarting"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by larsemil on 2007-06-06
i just did a clean install on my third ubuntumachine. i have two on my own and my father finally decided to join the free world.

everything worked fine except some problems with eth0. it does not autostart when starting the computer. it says it is active but it doesnt have a ip. 
clicking on the networkicon in the panel and choosing cable connection starts it up. also it starts up doing sudo ifdown eth0 and then a sudo ifup eth0. then i get a ip and everything is working like a charm. but as soon as i reboot the computer i once again have to manually activate the connection. 

this is my /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by carolinason on 2007-06-07
In the gui network manager is the adapter checked to start on boot. It could the startup script is not running the proper ifup command.
I've had this issue with the live cd, but not with a hard drive install.

---

