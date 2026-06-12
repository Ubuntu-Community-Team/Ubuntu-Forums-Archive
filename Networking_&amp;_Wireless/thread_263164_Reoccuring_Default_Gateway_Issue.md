---
title: "Reoccuring Default Gateway Issue"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by Regord on 2006-09-22
The default gateway that I want is eth0.  However when I reboot, this is unselected and the selected default gateway is null, meaning nothing is selected.  I go to System | Administration | Networking and select eth0 from that first screen and everything works fine.  However, on the next reboot, I'll have to go through the same process again.

From a console, when I type ifconfig, I see 3 devices listed, eth0, lo, usb1.  I don't have anything connected to my usb port and I'm not sure why it's being listed.

So....any suggestions on how to make eth0 my default gateway AND make it stick through a reboot??

---

### Post by Regord on 2006-09-23
ugh...no responses??  Help me UbNetworking...you're my only hope. :)

---

### Post by christhemonkey on 2006-09-23
If you make your changes, but before you quit the networking setup dialog box;
Make sure you make a new location with the drop down box at the top.
This will store your settings for the rest of time!
(or for a while anyway)

---

