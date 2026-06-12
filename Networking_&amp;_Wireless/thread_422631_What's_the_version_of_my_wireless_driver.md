---
title: "What's the version of my wireless driver?"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2007-04-25
Where do I check to find out if its the latest?
In my case I'm using Feisty and a Belkin F5D7000 uk v3.  It's a rt2500 based pci card.

I appear to have the latest  RT2500 driver downloaded onto my Desktop but that might have been when I was setting up Puppy Linux a few months ago ( rt2500-1.1.0-b4 ) . My Ubuntu wireless driver might be older.

---

### Post by spd106 on 2007-04-26
This command should tell you the version of the driver currently being used.
```
sudo lshw -class network
```

Also check dmesg.

---

