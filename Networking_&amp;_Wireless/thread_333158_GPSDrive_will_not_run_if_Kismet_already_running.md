---
title: "GPSDrive will not run if Kismet already running"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by elcasey on 2007-01-07
I was all jazzed up the other day when my Garmin eTrex GPS arrived. I then realized I had to buy a $40 Serial-to-USB adapter to connect it to my laptop, but I wanted to do all the cool stuff I'd read about in tutorials with GPSDrive!

The moment arrived, I finally figured out that the GPS unit needs to be in NMEA mode to communicate with GPSDrive, I fire up gpsd, I start my MySQL server, run Kismet and then GPSDrive.

And the only thing GPSDrive "says" in the Terminal window is:```
Select () call: Bad file descriptor
Select () call: Bad file descriptor
Select () call: Bad file descriptor
Select () call: Bad file descriptor
Select () call: Bad file descriptor
```

GPSDrive never fully starts up, and I can't find a resolution to the problem. Has anyone else suffered the same fate and, if so, how was it rectified?

Thanks! I'm really looking forward to (belatedly) getting my wardrive on, but so far it's been nothing but an ordeal. :mad:

---

### Post by tturrisi on 2007-01-07
may find some answers here:
[http://www.howtoforge.com/wardriving_garmin_kismet_gpsdrive_ubuntu](http://www.howtoforge.com/wardriving_garmin_kismet_gpsdrive_ubuntu)

---

### Post by elcasey on 2007-01-07
I appreciate the link, but that's the howto I used to set the thing up in the beginning. Notice also that it was written for Breezy 5.10, which I suspect may have something to do with it. I have not found anything describing this problem on Edgy so far and it's been quite frustrating.

GPSDrive runs fine on its own, detects my GPS and shows my correct location on its map (I could use a source for new/better maps for GPSDrive as well). Kismet runs perfectly on its own, recognizes that a GPS is attached, and outputs workable log files. 

But they will not run together. From the error message, it seems like GPSDrive is having a problem with the MySQL server, but I don't know jack about databases in general and MySQL in particular. What gives? :???:

---

