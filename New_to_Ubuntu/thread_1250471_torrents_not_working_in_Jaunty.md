---
title: "torrents not working in Jaunty"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-08-26
I was running deluge with 8.10 and it worked fine, but since I switched to Jaunty it stopped working at all. I looked it up and found some bug reports that seemed a bit over my head, so I switched back to transmission. Nothing seems to be working. Today I picked a distro that had 16 seeders showing just to test and sure enough, no activity at all on my download.  I'm connected to the net via a wired connection through a router. Before I didn't need to do anything to it, it just worked. 

I'd love some suggestions on how I might get this going.

thanks
myst

---

### Post by cariboo on 2009-08-26
I believe in both programs in preferences, there is a test network option, try that and post back the reults.

---

### Post by embiggened.badger on 2009-08-26
This is probably stating the obvious, as you've worked with Linux before, but you may need to find a direct way to specify to the OS which ports you want to remain open. [This article]("https://help.ubuntu.com/community/WorldofWarcraft") on configuring 'WoW' to run in Ubuntu + Wine recommends installing Firestarter and opening ports 6881-6999 as they are recognized by Ubuntu for being BitTorrent ports.

---

### Post by lovinglinux on 2009-08-26
> **embiggened.badger said:**
> This is probably stating the obvious, as you've worked with Linux before, but you may need to find a direct way to specify to the OS which ports you want to remain open. [This article]("https://help.ubuntu.com/community/WorldofWarcraft") on configuring 'WoW' to run in Ubuntu + Wine recommends installing Firestarter and opening ports 6881-6999 as they are recognized by Ubuntu for being BitTorrent ports.

There is no need to use ports 6881-6999. In fact it is advised to not use this range, because some ISP's cap the speed on those ports. I recommend ports from 49152 to 65535.

As long as you open the port selected on the router to accept incoming connections and configure the torrent client to use the same port, then it should work. Ubuntu does not recognize a port for being a torrent port. There is no such thing. Besides, Firestarter is not recommended anymore and probably not needed if you have a router with firewall capabilities.

You might also need to check if you have a firewall rule blocking the port.

BTW, did you get that distro torrent from an official site or from any torrent site out there? Check the trackers included in the torrent, because if it is tracked by the Pirate Bay tracker, then the problem is probably the fact that it is offline due to a court order.

---

