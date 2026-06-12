---
title: "Panel disappeared when drivers installed (Ubuntu test)"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by pfooca on 2011-05-03
Dear community,

Absolutely new to Ubuntu and installed video driver for Nvidia. When I restarted, all the panels disappeared and cannot access terminal with CTRL+Alt+T (orF2). 
1. How can I access the terminal from a blank desktop?
2. Once I have access to the terminal shall I just run the commands mentioned in the other forums?
                a. killall gnome-panel

Thanks for any help

---

### Post by edm1 on 2011-05-04
It is not ideal but i recommend not using the binary nvidia driver you have installed, it seems to be causing problems for a lot of people. The open source driver is actually quite good. It has alot of features the binary one doesnt (except it doesnt support 3D). You can acheive this by logging out, at the login screen once youve selected your user name select Ubuntu Classic (No Effects) at the bottom, log in, open synaptic package manager, search 'nvidia', removed any packages installed that begin with 'nvidia' except nvidia-common, and apply. You may then need to open the terminal and reconfigure xorg.

> sudo dpkg-reconfigure xserver-xorg

---

