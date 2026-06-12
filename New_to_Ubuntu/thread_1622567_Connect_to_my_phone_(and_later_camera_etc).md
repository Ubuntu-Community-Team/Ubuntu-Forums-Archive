---
title: "Connect to my phone (and later camera etc)"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by NeverUsedItBefore on 2010-11-15
Hi,
Plugged my phone in (its a Samsung and not android).
But it seems like Ubuntu doesn't recognize it. E.g. I can't select it anywhere or anything.

But I want to so I can add files to it? How to connect to phone?
Its plugged into a USB cable.

---

### Post by sanderd17 on 2010-11-15
I believe you need samsung PC studio for this. You can try to run it through wine, I've never tried it though. I always used an SD-card.

---

### Post by Hippytaff on 2010-11-15
You can sometimes use it as external storage device if it has an sd card in it, though I had to resort to XP and PC Studio.

what does
```

lsusb

```
return? if it can see your phone try
```

cd /media/

```
```

ls

```
if your phone is listed you should be able to cd to it.
:-)

---

### Post by NeverUsedItBefore on 2010-11-15
Thanks. Did a little tinkering. I found I can change the Settings - PC Connection.
If I select mass storage at least ubuntu can connect to the phone as a separate drive. 

Rhythmbox music player has still not picked it up yet however...

---

### Post by NeverUsedItBefore on 2010-11-15
lsusb can see my phone..

---

