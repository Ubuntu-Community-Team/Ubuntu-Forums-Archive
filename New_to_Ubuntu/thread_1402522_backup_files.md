---
title: "backup files"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by norbert26 on 2010-02-09
how do i make and save a complete backup ubuntu image onto my external 1 TB HDD. i installed simple backup from extras but it doesnt seem to back up everything and im stuck i can't even exit the program.

---

### Post by warfacegod on 2010-02-09
This is what I do with some modifications:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by gwagchunks on 2010-02-09
Clonezilla is a good tool for making a complete image of your whole drive (sort of like windows ghost)

---

### Post by Dunchillin on 2010-02-09
Hi there. Wow I must be dumb...just read through that other thread but don't understand it really at all!

Any chance someone could post a 'backup for dummies' guide?

Am wanting to backup EVERYTHING to HDD.  Please please thank you?!

---

### Post by warfacegod on 2010-02-09
I suppose if you have the drive space you could just copy one drive to the other.

---

### Post by Dunchillin on 2010-02-09
Thanks for the fast reply!
Okay so if I just copy 'home' folder to another drive?

I want to make sure I keep all my settings etc (have to do a reinstall of Ubuntu as it stuffed up on me after upgrading to 9.10) but am concerned 'home' doesn't contain everything as it appears to itself be inside another directory?

---

### Post by Girya on 2010-02-09
> **Dunchillin said:**
> Thanks for the fast reply!
Okay so if I just copy 'home' folder to another drive?

I want to make sure I keep all my settings etc (have to do a reinstall of Ubuntu as it stuffed up on me after upgrading to 9.10) but am concerned 'home' doesn't contain everything as it appears to itself be inside another directory?

your home folder contains all your data and personal config settings. It doesn't contain system wide configuration files those are in /etc. If you back up your home folder and verify that you backed up everything you should be fine.

you might want to follow the tutorial on psychocats about creating a seperate home partition.

---

### Post by warfacegod on 2010-02-09
> **Dunchillin said:**
> Thanks for the fast reply!
Okay so if I just copy 'home' folder to another drive?

I want to make sure I keep all my settings etc (have to do a reinstall of Ubuntu as it stuffed up on me after upgrading to 9.10) but am concerned 'home' doesn't contain everything as it appears to itself be inside another directory?

Actually, I was thinking that if your "spare" drive is big enough to simply copy the entire drive to it. But Girya is correct, your /home folder really should suffice as a backup.

---

### Post by Girya on 2010-02-09
you could try:

 ```
rsync -avz /home/<username>/ /media/<external_harddrive> 
```

this should create a folder <username> on your external harddrive
you might have to run this as sudo because I believe their are a few folders or files that are owned by root in your home directory.

---

### Post by warfacegod on 2010-02-09
Like this:

```
sudo rsync -avz /home/<username>/ /media/<external_harddrive>
```

---

### Post by Geoff918 on 2010-02-09
> **warfacegod said:**
> Like this:

```
sudo rsync -avz /home/<username>/ /media/<external_harddrive>
```

Yes. Depending on whether you're just doing it to make a total backup or whether you're interested in creating essentially a "restorable" image, you may want to try remastersys?

You might want to search for that. I will probably be doing the same shortly for my business so that I can quickly install just the applications I want for the workers to use.

---

### Post by barkej on 2010-02-09
> **warfacegod said:**
> Like this:

```
sudo rsync -avz /home/<username>/ /media/<external_harddrive>
```

Ah. Excellent, this is just what I needed.

Thanks!

---

### Post by Dunchillin on 2010-02-09
Great, seems to be working well!

