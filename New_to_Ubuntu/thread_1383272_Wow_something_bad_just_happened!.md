---
title: "Wow something bad just happened!"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by BlueBomber on 2010-01-17
Been using Kubuntu for a month or so now because my Windows drive died and I wanted to try something new (and free).

Anyway, I was just trying to Cut and Paste some files onto a flash drive, but I accidentally picked a folder that had a huge file in it that wouldn't fit on the drive. So of course it said it was out of room. Problem is, it seems like all the files that didn't make it onto the flash drive are no longer in the computer. I was browsing the internet as this was going on so my clipboard history got full as well. I've tried searching with the Dolphin file manager but the built in search keeps dying unexpectedly. What could have happened to my files??

---

### Post by ankspo71 on 2010-01-17
Hi,
I'm not sure what happened to your files, but if you happen to know some of the file names to your files you can search for files using the locate command in the terminal.

First you need to update the database:
**sudo updatedb**

Next you could use the command:
**locate filename***
The * is a wildcard and is optional. So you can search with ' locate *.bmp ' if you like (without the quotes).
If you find one of your files, I'm sure the rest would be in the same parent location.

Hope this helps.

---

### Post by J V on 2010-01-17
if you didn't reboot you should have been able to paste back in place... oops?

---

### Post by SuperSonic4 on 2010-01-17
If you cut them you may find them in the trash folder. Either use dolphin's wastebin or paste the results of ```
ls -Ash ~/.local/share/Trash/files/ | head -n1
```

---

