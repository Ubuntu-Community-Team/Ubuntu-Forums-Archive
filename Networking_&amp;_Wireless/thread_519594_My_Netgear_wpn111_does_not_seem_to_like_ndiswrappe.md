---
title: "My Netgear wpn111 does not seem to like ndiswrapper..."
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by DarkED on 2007-08-07
Hi all. I've been bashing my head against the wall for the past day or so. I've got a wpn111 USB wireless card, works great in Windows but not in Ubuntu.

I followed this guide and got it working:

[http://ubuntuforums.org/showthread.php?t=414023](http://ubuntuforums.org/showthread.php?t=414023)

Note, that I did NOT use the 'load_ar_fw' method. I just used sudo ndiswrapper -i netwpn11.inf to get mine going.

It works for a few minutes but then it seems to glitch or something. One minute I'll be able to see my wifi router and all kinds of other routers in the neighborhood, a few minutes later I can only see one or two. If I try typing the ID manually when this happens it won't connect. It just REFUSES to see my router. Other times it says it CAN see the router, it just won't connect to it. Works for hours on end in Windows so I know it's not the card. I also tried unplugging it and plugging it back in but that makes the system hardlock every time. Mouse locks up and capslock key no longer makes the caps light on my keyboard light up. Hardboot gets me back.

I'm using ndiswrapper 1.47 which I compiled and installed from source. I also manually deleted the driver from /etc/ndiswrapper and reinstalled it. No dice. Any ideas?

---

### Post by DarkED on 2007-08-07
Sorry to double post but I've got an update.

Apparently it's not an ndiswrapper or driver issue, it's a usb issue. The wifi card seems to just be the catalyst. When it goes on the blank I realized that my usb essentially locks up. I tried plugging in my ipod and my PSP and nothing happened. Going into the usb section in KDE device manager caused device manager to lock up. Doing a lsusb from shell also doesn't work, the program seems to lock. I also tried to restart ndiswrapper using sudo modprobe -r ndiswrapper, this caused modprobe to lock :) When I tried doing a sudo modprobe ndiswrapper after that it also locked.

Seems to be related to my usb. I have no idea how...

I'm running an MSI PM8M-V w/ a Pentium 4 Northwood @ 3000, 512mb Kingston DDR and a 256mb BFGTech FX5200. Any ideas? :)

---

### Post by DarkED on 2007-08-11
I can't figure out why it works for everyone else but me. I've searched google relentlessly and I cannot find so much as a bug report on this.

After the card stops working if I do ANYTHING that polls the usb subsystem or ndiswrapper, that process will lock. lshw (which locked RIGHT at the 'USB' stage btw) lsusb, modprobe, running device manager, just anything. I tried going into system monitor thinking I could possibly kill these processes and get my usb to come back - no dice. I couldn't even actually kill them. They just became 100% nonresponsive (status as 'Uninterruptible.')

Funny though, when it happens, the only thing that stops working is the card. Anything else plugged in BEFORE the card locks up will continue to work. However, any devices I plug in AFTER it locks won't work.

What is going on here?

---

### Post by Willis2008 on 2008-04-27
Im very new to linux - dont understand it very much :P

I got the WPN111 installed and it finds my router fine. I put in my WPA code but it wont connect. Is this because the router wont allow access or it a problem with the drivers in Ubuntu:confused::confused:

---