On a slight tangent, when I have finished backing up and go to reinstall ubuntu, do I need to wipe my HD first?  Or will the install disc take care of that?  Or is it more of a re-install option (don't wipe anything)?

---

### Post by warfacegod on 2010-02-09
> **Dunchillin said:**
> Great, seems to be working well!

On a slight tangent, when I have finished backing up and go to reinstall ubuntu, do I need to wipe my HD first?  Or will the install disc take care of that?  Or is it more of a re-install option (don't wipe anything)?

The install process will wipe it if you tell it to.

---

### Post by Dunchillin on 2010-02-10
Okay...sigh...it took my from my last post to now for terminal to finish doing its thing after I typed in > sudo rsync -avz /home/<username>/ /media/<external_harddrive>/<folder>...

...and now that it has there don't seem to be any files at all in the folder I backed up to on my external media.

help?...!

I did get this message at the end of the operation
> sent 87001832438 bytes  received 475710 bytes  4542371.27 bytes/sec
total size is 105214408914  speedup is 1.21
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]


But as it had scrolled through my entire files the other error messages have long disappeared from the terminal screen and I can't scroll back to see what "previous errors" were

---

### Post by Dunchillin on 2010-02-10
Okay, and looking at the HDD it has the same amount of free space as before, so what did > sudo rsync -avz /home/<username>/ /media/<external_harddrive>/<folder> do?  Where did they go?!

please help

---

### Post by laurielegit on 2010-02-10
It should have gone into your home directory. Check to see if anything new has appeared there.

Edit: Unless of course, you didn't replace <username>,<external_harddrive>, and <folder>... For example, for me, it would be  
```
sudo rsync -avz /home/laurie/ /media/storage/PersonalMedia
```

---

### Post by Dunchillin on 2010-02-10
I wrote > sudo rsync -avz /home/john/ /media/My Book/HOME BACKUP
My book is what the HDD comes up as and HOME BACKUP is the name of the folder I was hoping i was backing up into!

The files definitely are somewhere on my comp - I can tell by how much space is being taken up on the HD, but I can't find em!

---

### Post by Cheezespread on 2010-02-10
Were those folders tab completed ( as in , did you press tab between the My and Book & HOME and BACKUP ). It should have thrown an error else . But still .

---

### Post by Dunchillin on 2010-02-10
No I didn't press tab between them, just space bar

---

### Post by Dunchillin on 2010-02-10
!#??!@!! computers!

I've found a file in my home folder I'm pretty certain wasn't there before called 'BACKUP' that seems to have everything in it, is the right size etc.  Only thing wrong with it is it says it was created about 6 hours before it was (if it is my backup).

Does this make sense given what command I gave in terminal?

And if it is now what do I do?  I tried to cut and paste into my HDD but some (root owned?) files give me a 'permission denied' when I try, and others, such as '.kde', give me 'Error making symbolic link: Operation not permitted'

---

### Post by musarraf172 on 2010-02-10
sudo rsync -avz /home/john/ /media/My Book/HOME\ BACKUP

Try the above command. If you have a white space in the name of the folder then that has to be indicated by the  slash "\"

Hope this helps.


> **Dunchillin said:**
> I wrote 
My book is what the HDD comes up as and HOME BACKUP is the name of the folder I was hoping i was backing up into!

The files definitely are somewhere on my comp - I can tell by how much space is being taken up on the HD, but I can't find em!

---

### Post by Cheezespread on 2010-02-10
> **Dunchillin said:**
> !#??!@!! computers!

I've found a file in my home folder I'm pretty certain wasn't there before called 'BACKUP' that seems to have everything in it, is the right size etc.  Only thing wrong with it is it says it was created about 6 hours before it was (if it is my backup).

Does this make sense given what command I gave in terminal?

And if it is now what do I do?  I tried to cut and paste into my HDD but some (root owned?) files give me a 'permission denied' when I try, and others, such as '.kde', give me 'Error making symbolic link: Operation not permitted'

**I am assuming the folder HOME FOLDER is already created .**

Thats because of the file name . The whitespaces made that command you executed behave in a different way altogether. 

If incase of filenames or directory names having spaces , use them in quotes or use tab completion.

For eg : 

if there is a directory name like 
'Cheeze folder'

Its easier to use  "command Cheeze<tab>". Press tab and it will fill the name for you , unless there is a file with a similar name.


```
sudo rsync -avz /home/john/ /media/My<tab>/HOME<tab> 
```

If you have a space between **My and Book**, use tab after My . and then type HOME<tab> .

---

### Post by Dunchillin on 2010-02-10
Thanks people, trying again now.

Did get this message right at the start: > sending incremental file list
rsync: readlink_stat("/home/john/.gvfs") failed: Permission denied (13)
but have left it running and keeping my fingers crossed!  Am putting them in a file with no spaces in the name just to make bloody sure!!

Judging by the last time I'll find out if it works in about 5 hours.  Thanks again.

Oh, sorry, final question.  After I reinstall, how do I restore these files?! Probably best to know that before I get rid of everything eh!  Can I simply reverse the code? so > sudo rsync -avz /media/My Book/backup//home/john/ ???

---

