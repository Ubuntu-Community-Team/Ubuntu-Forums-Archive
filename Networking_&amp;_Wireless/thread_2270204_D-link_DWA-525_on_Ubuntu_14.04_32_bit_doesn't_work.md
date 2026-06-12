---
title: "D-link DWA-525 on Ubuntu 14.04 32 bit doesn't work"
date: 2015-03-21
forum: Networking &amp; Wireless
---

### Post by Richard_Burgdorf on 2015-03-21
Hi,

I'm a serious novice and I can't get the D-link DWA-525 PCI network card working on my 32 bit Ubuntu 14.04. I inserted it then downloaded the driver and at the terminal I went to the driver directory and typed >make. Something happened, but then I typed '>make install' and there was an error. attached is the wireless info file.

Any ideas? I could use a basic step by step instyruction. Should I take the card out and then reinstall the drivers and reinsert?


Thanks [ATTACH]260791[/ATTACH]

---

### Post by jeremy31 on 2015-03-21
It appears that there is already a driver in the kernel for your wifi.  You may want to change your wifi router to a different channel and change the encryption to WPA2 only without WPA or TKIP.  It also appears that the wireless was connected when the script was run

---

### Post by praseodym on 2015-03-21
Which driver is it for the PCI card? I haven't seen this device so far.

What about the stick? Does it work?

---

### Post by Richard_Burgdorf on 2015-03-23
Thanks for the responses. P[COLOR=#000000]raseodym,[/COLOR] the stick worked perfectly with no problems. I was using it to download the drivers as we don't have a wired connection available there. I'll have to get back to you with the driver info, it's on another PC at another site I was working from. Jeremy31, I'll have a look and see if I can change those settings on another PC here and if it makes a difference. I'll try and get it going on the Ubuntu 14.04, but I have a bunch of other PC's with Lubuntu (calling itself Ubuntu 14.10 on the system info summary) that also need the card. Using the usb stick is not an option as they would get 'removed' to easily. Again, thanks for the help.

---

### Post by Richard_Burgdorf on 2015-03-23
Problem solved. Tested a Zyxel G302 V3 PCI card with  a realtek chipset and it work straight away out of the box on Ubuntu and Lubuntu. Sending th eD-link cards back to the supplier and exchanging. I'm sure there is a more elaborate solution, but I don't have the skill.

---

