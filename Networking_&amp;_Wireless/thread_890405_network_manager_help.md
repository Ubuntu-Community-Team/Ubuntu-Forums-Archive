---
title: "network manager help"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by azlinuxnb on 2008-08-15
Hello, I lost my network manager.  Now I can't connect wired or wireless.  Was connected wireless before.  I was playing around to get my laptop to connect automatically.  Please Help.  I am a newB.  Thank You. INFO duelboot xp/hardy

---

### Post by Iowan on 2008-08-15
> **azlinuxnb said:**
> Hello, I lost my network manager. Congratulations, your system might work better...
Seriously now, use an editor to open /etc/network/interfaces and add an "auto" line to the interface(s) you want started automatically. Details [here.]("http://ubuntuforums.org/showthread.php?t=890531")

---

### Post by cdtech on 2008-08-15
I switched to "wicd" and mine works great now.

If you want to try "wicd" just add:
```
deb http://apt.wicd.net **hardy** extras
```
to your "/etc/apt/sources.list" file (change **hardy** to whatever version your running) and:
```
sudo apt-get update
sudo apt-get install wicd
```

Hope this helps.......

---

