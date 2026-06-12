---
title: "how to wipeout an external hard drive"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by mal_conductor on 2011-06-24
Does any one know of any application to wipeout an external hard drive?

---

### Post by crispy_420 on 2011-06-24
To what level? Data just gone or gone forever?

---

### Post by dFlyer on 2011-06-24
The simple way is to just use disk utilities and reformat the drive.

---

### Post by mal_conductor on 2011-06-24
> **crispy_420 said:**
> To what level? Data just gone or gone forever?
I want to delete all the data format it and start fresh

---

### Post by dFlyer on 2011-06-24
If it's usb, mount it using disk utilities under System settings, Hardware, Disk utility. Before you can format the drive you will have to unmount it and then select format, select the file system you want and that should do it. I rotate several external drive for backup and that is how I wipe an one backup for future use.

---

### Post by e79 on 2011-06-24
System --> Administration --> Disk Utility --> Format drive

That would be for a plain format but data would still be recoverable with some tools.
To really destroy the data before reformating, i'd suggest something like DBAN (Darick Boot and Nuke) to rewrite the whole drive using zeros or specific algorithym to write random data.

But I think in your case a simple reformat would do the job, unless you want to go for a little clean of your drive and wipe it with DBAN using the 'zero' pass (writing zeros all over your hard drive)

Hope this helps

---

### Post by crispy_420 on 2011-06-24
Since this is not the case of selling the drive and you just want the data gone I would do as others have suggested, just reformat it. It won't take long so you'll be back to using it quickly. A full wipe as mentioned to make your data completely unrecoverable (for security reason) can take hours even on a small disk or maybe a day on larger.

---

