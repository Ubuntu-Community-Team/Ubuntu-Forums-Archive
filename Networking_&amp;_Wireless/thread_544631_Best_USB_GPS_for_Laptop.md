---
title: "Best USB GPS for Laptop"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by Senathon on 2007-09-06
Can anyone recommend a good GPS and/or GPS software?  I been hearing about GPSdrive but I would like opinions first.

I will be using a Emachine M6811, USB Connection, with Ubuntu Feisty.

I will be using the GPS for traveling to site to site location for delivers.  Nothing fancy, but stable and works.

If I get a good recommendation, then my Windows dependency will be no longer.

Senathon

---

### Post by tgalati4 on 2007-09-06
You want something with the SirFStar III chipset:

[http://www.usglobalsat.com/item.asp?itemid=60&catid=17](http://www.usglobalsat.com/item.asp?itemid=60&catid=17)  ~$80

Marine-grade, surface mount ~$100

I'm using 10 of the marine-grade for a project and the magnetic mount for casual use.  Works indoors, under trees, inside cars.  Good unit.

---

### Post by Shawn Dineley on 2007-09-07
Hello

   I Just bought a gps unit off ebay, and used it with gpsdrive (from synaptic). For our vacation. worked pretty well. Does take some time to download all the maps and setup the waypoints. But other then that. It's great.

Here's the ebay link: [http://cgi.ebay.com/USB-GPS-Receiver-for-Laptop-Notebook-12Ch-NMEA-0183-NEW_W0QQitemZ290156970917QQihZ019QQcategoryZ4668QQtcZphotoQQcmdZViewItem](http://cgi.ebay.com/USB-GPS-Receiver-for-Laptop-Notebook-12Ch-NMEA-0183-NEW_W0QQitemZ290156970917QQihZ019QQcategoryZ4668QQtcZphotoQQcmdZViewItem)

---

### Post by detarmstrong on 2007-09-14
I would recommend against garmin gps 18 USB. 

This is why:

When I plug my garmin gps 18 USB in dmesg says:

usb 3-2: Garmin GPS usb/tty converter now attached to ttyUSB0

Good.
But when I run:

stty -F /dev/ttyUSB0 && cat < /dev/ttyUSB0

expecting to see output I see nothing

Unless someone has a smooth solution to this problem ;) no one must ever touch a Garmin product again.

I'm on feisty fawn.

---

### Post by tgalati4 on 2007-09-15
Garmin has a funky protocol that gpsdrive deals with using added modules in the code.  I stripped them out for my project.  I can't comment on performance of the Garmin units.

It's unfortunate that most of the decent mapping and gps utilities are on windows.  There's not a lot to choose from in Linux.  But what is available works OK, it's just not fancy.  I'm hoping for better tools in the future.  In the meantime, we just have to write our own.

Gpsdrive is undergoing rapid development and there are new features and frameworks every few weeks.  I would download an SVN snapshot and compile it from scratch to see what the new capabilities are.  The repository version of gpsdrive is stable, but also old.

---

### Post by detarmstrong on 2007-09-16
I found [this little tidbit]("http://www.gpsbabel.org/os/Linux_Hotplug.html") today.
Apparently the default 'garmin_gps' driver rarely Works, so the solution is to remove it and install the gpsbabel software. 
Note the nice little caveat at the bottom for edgy+ users.

---

### Post by detarmstrong on 2007-09-20
A lot of info on specific makes and brands can be found in the gpsbabel doc:
 [http://www.gpsbabel.org/htmldoc-1.3.4/readme.html]("http://www.gpsbabel.org/htmldoc-1.3.4/readme.html")

I ended up using [real time tracking]("http://www.gpsbabel.org/htmldoc-1.3.4/tracking.html") with my garmin USB 18. It's cool I guess.

---

