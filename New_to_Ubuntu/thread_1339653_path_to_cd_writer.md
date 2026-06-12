---
title: "path to cd writer"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Claude Lavigne on 2009-11-27
Hi all,

I searched, did not find anything. so:

I am about to backup using Dargui. Using 650 MB slices for the CDWriter here.

How can i tell it (Dargui) to write to the cd? In the requester (dialog, file chooser, whatdoyoucallit) i can't choose the cdwriter, even if it seems to be mounted (an icon for its blank disk is on the desktop).

Or, i guess my question could be: how could i write to that cd frome the terminal? What "path" would i use?

See, i come from the Amiga world, with df0:, hd0:, cd0: all so simple. What do i call the cdwriter here?

Sorry for the bad english, bear with me and help if you can, thanx

Claude

---

### Post by sandyd on 2009-11-27
> **Claude Lavigne said:**
> Hi all,

I searched, did not find anything. so:

I am about to backup using Dargui. Using 650 MB slices for the CDWriter here.

How can i tell it (Dargui) to write to the cd? In the requester (dialog, file chooser, whatdoyoucallit) i can't choose the cdwriter, even if it seems to be mounted (an icon for its blank disk is on the desktop).

Or, i guess my question could be: how could i write to that cd frome the terminal? What "path" would i use?

See, i come from the Amiga world, with df0:, hd0:, cd0: all so simple. What do i call the cdwriter here?

Sorry for the bad english, bear with me and help if you can, thanx

Claude
its in /media/cdrom0 (or cdrom1, cdrom2...)
not sure if linux supports direct burning though

---

### Post by Claude Lavigne on 2009-11-27
Thanx Carlee,

but i already tried putting that ( media/cdrom0) in the field where it puts arhives. It won't go to the cd, just in that folder.

What do i put in that Dargui's "save archive in" field to make it go to the cd?

Or do i have to let it put the slices on hardisk somewhere and burn them afterward?

Claude

---

### Post by phidia on 2009-11-27
The Dargui tutorial [here]("http://dar.linux.free.fr/doc/Tutorial.html") gives an explanation of the mount points to use for writng the backup file. You will need to create a mount point for your cdrom in /mnt and write to that.

---

### Post by Claude Lavigne on 2009-11-28
> **phidia said:**
> The Dargui tutorial [here]("http://dar.linux.free.fr/doc/Tutorial.html") gives an explanation of the mount points to use for writng the backup file. You will need to create a mount point for your cdrom in /mnt and write to that.

yep, saw that too, thanx.

I will experiment with mount point, manana.

Sweet dreams (well, me, i do sleep) and thanx

Claude

---

### Post by Claude Lavigne on 2009-11-28
> **phidia said:**
> The Dargui tutorial [here]("http://dar.linux.free.fr/doc/Tutorial.html") gives an explanation of the mount points to use for writng the backup file. You will need to create a mount point for your cdrom in /mnt and write to that.

ok, i give in.

/mnt being empty, how do i create an entry for cdrom in there?

Claude

---

### Post by jolx on 2009-11-28
> **Claude Lavigne said:**
> Hi all,

I searched, did not find anything. so:

I am about to backup using Dargui. Using 650 MB slices for the CDWriter here.

How can i tell it (Dargui) to write to the cd? In the requester (dialog, file chooser, whatdoyoucallit) i can't choose the cdwriter, even if it seems to be mounted (an icon for its blank disk is on the desktop).

Or, i guess my question could be: how could i write to that cd frome the terminal? What "path" would i use?

See, i come from the Amiga world, with df0:, hd0:, cd0: all so simple. What do i call the cdwriter here?

Sorry for the bad english, bear with me and help if you can, thanx

Claude

A blank disk couldn't be mounted as it wouldn't have a filesystem.

I havn't used Dargui, but maybe try pointing it to /dev/sr0 or /dev/cdrom

EDIT: After looking at the DarGUI documentation, it seems it's able to produce archives which are a suitable size for burning/transfering to cd/dvd/whatever which could be done with another program, for example, with Brasero.

---

### Post by Claude Lavigne on 2009-11-28
> **jolx said:**
> A blank disk couldn't be mounted as it wouldn't have a filesystem.

I havn't used Dargui, but maybe try pointing it to /dev/sr0 or /dev/cdrom

EDIT: After looking at the DarGUI documentation, it seems it's able to produce archives which are a suitable size for burning/transfering to cd/dvd/whatever which could be done with another program, for example, with Brasero.


Well, i have to let go of the idea.

I was aware that cd writing has overhead that prevents a recordable cd drive to be treated like a hard disk (or floppy or Zip), but i thought maybe since i was "copying" a signle file to the disk, that that overhead was somehow not important. But since i can't access the cdwriter from Dargui's interface, i give up.

I will symply let Dargui write its slices on harddisk, and burn them from there. 

**Only one question left:**

On this 1.7 mghz system here, (sempron, ide disks, 750 RAM, 60g free disk space) do i endanger the burning process if i let Dargui write another slice *while* i burn?
Thanx all,

Claude

---

