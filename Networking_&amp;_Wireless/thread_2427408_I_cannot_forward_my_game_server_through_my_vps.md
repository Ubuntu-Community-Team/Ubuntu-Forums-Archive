---
title: "I cannot forward my game server through my vps"
date: 2019-09-21
forum: Networking &amp; Wireless
---

### Post by ikinnojo on 2019-09-21
This is an odd one but I made a vpn on my vps then on my home machine running 19.10 desktop VM it's fully routed through the VPN and all ports are open, but when I go to connect to the game server it doesn't show up, am I missing a step? Is this impossible, do I have to do port forwarding in Linux itself or is it fine to use my hosts controll panel, please help, much luv <3

---

### Post by SeijiSensei on 2019-09-22
I'd check to see whether the server program has an option to listen to specific devices.  It might not know to listen to tun0 or whatever device the VPN uses.  

If you have a direct VPN tunnel to the server, you shouldn't need any port forwarding.  You should just be able to address the server's VPN tunnel IP address.

---

