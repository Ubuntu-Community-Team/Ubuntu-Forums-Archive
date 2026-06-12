---
title: "Formatting Issues (iPod and External HDD)"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by definedglory on 2010-05-02
I recently had to uninstall Snow Leopard and replace it with Ubuntu, now I was able to pull some files to my external HDD and restore the factory settings on my iPod. Here's where my problems start:

External HDD:

I am allowed to pull files off of the disk, however, I am not able to move files to the disk, I assume because it is Journaled but I could be wrong. Any suggestions?

iPod:

This is the biggest hangup I have had, my computer recognizes that is an iPod but when I try to put anything on it, I get an error message saying that it is a "read-only filesystem." I've tried to format it but I have had no luck, can anyone give me or lead me to a simple guide on how to do this?

---

### Post by SnickerSnack on 2010-05-02
> **definedglory said:**
> External HDD:

I am allowed to pull files off of the disk, however, I am not able to move files to the disk, I assume because it is Journaled but I could be wrong. Any suggestions?

This is because the external drive is using a filesystem that ubuntu cannot write to (at least not without additional software).  Go to the command line and run

```
sudo fdisk -l
```

(that's an ell, not a one, for 'list')  The last column in the output is the filesystem type.  Do a google search for "[fs type] ubuntu linux" (replacing the brackets with the type you have, obviously).  If there is a way to get ubuntu to write to that filesystem, that should help you find it.  (Edit: Any software you might find will work for any flavor of linux and not only ubuntu, so in that regard, 'ubuntu' is not needed as a search term, but instructions and how-tos intended for ubuntu users tend to be easier to use since they're directed at less experienced linux users.)

If that fails, then you can reformat the drive using gParted (which you probably already have installed; menu: System > Administration > GParted).  You'd probably want to backup the files first, of course.




edit: there's a bit of information (and possibly everything you need) on this page: [http://www.linuxquestions.org/questions/linux-software-2/mounting-hfs-volumes-under-linux-521189/](http://www.linuxquestions.org/questions/linux-software-2/mounting-hfs-volumes-under-linux-521189/)

You should probably read the whole thing, as it seems to have useful info scattered throughout.

EDIT: Actually, this looks better: [http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/)

---

### Post by definedglory on 2010-05-02
I was able to fix the iPod issue, I just had to Restore it on another laptop (so it would erase the sync with my library).

EDIT: Disregard that. Shows up in Banshee and I was able to put music in it but once I disconnected it, there was no music on the iPod.

Currently trying SnickerSnack's tips on the External HDD, I will edit this post with my findings.

EDIT: I decided to back up my files and just reformat the HDD, figured it would be the easiest way.

---

