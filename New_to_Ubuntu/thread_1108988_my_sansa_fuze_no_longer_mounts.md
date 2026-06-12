---
title: "my sansa fuze no longer mounts"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-03-28
i was able to mount my sansa fuze 4 gb mp3 player in rhythmbox automatically. this has been fine til this morning when i plugged it in and its charging but will not mount to my computer. i havent tried my windows partition yet but that is next. does anyone have a solution to this issue?

---

### Post by kanikilu on 2009-03-28
Try these in a terminal (Applications > Accessories > Terminal):

1) See if it was mounted: ```
mount
```
2) See if it was recognized, but not necessarily mounted: ```
sudo fdisk -l
```
3) See if a problem was logged. Plug in the drive and then do: ```
dmesg | tail -n 20
```

---

### Post by InfectedWithDrew on 2009-03-28
I have this problem too: [http://ubuntuforums.org/showthread.php?t=1103434](http://ubuntuforums.org/showthread.php?t=1103434)

----------------
Now playing: [Relient K - College Kids](http://www.foxytunes.com/artist/relient+k/track/college+kids)

---

### Post by PatrickMoore on 2009-03-28
i resolved it by changing the usb option to msc and restarting the computer. it came up mounted when i logged on

---

### Post by e.m.fields on 2009-11-22
Hi guys.
Did you ever find a solution to your problem?

I was never able to get my sansa fuze to mount in the first place.

Please someone respond if you've figure this out and I'll add it to a "solved" thread.

---

