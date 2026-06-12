---
title: "Wireless Help"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by nightimexscene on 2007-05-11
I'm using an ACER ASPIRE 3680 notebook pc. I recently installed linux ubuntu, this it the first time Im stepping foot outside a microsoft operating system, anyways.. linux does not detect and install drivers for my wireless internet card. can anyone help me with this problem please? 

thanks.

---

### Post by ZCarPilot on 2007-05-11
This is a pretty common problem.  Apparently the firmware needed by some popular wireless network adapters is proprietary and they haven't been reverse engineered yet.

One possible process is as follows:

1) Find out which wireless adapter you have using 'lspci' in a terminal window.

2) Search for help, both here and from google, on your particular adapter, using something like "bcm4318 Feisty wireless network" or similar keywords (the "bcm4318" is a wireless nic used in many modern laptops - it may or may not be the brand and model in *your* laptop).

3) Look at the man pages, again in a terminal window, for ndiswrapper, network-manager, interfaces, ifconfig, iwconfig, and other commands that these man pages refer you to.

Without the specifics of your particular situation, it's impossible to be more specific than this.

Good luck!

---

