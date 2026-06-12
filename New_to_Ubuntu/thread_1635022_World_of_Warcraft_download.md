---
title: "World of Warcraft download"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Jackson7 on 2010-12-01
hi guys,

i have recently tried world of warcraft and loved it. i just bought burning crusade to play on our home pc (windows XP :( ) so i go to download it, and uh oh, its almost 30GB of bandwidth usage to download it, so i go onto my laptop and try to download it at the local libraries internet (completely free muahaha). but i have Ubuntu on my laptop and it said that it couldn't download WoW. i have considered just downloading small bits per month onto my home pc (windows, yuck) but that would take forever and i would have to pay monthly for no game time.

is there any way to get WoW onto my laptop?

any reply would be great, thanks guys :D

---

### Post by khelben1979 on 2010-12-01
You need the [Wine software]("http://en.wikipedia.org/wiki/Wine_%28software%29") in your system in order for the system to run the WoW downloader since it's Windows software.
```

apt-get install wine
```

---

### Post by Jackson7 on 2010-12-01
> **khelben1979 said:**
> You need the [Wine software]("http://en.wikipedia.org/wiki/Wine_%28software%29") in your system in order for the system to run the WoW downloader since it's Windows software.
```

apt-get install wine
```

cool so once i get wine it should download without any problems?

---

### Post by eriktheblu on 2010-12-01
There might be problems, but not with the downloader.

Installation *can* be a hassle with Wine; I recommend looking at the [AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549") for advice. If you only purchased Burning Crusade, you're in for a shock because that is simply an expansion of the core game. There will be a 3rd expansion in a few days so your game experience will be slightly limited.

Once downloaded and installed on your laptop, there should be no trouble (other than the time required) to copy over to your home PC and run from there. IIRC, the EULA allows for a backup copy of the game, so you should be OK there.

---

### Post by khelben1979 on 2010-12-01
> **Jackson7 said:**
> cool so once i get wine it should download without any problems?

Yes, if the network is stable enough to complete the download.

---

