---
title: "rtl8187l Linux drivers work mostly"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by sgt_urankar on 2008-01-24
Well after many days and nights I got the linux drivers working on fiesty.  One evening I emailed realtek and the responded with an attachment containing the latest drivers.  After getting them onto the desktop I sudo su-ed on the cli.  ran the ./makedrv and errored out, then opened the script to see what the script did.  After review I just did the process manually; make clean, make in each of the 2 required directories. then copied fron he script one line at a time (copy past) into the cli. after compleating that the wireless connection started working.  Now my signal strength is not steady it does alot of uo and down.  I did not however deal with the supplicant file for wpa or wep.  Now I have a working usb adapter by encore (ENUGWI-G2).  My next step is to try the same thing with a Trendnet pci card that is rtl8185.:)

---

