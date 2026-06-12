---
title: "What to do with 1TB NTFS drive?"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by darkmaxa on 2010-07-17
I suppose that similar question has already been discussed, but I can't find right key words for the search.

My storage configuration:

[LIST]
[*] Intel SSD drive with Lucid Lynx on it (previously was Win7 on it)
[*] 1TB storage drive, NTFS formatted, with my docs, workspace, movies, music, etc (60% full)
[/LIST]
 
I'm planning to use Ubuntu as a only OS on this computer, so I'm wondering what is the best solution to integrate 1TB storage disk to Linux file system?

Unfortunately, I currently don't have another hard disk to move the data and then format storage disk in ext4.

Is it safe to leave storage drive as NTFS disk? If is safe, how can I mount it to be permanently visible to all applications (and not visible on the desktop as an icon)?

---

### Post by Elfy on 2010-07-17
This one is the same thing - [http://ubuntuforums.org/showthread.php?t=1532824](http://ubuntuforums.org/showthread.php?t=1532824)

At least the way to deal with the issue is - to make sure that the drive does not show on the desktop you need to mount the drive in /mnt/somename or you could change the gconf value so that nothing shows on the desktop - that would also include cd's usb's etc.

---

### Post by darkmaxa on 2010-07-17
Ok, thx!

Is it safe (for data) to leave disk in NTFS for long-term usage (read/write)?

---

### Post by S.R on 2010-07-17
Would you have a need to use gpart and shrink the NTFS partition size while leaving the remainder as EXT 3 or 4. Do your business with ubuntu while still being able to grab files from the NTFS side of the house ... which windows would still have access too. I mean unless you can do without.

---

### Post by Elfy on 2010-07-17
Well I did that at the beginning until I was in a position to move data to a partition formatted to ext3.

Edit - As SR says - you could, assuming you have the space, do that - but I would always make sure I had backups prior to any partition editing - which given that you've not got space at the moment might make the option less appealing

---

### Post by darkmaxa on 2010-07-17
I have two additional questions...

I've made directory Storage in mnt (mnt/Storage), and then I've made link in my Home directory to mnt/Storage. After that, I've added the following line in fstab:
```
LABEL=Storage /mnt/Storage ntfs-3g defaults,locale=en_US.utf8 0 0
```

After restart, everything works well, I now can access my storage disk through my home folder. :p

- Is it right decision to point all the apps to ~/Storage rather then /mnt/Storage? (for example music player to ~/Storage/Music)

- If I try do delete any file in Storage, file can **not** be moved to the Trash ("*Cannot move file to trash, do yo want to delete immediately*?"). So question is, why Trash function doesn't work on Storage drive?

---

