---
title: "config'ing ndiswrapper for wifi"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by AvengingAngel718 on 2008-07-26
i'm trying to configure ndiswrapper for draft-n wireless and i've hit a brick wall. i had it running in 32-bit hardy but i recently installed 64 bit and since haven't been able to figure it out. i installed ndiswrapper and the amd-64 versions of ndiswrapper utils and ndisgtk, blacklisted the built-in wireless drivers, installed the drivers for my wireless adapter, ran ' sudo ndiswrapper -m' and added ndiswrapper to /etc/modules. however, when i run 'ifconfig' it shows eth0 and l0 but not wlan0....which means for some reason the driver isnt working

i'm stumped. please help :(

---

### Post by Ayuthia on 2008-07-26
> **AvengingAngel718 said:**
> i'm trying to configure ndiswrapper for draft-n wireless and i've hit a brick wall. i had it running in 32-bit hardy but i recently installed 64 bit and since haven't been able to figure it out. i installed ndiswrapper and the amd-64 versions of ndiswrapper utils and ndisgtk, blacklisted the built-in wireless drivers, installed the drivers for my wireless adapter, ran ' sudo ndiswrapper -m' and added ndiswrapper to /etc/modules. however, when i run 'ifconfig' it shows eth0 and l0 but not wlan0....which means for some reason the driver isnt working

i'm stumped. please help :(

Are you using the same driver as you did in the 32-bit?  If so, that could be the problem.  You usually have to use 64-bit drivers with the the 64-bit version of NDISwrapper.  You should be able to confirm this by looking at dmesg from the Terminal.

---

### Post by AvengingAngel718 on 2008-07-26
that could be it, but i used the drivers that came on the cd. i suppose i'll have to dig through google to find the 64 bit version and see if it works with that

if it doesn't, i guess i'll come back and complain some more

---

### Post by AvengingAngel718 on 2008-07-26
ok apparently there are no 64 bit drivers for it. is there any way to run 32 bit ndiswrapper in a 64 bit environment? i'd write the driver myself if i could but i have no idea how :/

---

