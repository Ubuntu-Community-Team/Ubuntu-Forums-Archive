---
title: "Trying to configure Linux-Windows network with no router, but 2 ethernet cards."
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by Dawnshadow on 2006-09-29
All right. I have two computers, one with Ubuntu Linux (KDE, so it's closer to Kubuntu now,) the other a laptop with Windows XP. (If my wireless card worked with Ubuntu I'd use it, instead, but until then....) The Linux desktop has two Ethernet cards. Eth0 has a normal Ethernet cable to the wall jack, the other (eth2) goes to the laptop with a crossover cable. I've installed Firestarter, Samba and DHCP, fiddled with the network settings, and even ordered books on the networking from the library. Nothing seems to help. I'm just trying for file sharing now, not shared internet, although the shared internet would be a nice touch.

They shared files easily when I had the router at home, but here it's not an option; the school I go to has banned wireless routers in their dorms and the spare router I have is, indeed, wireless. Does anyone know of a step-by-step tutorial for configuring these computers?

---

### Post by BoneKracker on 2006-09-30
This ought to help:
[https://wiki.ubuntu.com/BridgeConnections?highlight=%28bridge%29](https://wiki.ubuntu.com/BridgeConnections?highlight=%28bridge%29) 

You don't NEED to run a dchp server to make this work, you could just use a static IP address for the LAN (desktop-to-laptop) circuit.  If you're running XP, your laptop's networking should fallback to APIPA (it will start trying IP addresses in a certain range until it finds one that's not being used).  Behind where you configure for dhcp, look at the "alternative connection" tab or whatever it's called.  Just make sure the desktop's eth2 and the laptop's "alternative connection" settings coincide.

Also, if the crossover cable is home-made, you may want to test it.

---

### Post by Dawnshadow on 2006-10-01
Cool. I'll try it tomorrow. Thanks. :)

---

