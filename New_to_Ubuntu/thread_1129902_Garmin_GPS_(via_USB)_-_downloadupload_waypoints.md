---
title: "Garmin GPS (via USB) - download/upload waypoints"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by martin_1 on 2009-04-19
Hello,

I have Garmin eTrex Legend HCX. I can connect it to my PC via USB. I need to download/upload waypoints, tracklog etc. but don't know how I can do this in Ubuntu (8.10). I tried VikingGPS with no success :(

Does anyone know which program should I use and/or how should I setup my system?

(I could use EasyGPS on Windows in VirtualBox... but I would prefer some native Linux application)

Thanks,
Martin.

---

### Post by _march_ on 2009-04-21
You can use gpsbabel. A little script can be found [here]("http://wiki.openstreetmap.org/wiki/User:Marchk/Ubuntu"). Also read our [Wiki]("http://translate.google.de/translate?prev=hp&hl=de&js=n&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FOpenStreetMap%2FProgramme&sl=de&tl=en&swap=1&swap=1").

---

### Post by s2001t on 2009-05-29
I have been able to get Mapsource to work with WINE.  before I open mapsource I have to put in:
$ sudo modprobe garmin_gps
$ ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

Now, I'm far from a computer programmer, only know some basic HTML at best.  I'm trying to pick up what I can, and without these forums, I would have given up on Ubuntu.  

To the point though, is there anyway of getting around having to type in the above commands each time I restart my computer??  

Thanks!

---

### Post by De Baimbo on 2009-08-04
the thing is: /dev/ttyUSB0 doesn't seem to exist anymore in the newest ubuntu!

---

### Post by gabak on 2010-06-04
here it explain how to do it

[http://jhau.maliwi.de/linux/gpssw.html](http://jhau.maliwi.de/linux/gpssw.html)

---

