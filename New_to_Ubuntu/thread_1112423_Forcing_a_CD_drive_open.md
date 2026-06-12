---
title: "Forcing a CD drive open"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by daft crunk on 2009-03-31
I've tried the "eject" command but I get this error message:

umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed


My drive is sticking shut after I started installing something that requires me to switch discs. It usually opens and closes.

How can I open it?

---

### Post by Fenris_rising on 2009-03-31
Observe the front of the disk player. Look for a small hole in the panel below the tray front. Straighten a paper clip that will fit in the hole. Insert straight in until you feel some resistance press firmly and as the clip goes in the drawer will open so far or it may open completely once you get it moving. If not you can pull open the drawer carefully by hand remember to remove the clip.

regards

Fenris

---

### Post by kanikilu on 2009-03-31
I'm not sure if this will help in your case since you say this happens during a multidisc install, however, you could try:```
lsof | grep cdrom
``` This should give you a list of any processes that might be using the cdrom. From there you could try to kill it with the process ID.

---

### Post by daft crunk on 2009-03-31
I can't find a paperclip anywhere, so I'm trying the Terminal approach.

I get this message ("forrest" is me):

wineserve 6060    forrest   52r      REG       11,0 548439098     2416 /media/cdrom0/data2.cab

What do I do from here?

---

### Post by kanikilu on 2009-03-31
> **daft crunk said:**
> I can't find a paperclip anywhere, so I'm trying the Terminal approach.

I get this message ("forrest" is me):

wineserve 6060    forrest   52r      REG       11,0 548439098     2416 /media/cdrom0/data2.cab

What do I do from here? If I remember correctly, the second number is the PID, so try ```
kill -9 6060; eject
```

---

### Post by daft crunk on 2009-03-31
Thanks, it ejected with only the slightest bit of reluctance.

---

### Post by sgosnell on 2009-03-31
Aftermarket drives come with a device for opening stuck drives - a piece of wire with a handle folded onto one end.  Just stick the wire into the small hole and push, and the drive will open, even if it has no power.  Paperclips are very useful tools for all sorts of jobs, and it's always prudent to keep a few on hand, just in case.

---

