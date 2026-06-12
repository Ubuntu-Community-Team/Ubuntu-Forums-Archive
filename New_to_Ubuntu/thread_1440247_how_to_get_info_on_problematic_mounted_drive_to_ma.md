---
title: "how to get info on problematic mounted drive to manually mount it later"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by ave2 on 2010-03-27
Iv had a bit of a problem detecting my microsd card in my sansa mp3 player.

If I plug in my mp3 before starting ubuntu then it picks up the internal memory plus the microsd card. If I plug it in after ubuntu has started, then it only detects the internal storage. 

firstly- why would it do this?

Now that its mounted is it possible to get the info for the microSD so that I can manually mount it later- you know- tell Ubuntu where to look

---

### Post by vanadium on 2010-03-27
You can see any partitions that your system "sees" from the command
```

sudo fdisk -l

```
You also get an overvieuw of available partitions, including their UUID (the identifiers) with
```

sudo blkid

```
You can see what is currently mounted where with
```

mount

```

---

