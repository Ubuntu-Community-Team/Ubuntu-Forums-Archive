---
title: "How to connect from the internet to a X11VNC Xubuntu PC?"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by ubu-for on 2014-08-28
I would like to connect from the internet with my MacBook to my Xubuntu PC some miles away.

I.

I've installed Chicken of the VNC on my MacBook and X11VNC on my Xubuntu PC. The Xubuntu PC is behind a TP Link Switch and a AVM FritzBox (DSL Modem with dynamic IP).

If I connect for testing my MacBook to the TP Link Switch and enter the IP (192.xxx.xxx.xx) of the Xubuntu PC (righ corner "connection information") into Chicken of the VNC everything wokrs fine, but if I'm at home and try to connect through the internet the same way, I get the following error from Chicken of the VNC: "Could not connect to server 192.xxx.xxx.xx The connection attempt timed out"

I'm pretty new to networking but I guess, I need first of all the current IP of the AVM FritzBox and probably the IP of my Xubuntu PC but which way do I have enter both addresses? Maybe this way xx.xx.xx.xxx:192.xxx.xxx.xx (1. AVM IP + 2. Xubuntu IP)?

II.

I've found a second method with SSH but haven't tried it because I don't know how to forward a port and where. In the Switch or the AVM FritzBox (DSL modem)?
"sudo apt-get install openssh-server byobu
If you plan to manage your mining rig remotely over the internet, you’ll need to forward port 22 on your router to your miner."

III.

If someone knows a better or more secure way to connect through the internet to my Xubuntu PC with dynamic IP addresses, please let me know!

THX :)

---

