---
title: "Several networks in the same time but no internet"
date: 2016-05-25
forum: Networking &amp; Wireless
---

### Post by Ptipois59 on 2016-05-25
Hey guys! I'm currently experiencing some troubles with my Ubuntu 14.04.

I explain you the problem : I'm working on an electric car, which is supposed to drive itself. For the moment it works pretty great, but I need an internet access for new functionalities. The whole embedded system is managed by a Ubuntu computer with an i5 to make the calculations. This computer is plugged to a wifi router, so the car broadcasts a Wifi network around it, allowing me to connect via SSH. This router is important because it allows me to connect to other systems like sensors via wired network.

Now I want internet on my car, so I tried to make a wifi hotspot with my phone. I plugged a USB wifi dongle directly on the computer, but I can't have internet with it. The wifi is connected, pings requests are doing well, but the car doesn't have internet.

Though, I don't want to completely destroy the routes, because when I'm in the lab and I need internet for doing stuff like "git clone" or whatever, I plug the router directly on the internet of my wall and it works great.

You've understood, the point is I'd like that Ubuntu check if the internet connexion is available on wlan0, and if not, use eth0. Can you please help me to do it ? I'm not sure of experiencing myself on this project, I've got a presentation on friday and I don't wanna blow the whole thing up :D

Thanks for the help!

---

### Post by Ptipois59 on 2016-05-27
Up ! :(

---

