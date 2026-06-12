---
title: "Remnants of deleted files"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Kirk M on 2009-05-27
I'm fairly new to Linux, Ubuntu being my first permanent Linux OS after I finally tossed Windows out the door, and I have a question about deleted files.

I usually only use the Desktop for temporary storage of files and otherwise keep it clean, deleting temporary text files and such once I'm through using them. I noticed yesterday when viewing the Desktop in Nautilus with "View hidden files" checked that all of these temporary text files were still listed on the Desktop but the names were slightly modified with a "~" instead of the extension. Here's an example:

New file~
Test file~

I'm wondering what these remnants of deleted files are for. Is there an undelete function I'm not aware of or is it something else? I did notice that when I right clicked on one of these remnants that there was a "Delete permanently" entry in the context menu. And just so you know, the real files had been deleted from the "Trash can" quite awhile back.

Just wondering. I'd hate to think I have a bunch of these "remnants" of deleted files cluttering up my OS you know. :)

---

### Post by Celauran on 2009-05-27
Files ending in ~ are typically backup files. I think gedit creates these by default; surely some other apps do too. You can modify the default behaviour if you like, or just periodically clean them out. There ultimately shouldn't be that many.

---

### Post by achase79 on 2009-05-27
These are backup files from when you saved a text document.  It is perfectly safe to delete these files.

---

### Post by philinux on 2009-05-27
> **Kirk M said:**
> I'm fairly new to Linux, Ubuntu being my first permanent Linux OS after I finally tossed Windows out the door, and I have a question about deleted files.

I usually only use the Desktop for temporary storage of files and otherwise keep it clean, deleting temporary text files and such once I'm through using them. I noticed yesterday when viewing the Desktop in Nautilus with "View hidden files" checked that all of these temporary text files were still listed on the Desktop but the names were slightly modified with a "~" instead of the extension. Here's an example:

New file~
Test file~

I'm wondering what these remnants of deleted files are for. Is there an undelete function I'm not aware of or is it something else? I did notice that when I right clicked on one of these remnants that there was a "Delete permanently" entry in the context menu. And just so you know, the real files had been deleted from the "Trash can" quite awhile back.

Just wondering. I'd hate to think I have a bunch of these "remnants" of deleted files cluttering up my OS you know. :)

They are backup files. Say you have a document on your desktop and you save it, the system will automatically create a backup of the original. This is the default behaviour for any file including system files.

---

### Post by Celauran on 2009-05-27
> **philinux said:**
> They are backup files. Say you have a document on your desktop and you save it, the system will automatically create a backup of the original. **This is the default behaviour for any file including system files.**

Are you sure that's accurate? I certainly have not experienced this on my machine.

---

### Post by mapes12 on 2009-05-27
I had a similar problem and found this Howto helpful in clearing out my system: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by mcduck on 2009-05-27
> **Celauran said:**
> Are you sure that's accurate? I certainly have not experienced this on my machine.

It's the default behavior for *many text editors*, not any system-wide feature or anything like that.

---

### Post by philinux on 2009-05-27
> **Celauran said:**
> Are you sure that's accurate? I certainly have not experienced this on my machine.

Have a look in /boot/grub press ctrl h and you'll most likely see a backup copy of menu.lst~ that the system made. Same with xorg.conf if someone used say xfix.

---

### Post by Kirk M on 2009-05-27
Thanks for the quick responses everyone. Would have replied sooner but MY DSL slowed down to a crawl (backwoods living does have it's drawbacks).

I realized that I had seen this very thing before when a doc was open in MS Office but it was always deleted when the doc was closed. I didn't realize that Ubuntu (Linux) didn't delete these temp docs automatically as well. I wouldn't have even known they were there if I hadn't check "View hidden files" in Nautilus.

Thanks for cluing me in. I swear my fifty year old brain gets stuck in nuetral more often than it used to.

---

### Post by Celauran on 2009-05-27
> **Kirk M said:**
> Thanks for the quick responses everyone. Would have replied sooner but MY DSL slowed down to a crawl (backwoods living does have it's drawbacks).

I realized that I had seen this very thing before when a doc was open in MS Office but it was always deleted when the doc was closed. I didn't realize that Ubuntu (Linux) didn't delete these temp docs automatically as well. I wouldn't have even known they were there if I hadn't check "View hidden files" in Nautilus.

Thanks for cluing me in. I swear my fifty year old brain gets stuck in nuetral more often than it used to.

They aren't temp files, though. They are backups. The behaviour is deliberately different. Deleting a backup file when the app exits would all but defeat the purpose of creating a backup in the first place. That said, the option can easily be switched off in gedit preferences.

---

### Post by mcduck on 2009-05-27
> **philinux said:**
> Have a look in /boot/grub press ctrl h and you'll most likely see a backup copy of menu.lst~ that the system made. Same with xorg.conf if someone used say xfix.

No, system didn't make, and it still isn't any kind of system functionality. If xfix names it's backups that way, then it does. Some programs simply append .backup to the file name, others add date/time when the backup was made or even some random number sequence.

---

### Post by philinux on 2009-05-27
> **mcduck said:**
> No, system didn't make, and it still isn't any kind of system functionality. If xfix names it's backups that way, then it does. Some programs simply append .backup to the file name, others add date/time when the backup was made or even some random number sequence.

I forgot about the random number thing. It's not something that crops up a lot. Cheers.

---

### Post by Penguin Guy on 2009-05-27
Yeah, backup files. I think it's a mess personally though - if you want backup files then the system should do it; not the programs. The current way of doing things is kind of random...

---

### Post by Kirk M on 2009-05-27
> **Celauran said:**
> They aren't temp files, though. They are backups. The behaviour is deliberately different. Deleting a backup file when the app exits would all but defeat the purpose of creating a backup in the first place. That said, the option can easily be switched off in gedit preferences.

Ah, thanks for pointing out the difference. I did notice however that once the original file is deleted, the 'backup' of that file cannot be recovered via Gedit and opening the backup manually as text (right-click menu) shows an empty text file.

Just an observation.

---

