---
title: "downloaded 9.10 iso, can't burn cd"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by abooks on 2009-11-13
I've got a bad Kubuntu and have downloaded new Ubuntu, but machine can't find the iso I've downloaded. suggestions?

---

### Post by KayakJim on 2009-11-13
> **abooks said:**
> I've got a bad Kubuntu and have downloaded new Ubuntu, but machine can't find the iso I've downloaded. suggestions?

Select to redownload the file and look at the directory it is being placed in and that is where your last download should be.

Or you could open a terminal and use the find command to look for the new .iso file.

---

### Post by abooks on 2009-11-13
elect to redownload the file and look at the directory it is being placed in and that is where your last download should be.

Or you could open a terminal and use the find command to look for the new .iso file.

Sorry, I don't know how to redownload. I tried find .iso and ubuntu-9.10-desktop-i386.iso and neither worked.

---

### Post by abooks on 2009-11-13
I also tried looking in var>cache>apt and found something similar but much smaller. CD is detected but where to look for download. I kept window open just in case.

---

### Post by redseventyseven on 2009-11-13
Umm... how can you not re-download the file? It just means trying to download the file again, exactly the same as how you did it last time.

However, instead of saving the file, make a note of the folder that comes up when it asks you where you want to save the file. You'll probably find the .iso file there.

Failing that, look in your "Home" folder. On Kubuntu 9.10, click on the folder with the star next to the main menu and have a little look through there.

---

### Post by abooks on 2009-11-13
I think I found it in Home, and I COULD still burn a CD with that. Thanks!

---

### Post by redseventyseven on 2009-11-13
Are you new to this whole Ubuntu/Linux thing?

For future reference, the way the filesystem is set up is very different from Windows. Your "home" folder is where all your personal files sit. Your removable media (such as CD-ROMs, USB sticks, etc.) you'll find in the "media" folder.

All the other folders ("etc", "var", "usr", and so on) are what we might loosely call "system" files. Playing around with them in the wrong way might make things break. They're there so that you can tweak them *if you know what you're doing*. If you don't know what you're doing, then leave them well alone.

---

### Post by garvinrick4 on 2009-11-13
I think you will be better off just downloading everything to desktop. Put them
where you want from there until you get used to where you download to.

---

