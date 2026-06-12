---
title: "Need help setting up Chiefmax Ralink RT73 USB"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2007-02-09
Here is a link to the page I bought the thing from:

[http://3btech.net/chrart80wius.html](http://3btech.net/chrart80wius.html)

And the link that pages give for the drivers:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
...and I have no idea how to install those drivers (or if I even need to in the first place).  And I don't know how to compile source code...

Anyway... I have a fresh install of Ubuntu Edgy, and after inserting the adapter into a USB slot, it shows the wmaster0 and wlan0 (I think, and I read in another thread that this is "the new standard" and is normal).

For testing purposes (to ensure it's not my wireless router causing connection problems), I reset the factory defaults, and have no encryption enabled at this time.  I can't tell if the wireless adapter is working correctly or not.  I've entered the correct SSID, and no password (in this case) is necessary.  But when I run Firefox, I can't get to google.  I've tried "direct connect", "Auto detect proxy" and manual static IP address.

The system is a duel-boot, and I'm using the adapter right now under XP to get on the internet.  So if I need to download something, I can do it on the XP side, and then boot into Ubuntu next to install the drivers if need be.  So what I really need help with is learning just how to do that.

Thanks in advanced!

---

### Post by diablo75 on 2007-02-09
Can anyone help me with this?  I looked at some other threads, and followed the instructions at this link:

[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)

While my device isn't made by Belkin, the instructions looks fairly generic.  But I ran into snags when trying to test the driver using modprobe (after running Make and Make Install as root using sudo).

Perhaps you could suggest a wireless adapter of some sort that will work for me right out of the box.  This terminal stuff is a pain.

---

### Post by anidritesolforosa on 2008-02-17
I have a Belkin usb wireless dongle with chipset RT73. The only way I found to make it working was using ndisgtk (graphical interface for ndiswrapper)  As far as I can see the driver for RT73 it is not opensource that is why I had to go for the less attractive option i.e. installing the Windo drivers from the CD that comes with your usb device. However after upgrading to 7.10 I have to insert the dongle after booting (which is a pain) but it still works.

---

### Post by anidritesolforosa on 2008-02-17
Apparently now there is a driver for RT73 I have not tried that yet but with ndisgtk it works fine, I could set up the wep key and everything hope you will fix it

---

### Post by anidritesolforosa on 2008-02-17
I am  following  this link: [URL="http://ubuntuforums.org/showthread.php?t=400236"] just copy an paste in a terminal window

---

