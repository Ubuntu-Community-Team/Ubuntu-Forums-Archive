---
title: "how to backup files"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by dwhite on 2011-04-04
i would like to backup my files on a regular basis but don't know the best way to do that here are some things i am considering.


[LIST]
[*]using deja dup to backup to a sd card (i don't have huge files and i don't really want to back up applications so 4 gigs should be more than enough
[*]using ubuntu1 to backup but i can't really tell if this is possible, if i sync several of the folders in my home folder can i use that as backup if i need to?  i won't really be syncing to another computer i just want to be able to retrieve files if my computer crashes etc.
[/LIST]
are either of these reasonable, ubuntu1 seems it would be really convenient but not really sure if i can use to backup as i said (tried to fathom that out by reading faq on the ubuntu1 site but couldn't really tell.

thanks for any advice :)

---

### Post by Learning Linux 2011 on 2011-04-04
Do you want an automated system you mean?

If not, you can also just 'zip' your entire home directory (or wherever you store your files) and transfer the zip file to an external device.  Your '/Home' directory is usually where all of your files are stored, like pictures, music, movies, documents, etc.

USB drives are good for small amounts of files, an external hard drive is better for large files.
Use FAT32 if you want to use them with Windows.

I've never tried it, but unlike Windows, I have heard you can actually zip your entire Linux system into one zip file.

You could also just store everything on an external drive from day one.  Never use your /Home directory on your hard drive, just plug a backup device into your computer and save everything to that drive from the beginning, then you wouldn't have to think about it.

---

### Post by ikt on 2011-04-04
> **dwhite said:**
> if i sync several of the folders in my home folder can i use that as backup if i need to?  i won't really be syncing to another computer i just want to be able to retrieve files if my computer crashes etc.
[/LIST]

yep but tbh I wouldn't rely on it, I would use ubuntu one + a hard backup to maybe a USB pen drive, that way if one goes down you've got the other to be 100% sure.

---

### Post by ndstate on 2011-04-04
Hello,

Either of those could work.  I would also recommend that maybe you take a look at the application Back In Time, its in the software center.  Its works really well in my experience.

You might also want to consider [Dropbox]("http://db.tt/BIOEVNZ"), [Spideroak]("https://spideroak.com/download/promo/cd1") (code is cd1), or some other online backup program.  Many offer free space.  Note that those are linked with my referral code, some of them will give you more free space if you use that specific link so I thought I would offer them up.

If you have any other questions feel free to ask! :)

---

### Post by dwhite on 2011-04-04
i'll check out your suggestions** pmp6nl **thanks

seems like using a usb drive is the easiest and most sure.  i don't see how saving to an external disk exclusively would help as was suggested, as what would happen if that drive failed (or am i missing something obvious here)  

if i decide on a usb drive is there some way to automate this? :-k

anyway thanks for the suggestions, certainly have something to think about, in any case i'll mark this thread solved as i have enough to go on.  

Thanks again

---

### Post by ndstate on 2011-04-04
Saving to a USB drive or external drive is basically the same, you are just replicating the data (but some say external drives are more reliable).  Since you dont have too much to backup I would recommend you also consider the online option... you can probably fit it all on a free one.

The Back In Time program can be set to backup your data automatically to any drive.  The online backup programs typically backup immediately if you wish.

---

### Post by Learning Linux 2011 on 2011-04-04
Ahh, I didn't mean to confuse you.  

As to the backing up to an external device exclusively, for redundancy I guess I meant you would make a duplicate of that external device every once and awhile or simply do a sort of "reverse backup" where you would copy the contents of the external device to the internal hard drive every once and awhile for redundancy.

In my experience, an internal hard drive is more likely to crash before an external one.  
I have USB devices from many many years ago that still function.

My personal backup strategy is to have an external hard drive and a separate internal drive devoted to data files.

Then I have my main hard drive that has my operating systems on it, but if that got hosed, it wouldn't matter all that much since I have my data separate on the internal drive and external drive. (so I have 3 drives total: 2 internal, 1 external)

I think this is the ideal situation.

---

### Post by dwhite on 2011-04-04
thanks Learning Linux, i think I'll go with something similar to your setup, thanks again

---

### Post by ndstate on 2011-04-04
> **Learning Linux 2011 said:**
> Ahh, I didn't mean to confuse you.  

As to the backing up to an external device exclusively, for redundancy I guess I meant you would make a duplicate of that external device every once and awhile or simply do a sort of "reverse backup" where you would copy the contents of the external device to the internal hard drive every once and awhile for redundancy.

In my experience, an internal hard drive is more likely to crash before an external one.  
I have USB devices from many many years ago that still function.

My personal backup strategy is to have an external hard drive and a separate internal drive devoted to data files.

Then I have my main hard drive that has my operating systems on it, but if that got hosed, it wouldn't matter all that much since I have my data separate on the internal drive and external drive. (so I have 3 drives total: 2 internal, 1 external)

I think this is the ideal situation.

Thats a pretty good method.  But also consider keeping a backup off-site in case of fire/tornado/flood etc.

---

### Post by Learning Linux 2011 on 2011-04-06
If you are interested...

Here is a backup script:
[https://help.ubuntu.com/10.10/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/10.10/serverguide/C/backup-shellscripts.html)

And this is for scheduling regular backups:
[https://help.ubuntu.com/10.10/serverguide/C/backups-shellscripts-rotation.html](https://help.ubuntu.com/10.10/serverguide/C/backups-shellscripts-rotation.html)

---

