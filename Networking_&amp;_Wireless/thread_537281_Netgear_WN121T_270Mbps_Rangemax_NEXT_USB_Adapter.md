---
title: "Netgear WN121T 270Mbps Rangemax NEXT USB Adapter"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by Logical on 2007-08-28
Will the Netgear WN121T 270Mbps Rangemax NEXT USB Adapterr work with ubuntu? Will i need new drivers installed for it to work?

---

### Post by brettnak on 2007-09-23
It will work with ndiswrapper.

I still can't figure out how to get the gnome GUI wireless thing to work with it though.  It works if you go through the command prompt or if you use gtkwifi.

---

### Post by safirr on 2008-01-23
I too have the same USB adapter, cant seem to find the .inf file to install the driver using ndiswrapper
I have the windows driver in .sys format
[LIST]
[*]Is there a way to install the .sys driver using ndiswrapper?
[*]or anyway to extract the .inf file from the windows setup.exe installer program?
[/LIST]
I have already tried Unshield on the Setup.exe. .  but it doesnt work
Please help. .  I have searching google for a week for a solution. . but couldnt find any solution to this problem.

---

### Post by Hightide on 2008-01-23
> **safirr said:**
> I too have the same USB adapter, cant seem to find the .inf file to install the driver using ndiswrapper
I have the windows driver in .sys format
[LIST]
[*]Is there a way to install the .sys driver using ndiswrapper?
[*]or anyway to extract the .inf file from the windows setup.exe installer program?
[/LIST]
I have already tried Unshield on the Setup.exe. .  but it doesnt work
Please help. .  I have searching google for a week for a solution. . but couldnt find any solution to this problem.

HI safirr
this s along shot but have a look at this thread about installing the Netgear WG111v2 usb adaptor,

[http://ubuntuforums.org/showthread.php?t=590942#6](http://ubuntuforums.org/showthread.php?t=590942#6)

regards
:)

---

### Post by safirr on 2008-01-24
Thanks for your help. .  but that post does not solve my problem ..  I know how to install using ndiswrapper.. my problem is I dont have the .inf file that ndiswrapper needs . . my wireless card uses Marvell chipset ..  and I have the .sys driver file from windows as the driver cd contains only a single file setup.exe.

---

### Post by Jammin80503 on 2008-04-21
bump.
I'm having the same exact problem :P

---

### Post by daimudan on 2008-04-26
I'm in the same boat as well.  It ends up being the MRVW245.sys.  Any ideas out there?  :(

---

### Post by Bubblebeard on 2008-05-20
Posting this reply a bit late for the original recipient but just for completion (so people like me don't have to waste all day trying to get it and can just find it when they search google or the forums), here is a link to the .inf and .sys files:

[http://www.freewebs.com/duckles/WN121T.inf](http://www.freewebs.com/duckles/WN121T.inf)
[http://www.freewebs.com/duckles/WN121TXP.sys](http://www.freewebs.com/duckles/WN121TXP.sys)

or go to [http://www.freewebs.com/duckles/netgearwn121tdriver.htm](http://www.freewebs.com/duckles/netgearwn121tdriver.htm) for both in one spot.

---

