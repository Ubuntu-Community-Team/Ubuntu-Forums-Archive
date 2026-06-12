---
title: "Ralink 3060 installation with no wired connection"
date: 2014-07-04
forum: Networking &amp; Wireless
---

### Post by donthurtme2 on 2014-07-04
I'm going to install Lubuntu on my parent's old PC (AMD 2200+ <1.8GHz>, 1GB RAM, GeForce FX 5200) since new Linux Mint doesnt work with this GPU :(
I tried on LiveCD and looks not as good as Mint, but should be ok for my parents. The only problem is that it doesnt detect wi-fi network so propably I will have to install driver from Internet. But I can't wire this old PC to router which is on the other floor, don't ask if maybe I can move PC/router, no way.
However, I can use my laptop to get proper drivers (.deb package?), then copy and install on PC. The question is which driver and how to do that?
Wi-fi card is Ralink 3060.
I'm using Debian on my own laptop, so I'm not totally newbie on GNU/Linux, but I'm far from good yet.
Sorry for bad english, not native :(

---

### Post by squakie on 2014-07-05
Boot PC with the live media and select "Try Ubuntu".  Does it show as wireless available in Network Manager?  

Next, we would need to know the wireless adapter chipset.

If this is an internal wireless card:

- open a terminal window (ctrl/alt/F1)
- log in with your normal userid and password - nothing is echoed to the screen as you type your password - press enter after each

Now you should be at a prompt that ends in a dollar sign ($).

- type:  lspci | grep Network <press enter> and post the output back here


If the adapter is a USB dongle, do the following:

- open a terminal window (ctrl/alt/F1)
- log in with your normal userid and password - nothing is echoed to the screen as you type the password - and press enter after each

Now you chould be at a prompt that ends in a dollar sign ($).

- type:  lsusb <press enter> and post the output back here

We can go from there to determine the driver that is actually needed and guide you on downloading it.

---

