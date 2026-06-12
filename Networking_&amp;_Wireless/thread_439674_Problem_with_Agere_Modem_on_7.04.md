---
title: "Problem with Agere Modem on 7.04"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by bulletshot60 on 2007-05-10
I have installed all the necessary drivers for my modem, and the driver is operational.  However, I don't understand how to manuver my way through the new networking window.  I am fairly new to linux, started about 6-7 months ago, but can do most things.  I have set up my dial-up connection which worked fine under 6.06, but now it won't even dial!  Every time I try to connect nothing happens no sound, no dialing, nada, nada, and more nada.  And every time I check my preferences, my modem is unselected and some wireless card is select, which I don't even have one to my knowledge.  Also, whenever I check my modem properties, it is on pulse instead of tone.  I have no clue whats wrong or what to do. :confused:  Any help that can be given will be greatly appreciated.  (BTW, I am on a dual-boot system, and am being forced to use Windows to access this site for help.  So, it make take some time for me to reply as to whether or not your advice helped.)  God Bless and Jesus Saves.

---

### Post by phidia on 2007-05-10
In a terminal type pppconfig <enter> and complete the configuration script.

after doing that try using pon (type pon in terminal, type poff to disconnect) Try it with sudo in front if it doesn't work. To get a gui dialer, once you get connection, do sudo apt-get install gnome-ppp

---

