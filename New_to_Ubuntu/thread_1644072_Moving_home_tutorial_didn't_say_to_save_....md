---
title: "Moving /home tutorial didn't say to save ..."
date: 2010-12-12
forum: New to Ubuntu
---

### Post by pgibson on 2010-12-12
The [[COLOR="Blue"]Partioning/Home/Moving[/COLOR]]("https://help.ubuntu.com/community/Partitioning/Home/Moving") tutorial doesn't say to save the two changes made to the fstab ... so I guessed and
rather capriciously split the difference and saved the second time only.  :D  

Would someone's more experienced eyes verify, please, whether one should, indeed, save at each or neither step?

I also didn't use a live CD or concern myself over setting up my not-yet-new-/home partition using ext4, though my current install (and /home therein) is ext3.  These are also two places I may have stumbled inadvertantly.  Here's my sudo blkid output:

```

/dev/sda1: UUID="389494239493E224" TYPE="ntfs" 
/dev/sda2: LABEL="los1" UUID="790838b8-15a0-4d15-af90-8caf01d76bed" TYPE="ext3" 
/dev/sda3: UUID="8cccaa24-8dc4-486e-86f7-92235822695b" TYPE="ext4" 
/dev/sda4: UUID="c1a9160f-cc1c-4aa1-9deb-1f997c089293" TYPE="swap"
```

My Ubuntu 9.10 install lives on los1, /dev/sda2, and I want to make /dev/sda3 my new /home. At this moment, /dev/sda3 is empty, nothing was installed on it by rsync, it seems.

This tutorial is so close to being beginner friendly, I'm looking at setting up a launchpad account and putting my English degree to use at last.

Thanks in advance,

---

### Post by diablo75 on 2010-12-12
You're right, it is rather pointless to tell someone to edit their fstab but not save those edits.  Someone should fix that.

I'm reading the documentation you linked and am at the point where you would use rsync to copy the contents of your soon-to-be old home folder into the root of the new partition.  Leading up to this rsync command is the new partition being mounted using the **sudo mount -a** command.  I am wondering if this is a sufficient way to reliably mount this partition.  Normally, when you mount, you use a more specific syntax like:

```
sudo mount /dev/sda1 /media/foldername
```

So in your case, the correct command MIGHT be:

```
sudo mount /dev/sda3 /media/home
```

This should mount the new ext4 partition as /media/home and then allow you to use the rsync command exactly as it is written to copy the contents of your own /home folder into /media/home.

---

### Post by pgibson on 2010-12-12
Yay!  For once ubuntu forums ten second login time worked for me.  I had just written the following ... no kidding! :D

> Actually, looking at the tutorial a bit more closely, after being directed to ```
sudo mkdir /media/home
``` I wonder if it's strictly necessary to use ```
sudo mount -a
``` wouldn't ```
sudo mount /dev/sda3 /media/home
``` be enough for the purposes of this?  It seems I'm mounting all the other partitions too, but I don't see why but that maybe it's less typing?

It's getting late, too late to run this all again tonight. ;) I'll try again with your (and my (yay)) suggestion to use ```
sudo mount /dev/sda3 /media/home
``` tomorrow, saving at each fstab change.

Any thoughts about the ```
sudo mkdir -p /home/user
``` ploy listed in the tutorial?

I'm thinking that the system managed to mount /home as /dev/sda3 (as it was told to in fstab), but that there was nothing there for it to use ... so the system tanked.  The tutorial's "Sneaky Safety Manoeuvre" [sic] of creating a false "/home/user" directory at via ```
cd /
sudo mkdir -p /home/user
``` was perhaps never seen (but I don't understand how that would work either ... wouldn't it be empty?

I've gotta get some sleep tonight ... I hope you'll speculate further.  (I'm thinking it's time to cobble together a junk-box just to bork trying stuff like this out.)  

Thanks for taking time to respond!  

Peace till later!

---

### Post by sandyd on 2010-12-12
> **diablo75 said:**
> You're right, it is rather pointless to tell someone to edit their fstab but not save those edits.  **Someone should fix that.**

I'm reading the documentation you linked and am at the point where you would use rsync to copy the contents of your soon-to-be old home folder into the root of the new partition.  Leading up to this rsync command is the new partition being mounted using the sudo mount -a command.  I am wondering if this is a sufficient way to reliably mount this partition.  Normally, when you mount, you use a more specific syntax like:

```
sudo mount /dev/sda1 /media/foldername
```So in your case, the correct command MIGHT be:

```
sudo mount /dev/sda3 /media/home
```This should mount the new ext4 partition as /media/home and then allow you to use the rsync command exactly as it is written to copy the contents of your own /home folder into /media/home.
done.
and whoever did the guide did a sloppy job of numbering....

---

### Post by diablo75 on 2010-12-12
Crikey, that's a bad tutorial indeed... 

I have a launchpad ID actually, I just barely use it.  So I'm going to attempt to do a face lift on this guide so fewer people get trapped like you have.  I'll post back here when I've met my limit on useful contributions towards it.

---

### Post by oldfred on 2010-12-13
Anytime you edit fstab you need to run

```
sudo mount -a
```

That reloads all the mounts in fstab, so if you have edited fstab with a new mount it will add it. If it has no errors, it just returns to the command line. If it has errors, it will tell you what it could not do.

---

### Post by diablo75 on 2010-12-13
I've edited the guide to make more sense.  [Check it out here]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

---

### Post by pgibson on 2010-12-14
Thanks to one and all!  I've only minutes to look tonight, but only a quick scan and I can feel a much smoother read and cleaner conveyance of what needs to be done and in what order.  Also, I very much appreciate the smooth way in which the how and why of the procedures illuminate without distracting the reader.

Brilliantly done.

I've got so much less time to work on my computer during the week, so I'll post once more when I actually have a chance to use the tutorial beginning to end.  

(and when I say "Thanks to one and all," it must be understood to that I am also including those people who created the tutorial in the first place).;)

Peace,
pgibson

:D

---

### Post by pgibson on 2010-12-19
Groovy ... worked like a charm, sorta ;)

There were a few dissimilar areas that "diff -r" came back with besides .gvfs.  A little reading about .diff (good brief article [[COLOR="Blue"]here[/COLOR]]("http://lowfatlinux.com/linux-compare-files-diff.html")) lead me to believe that most of these differences were minor things, such as some firefox add-ons (noscript chiefly) and firefox's curious inability to load ubuntu forums after I had run rsync and diff.  (Mighty little Dillo to the rescue!)  Other diffs were located in .gconf and had to do with network manager ... which has been giving me problems since changing my wan password at the router, 

Otherwise everything seems to have worked perfectly (including the annoying wireless problem, but that's another thread.)

Peace, and thanks.

---

