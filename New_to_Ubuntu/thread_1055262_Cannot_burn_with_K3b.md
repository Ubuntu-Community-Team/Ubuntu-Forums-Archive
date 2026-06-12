---
title: "Cannot burn with K3b"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Bruv on 2009-01-30
My first use of K3b to copy an iso image.
I have looked around by Googling 'How to' but I think I am doing everything right.
I have the image on the desktop, I have tried two ways.
Open K3b and click on Burn CD image, then navigate to iso file and magically it shows it to be looking for the md5sum which is good.
Then I tick verify written data,alter dropdown to read Image type ISO9660, but the Start button remains greyed out.
Alternatively, I have left K3b closed, clicked on iso file on desktop and magically K3b opens and runs through the md5sum check automatically, the start button remains greyed out.

Is it me or is it a fault ?
The Burn Medium asks for me to insert an empty Medium, although there is a blank already loaded.And it has already recognised the blank disc earlier

---

### Post by arochester on 2009-01-30
Try the command: sudo k3b

---

### Post by Bruv on 2009-01-30
> **arochester said:**
> Try the command: sudo k3b

Started with a warning....but same problem, the start is greyed out

---

### Post by Bruv on 2009-01-30
If I load the CD and click on it, it opens in Dolphin, with the following text below the window.
'Could not start process Unable to create io-slave:
Klauncher said: Unknown protocol".

---

### Post by Bruv on 2009-01-30
Although on the desktop the disk shows as empty, when in K3b it shows the folowing.
"Capacity:     79:57:70 min 702.8 MB
Used Capacity: 96:15:17 846 MB
Remaining:     00:00:00    0MB

So what does that all mean ?

---

