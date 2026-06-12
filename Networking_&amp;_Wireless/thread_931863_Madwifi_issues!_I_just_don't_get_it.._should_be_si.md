---
title: "Madwifi issues! I just don't get it.. should be simple."
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Vaughands on 2008-09-27
I built it, installed it, cleaned it up... I added the ath_pci module to startup but when scanning the area for networks.. nothing! I can't even jack right into a modem or anything... I got some NDSIWRAPPER driver installed now too, could that be overridng the MadWifi driver?

---

### Post by Vaughands on 2008-09-28
Gr.. nobody has an idea?

---

### Post by hellzkeeper1216 on 2008-09-28
I had a similiar issue with wifi when i install xubuntu on my sisters PC. What i did was a little time a research on google and i found that NDISWRAPPER and the windows driver for the make and model of your wireless card are all you need.

here is an example of what i needed to do
[http://forums.fedoraforum.org/showthread.php?t=782&page=6&pp=15](http://forums.fedoraforum.org/showthread.php?t=782&page=6&pp=15)

---

### Post by Vaughands on 2008-09-28
You see the problem is.. I installed the driver on my Windows machine, then copied the SYS and INF file over to my machine and installed a DEB package of NDSIWRAPPER and UTLIS and then NDISGTK. I then added the drivers.. the problem is... it still don't work. Is my driver for windows more universal or something?

EDIT: When listing devices.. my wireless device dosen't appear to be there...
EDIT: It's displayed.. but still nothing. I can't see wireless networks...
EDIT: wlan0 is being picked up as Ethernet?

 Also, its being displayed in Hardware Drivers that I have "Support for Atheroes 802.11 wireless LAN cards" as a proprietary card? So why isn't this working? ><

---

### Post by Vaughands on 2008-09-28
This is blowing my mind...

---

### Post by jpete on 2008-09-28
Not to hijack the thread but I figured I'd give it a bump.  I am also having trouble with MadWiFi.  I'm a rank newbie with Linux and was getting help from another Linux forum but seem to have hit a dead end.

I also did all the ndiswrapper stuff and I think I installed the Windows driver right but still nothing.

The card is a Linksys WMP 110 PCI.

If anyone has any suggestions, it would be greatly appreciated.

Thanks

---

### Post by Vaughands on 2008-09-28
Yeah, I wouldn't consider this a hijack either... I just can't seem to get it to work.. and I'm sure I'm not the only one.

---

