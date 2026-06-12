---
title: "Deleted files re-appeared in Windows...?"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Maybach on 2010-09-08
Hi, I am obviously a beginner, but I manage to get by....however, I inserted a USB drive into PC (Windows Vista) and found a trash folder that contained the deleted files from Ubuntu 10.04 LTS! These files aren't visible in Ubuntu, but can be seen in Windows?! How is that possible?

Thanks.

---

### Post by coffeecat on 2010-09-08
I think you'll find that the trash folder is actually named '.trash' or something like that. Certainly with a leading dot which makes it a hidden file in Linux (and in MacOS - you should see what MacOS deposits on USB drives :(). If you press ctrl-H in the file browser window in Ubuntu they'll be visible (or View > Show Hidden).

I *think* what is happening is that the files are not deleted permanently until you empty the trash (deleted items) on your desktop before unmounting the drive. But it sounds as if I'm about to do an experiment. :)

If you delete the whole folder in Windows, a new .trash folder will be made by Ubuntu the next time you do this.

---

### Post by coffeecat on 2010-09-08
> **coffeecat said:**
> But it sounds as if I'm about to do an experiment. :)

Indeed, and I've discovered something interesting.

The hidden folder on my system was .Trash-1000. If I right-click on the USB icon and choose 'Safely Remove Drive' it's simply unmounted and, yes, Windows (7) shows the folder, but curiously it doesn't show all the garbage left behind by MacOS.

But if I choose 'eject', I get the reminder to empty the wastebasket as attached.

Before you unmount, have a look at the trash icon in the bottom panel. It'll show some scrunched up paper. After you've unmounted that disappears because the deleted items are physically on the USB drive, not in your home trash folder.

---

### Post by mastablasta on 2010-09-08
I should add here that even when you delete the files in windows into trash they are still on your disk. i think windows puts them all in one file if i am not mistaking (at least XP).
 
Also even after you remove them from the trash they can still be recovered (quite easilly actually). and even after you format the disk you can still recover them (a bit more hard with this one but doable).

---

### Post by Maybach on 2010-09-08
Thanks for that!
You are right - the folder was .trash (didn't know that hides it in Windows) and the file/folder appeared by Ctrl+H... It also showed the three folders within (just like in Windows) one being expunged, files and info, but they were all empty.
In Windows the "files" folder did have those files, but now they aren't there?
btw, these files were deleted ages a go in Ubuntu....

---

### Post by coffeecat on 2010-09-08
> **Maybach said:**
> btw, these files were deleted ages a go in Ubuntu....

OK, but Windows will leave the .Trash* folder and the folders inside alone. If you delete that lot in Windows, Ubuntu will simply create a new one.

> **Maybach said:**
> It also showed the three folders within (just like in Windows) one being expunged, files and info,

I like that word 'expunged'. I've often wanted to expunge files. A couple of years ago, there was some discussion about what the trash should be called on the desktop. Here in the UK it was 'wastebasket' which everyone in the UK understood. But then it got changed to 'deleted items' for reasons I don't understand. But I prefer 'expunged items'. I'd be more conscientious with my hard drive housekeeping if I thought I was expunging things!

---

### Post by Maybach on 2010-09-08
Thanks coffeecat!

In Australia it is "Garbage Bin", but now I'll have to leave it at that...As you probably know it is 23:10 my way, so I am off to bed..... Thanks again!

---

