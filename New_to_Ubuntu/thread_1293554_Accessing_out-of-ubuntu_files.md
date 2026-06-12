---
title: "Accessing out-of-ubuntu files"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by BullHorn on 2009-10-17
I've only installed ubuntu last night and am a complete beginner.

I've used Wubi because I couldn't afford the high chance of damage to my partition right now. I'll reinstall it later properly.


The question is, how can I access the files that are not in the ubuntu folder, like my music, ebooks, movies, etc?

---

### Post by philinux on 2009-10-17
Your windows partition should show up under Places top left on Deaktop.

---

### Post by Mike_IronFist on 2009-10-17
> **BullHorn said:**
> I've only installed ubuntu last night and am a complete beginner.

I've used Wubi because I couldn't afford the high chance of damage to my partition right now. I'll reinstall it later properly.


The question is, how can I access the files that are not in the ubuntu folder, like my music, ebooks, movies, etc?

Most of the time, you can go to "Places", then click on your hard drive, put in your password, and access your windows stuff.

For example, you got to "places", click "200 GB volume", and then finally put in your password when prompted, and then your C:\ drive should be accessible with a simple double-click on its icon on your desktop.

I don't know if that applies to wubi installs though.

---

### Post by BullHorn on 2009-10-17
The C: drive is not showing there... If it was that simple, I would've not asked you guys, heh. :)

---

### Post by philinux on 2009-10-17
> **BullHorn said:**
> The C: drive is not showing there... If it was that simple, I would've not asked you guys, heh. :)

It wont show as C: what you got under places.

---

### Post by BullHorn on 2009-10-17
In Places -> Computer it only shows Filesystem and CD-RW/DVD±RW Drive.

---

### Post by philinux on 2009-10-17
From the wubi faq's

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

This.
> Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.

So. Places>filesystem then navigate to the media directory.

You can then create a bookmark so it will appear in places.

---

### Post by BullHorn on 2009-10-17
Aha! That was it, thank you so much!

---

