---
title: "No wired network connection"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by $il on 2007-09-17
Hello all

I have a small windows network at home and it works fine.  I can share files and printers.  Some time ago wanted to try linux (PC Linux) but so many things went wrong so I gave up.  Now I heard about Ubuntu and I tried the live CD.  All woreked fine.  Next day when I ran the live CD I had no connection to the router.  Even it said connected I still didn't have access to the router.  When I checked the IP address it was 0.0.0.0.  Tried to set it manualy but didn't work.  When I boot from the hard drive (windows) it's OK.  The hardware is compatible as it ran the first time.  My networkcard is an onboard "realtek PCI LAN8101L"  PLEASE help before I give it up again.  I really had enough of windows.

---

### Post by noob12 on 2007-09-17
If you can, try to run **sudo ethtool eth0** while booted in Ubuntu and see if it says that there is a line that says **link detected** and whether it says **yes** or **no**

---

