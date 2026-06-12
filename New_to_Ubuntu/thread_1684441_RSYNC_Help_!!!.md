---
title: "RSYNC Help !!!"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by jcouillard on 2011-02-09
Quick question...How do I make it so when I transfer the files from my home directory to my external drive, the files are literally synced to the condition where my external will have new info added AND be deleted if a certain folder was delted within my home dirctory, but was still on my external before I made the latest sync?  I hope you guys get what I mean...lol I basically want my home directory to "overide" my external drive to truly be updated to what's on my laptop's HDD. Thanks for the support..

I have a feeling the argument may be made with -u and mayeb some other variant but I wanted to double check.

---

### Post by Hawkoon on 2011-02-09
> **jcouillard said:**
> I have a feeling the argument may be made with -u and mayeb some other variant but I wanted to double check.

If you want to check whether your rsync options work for you, do a dry-run first (-n option) and turn on verbosity (-v).

As for your original question, you want to use the --delete option.  The -u option will cause rsync to NOT copy a source file if the target file is newer. 

Btw, in case you don't know that already, hitting "/" whilst browsing through man pages opens a search prompt. I only found out a few days ago! It makes working with man pages so much more efficient.

---

### Post by tea for one on 2011-02-09
> **jcouillard said:**
> Quick question...How do I make it so when I transfer the files from my home directory to my external drive, the files are literally synced to the condition where my external will have new info added AND be deleted if a certain folder was delted within my home dirctory, but was still on my external before I made the latest sync?  I hope you guys get what I mean...lol I basically want my home directory to "overide" my external drive to truly be updated to what's on my laptop's HDD. Thanks for the support..

I have a feeling the argument may be made with -u and mayeb some other variant but I wanted to double check.

Good evening

The syntax for terminal commands often baffles me so I would suggest you consider using Grsync available via the Software centre.

There is a tick box for "Delete on destination"

---

### Post by b0b138 on 2011-02-09
I use ```
rsync -vurt --progress --delete --exclude=.* /home/user /mnt/backup
```

WARNING!!!!!!!!!!!!!!

Be carefull with --delete.  The disk I used for /home started dying, and there were bad sectors and files that rsync couldn't read. So since rsysc couldn't read them, it deleted the backups.  I now run it without --delete first, just so I know it read everything fine

---

### Post by The Cog on 2011-02-09
This is the command I run (as root). I only back up /opt because I don't want to go through all the hassle of installing some games from CD again.
 
```
nice rsync -av --delete --exclude '*\.gvfs' /home /opt /media/BACKUP/StevesPC
```
I ought to try **-x** instead of **--exclude '*\.gvfs'** some time.
Edit: Nah, -x doesn't fix the error when it tries to enter .gvfs.

---

### Post by jcouillard on 2011-02-10
Thanks guys...Please tell me you all needed help understanding the CLI commands just from the help menu at first? lol Did most of you get codes from other as I am now or did u figure this stuff out. I imagine I would have eventually but I am busy at work right now, no time to truly get down and dirty with it. I will probablt give grsync a try once I get internet access from my laptop again...can't wait...I'll try some of this stuff out that you guys provided for me. :p

---

### Post by asmoore82 on 2011-02-10
If your external drive is a DOS derived filesystem,
remember that it cannot store exact timestamps.

You can use the `--modify-window` option of rsync to reduce accuracy calculations.

---

### Post by Andreas1 on 2011-02-10
```
rsync -av --delete source destination
```


for an explanation of the arguments, do ```
man rsync
``` where it will say that "-a" stands for "archive" (which is what you want, an exact copy), and "-v" stands for "verbose" (which just means it tells you what it's doing)

---

### Post by jcouillard on 2011-02-10
Thanks...I ended up getting it due to the help from you guys...appreciate it :o)

---

### Post by jcouillard on 2011-02-10
If I do rsync -avn /SRC /DEST is it the same as doing

rsync -av --dry-run /SRC /DEST

?? Thanks

---

