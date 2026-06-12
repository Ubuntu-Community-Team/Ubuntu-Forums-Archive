---
title: "Diablo II As an ISO"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by nnolund on 2009-11-12
I'm pretty new to ubuntu, so I don't know a lot of the technical stuff.

Anyway, I am trying to install Diablo II from a .iso file, using gmount. It mounts fine, and I can open the file in Wine, but it says there's no disk in the drive (it asks me to put in the install disk, when it has already been mounted and I can view the files from the drive)

I never had a problem doing this on PowerISO on Windows, so is there something I did wrong, or is the gmount?

---

### Post by kostkon on 2009-11-12
You also need to add the mounted folder as a drive in Wine preferences (in the *Drives* tab)

Add a new drive, e.g. *G:* and then set the *Path* to point to your games folder and the *Type* to CD-Rom.

Hope that helps.

---

### Post by nnolund on 2009-11-13
That worked! Thanks a lot.

---

