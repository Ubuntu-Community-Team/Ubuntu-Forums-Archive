---
title: "Is there a truely Linux supported WiFi router"
date: 2015-09-13
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2015-09-13
Just got burned on a Linksys WRT54GL router.  Setup CD only for Windows and, when router went into nonworking mode (powerlight flashing continuously), Linksys techs admitted that router was not Linux ready even though it had the Linux Penguin on the box nor were they trained in Linux.

Is there a Wifi router with true Linux support?

John

---

### Post by coffeecat on 2015-09-13
Yes, any router including a Linksys. Those setup CDs are just simplified wizards for those unsure of how to configure a router properly. Use the web interface configuration to set up your router. If I remember correctly, the address for a Linksys is 192.168.1.1 with an absurd username and password of blank (i.e nothing) and "admin", or something equally insecure. So the first time you configure the router, set a proper username and password.

If the router isn't actually faulty, you can factory reset it with the recessed reset button on the rear somewhere. You can then re-configure it by logging into the web interface.

The setup CD makes a handy coaster. Just about all it's good for, tbh.

---

### Post by ajgreeny on 2015-09-13
Even in the days that I used Windows XP, I never once used the CD that came with my Netgear Router to get it up and running; it was just as quick to use the web-interface.

I expect that the router has a sticker somewhere on it that tells you its IP address, and possibly also the name and password needed, if it has not already been changed previously, so just enter the IP into a web-browser address-bar and go from there.  The router will also probably have a useful **Help?** system that you can access using the same web-interface.

---

### Post by tgalati4 on 2015-09-13
Netgear used to make a Linux-friendly and firmware-replaceable wireless router.  I have one, and it's quite cool.  I don't know if they have any current routers that support open firmware.

But yes, you don't need a CD to set up a router.  Just plug your computer into it directly and open a webpage [http://192.168.1.1](http://192.168.1.1) or [http://192.168.1.254](http://192.168.1.254) or whatever the quick guide says.

---

### Post by cigtoxdoc on 2015-09-14
Thank you all for your replies.  I was only forced into WiFi with the use of smart phones and tablets by others in my household.  I am sure for those of you who are experienced in setting up WiFi, the web-interface is easy to use.  I got the router running with the web-interface, but it crashed on the firmware update.  Apparently the web-interface under Firefox caused the firmware update to end before completion.  Amazon is sending me a replacement.  BTW, the router came with a big sticker across all the connections saying do not remove until you run the CD.  Maybe it would have run under WINE.

If we are going to move Ubuntu more mainstream we need to make it easier for people to use.

John

---

### Post by tgalati4 on 2015-09-15
It's possible that the CD ran some firmware check and performed a firmware download, all of which would be in the background and hidden from the user.  I have never seen a router that couldn't be completely configured through the router's administrative webpage.

---

