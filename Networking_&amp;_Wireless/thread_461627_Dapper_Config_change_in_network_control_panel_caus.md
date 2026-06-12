---
title: "Dapper: Config change in network control panel causes system to hang."
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by jzerocsk on 2007-06-01
Here is my old thread: [http://ubuntuforums.org/showthread.php?t=454436](http://ubuntuforums.org/showthread.php?t=454436)

I'm starting a new thread, as I decided to try using ndiswrapper.  I have gotten pretty far this way - I can get iwconfig and iwlist to do various things.

However, I went to the network control panel (System->Admin->Networking) and attempted to enter the ESSID of my wireless network and the system hung completely and had to be hard-booted.

Now whenever I activate wlan0, the sytem hangs.  If I comment it out of /etc/network/interfaces I can load ndiswrapper and do various operations, but as soon as I uncomment wlan0 and attempt to start the interface, the system once again hangs.  If I attempt to modify it using the network control panel, it also hangs.

Is there a way I can undo the change I made?

Thanks!

---

