---
title: "disconnecting internet when inactive"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Tryer(ForLife) on 2010-05-07
Hello, well i'm trying to download something with torrents and i started several downloads in Transmission torrent client and i leave my computer to download it over night. I turn off my monitor and go to bed, and for a while it does download, but then it disconnects from the internet and stops downloading.

I figured out that i probably need to switch off Sreensaver and Lock sreen  in System>Preference>Screensaver and also i set "Put computer to  sleep when inactive" and "Put display to inactive" to Never. 

That didn't help at all, it still disconnects for some reason,  is there some other option that disconnects internet after inactivity?

I'm using 10.04 Lucid and i have broadband connection that works in bridge mode.

---

### Post by Tryer(ForLife) on 2010-05-07
well i tried leaving the PC running on it's own without Transmission client downloading and it didn't disconnect me, so i figured that the problem was caused by Transmission and sure enough after some googling i found this
[http://forum.transmissionbt.com/viewtopic.php?f=4&t=9686](http://forum.transmissionbt.com/viewtopic.php?f=4&t=9686)

i will try lowering number of peers and everything else that's suggested in that thread, and see how it goes.
if anyone has the same problem and you find this thread, you know what to do...:D

---

### Post by Mustard on 2010-05-07
I've encountered this one myself.  It's not necessarily Transmissions fault, certainly some blame must be placed on the routers ability to handle a large number of connections.  Some routers do, some don't.

---

### Post by warfacegod on 2010-05-07
I've heard of this happening somewhat often with Transmission. I prefer ktorrent over Transmission any day. If you try ktorrent, be sure to enable DHT.

Mustard is correct though, if you're downloading more than 2 or 3 torrents at the same time, you could easily have overworked your router.

This link may help: [http://ubuntuforums.org/showthread.php?t=1259923]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by diablo75 on 2010-05-07
I used to have a Linksys Wireless-B router that locked up completely after about 5 minutes of any torrent download activity.  You should be able to adjust (downgrade) the number of simultaneous connections and the amount of up/down bandwidth used overall.  As a rule of thumb, it's good to limit your max upload bandwidth to about 60 or 70 percent of the max available as provided by your ISP.  If you go higher than that, it overwhelms the modem and chokes the hell out of your downstream.  I don't know why this is but just check it out sometime and you see a big difference.

---

### Post by Tryer(ForLife) on 2010-05-08
Thank you guys/gals i did everything that was suggested here and in the thread in post #2 and i managed to finish my downloads with only 1 disconnection. I don't download a lot using torrents so i didn't know about this....next time i will also try Ktorrent and i hope it will work even better.

Regards.

---

