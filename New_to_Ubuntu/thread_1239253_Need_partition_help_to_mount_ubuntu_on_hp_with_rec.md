---
title: "Need partition help to mount ubuntu on hp with recovery partition first"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by texla on 2009-08-13
Ok, to catch up, I went from a corrupt xp to a recovered xp after installing ubuntu and finding the double boot option actually pointed to the HP recovery partition when I clicked on xp boot.  Now I have a recovered xp but no ubuntu and the partitions are all set up strange because xp did not reset them during recovery.  I would like to get a nice clean double boot of ubuntu and xp going but I'm worried that the double boot will always point to the recoovery disk instead of xp since it is the first partition on the drive.  In fact when I try to install, there is no side by side option like in the manuals so I don't know if that means anything as well.  Here is the current partition layout as shown by GParted:

dev/sda1 - fat32 - hp recovery - 8.01 gb
unallocated 0 2.77mb
dev/sda2 - ext3  - 9.31 gb
dev-sda3 - linux'swap - 1.86 gb
unallocated - 3.69 mb
dev/sda4 - ntfs - hp pavillion - 167 gb
unallocated - 7.84 MB

and my previous thread on the corrupt xp/ubuntu installl is here:
[http://ubuntuforums.org/showthread.php?p=7777886#post7777886](http://ubuntuforums.org/showthread.php?p=7777886#post7777886)

anyone have any ideas? btw, I'm not worried about losing any data or programs so if that's what has to haappen to clean this up, ir's fine.  I just want to keep the xp os on here for now.

---

### Post by lkraemer on 2009-08-13
Well, once again, if I were doing it I would purchase another 250G SATA
Drive, use Clonezilla to copy the entire drive, and then install the new
250G drive, save the original, and start the process if making a Dual
Boot system.

Typically XP is always the first Partition, and the RECOVERY Partition is
immediately after the OS.  Why yours appears different is confusing.
Maybe a check of Manage Disks will give you more information as to the
naming convention, and order, etc.

Since XP is booting properly, I'd remove the SWAP partition after
disabling it and remove the Ubuntu partition also.  I'd then gather up
all the un-allocated areas, and resize XP to make room for Ubuntu.
After the resize be sure to boot XP so it can is notified of the changes.
I'd give Ubuntu 60-80Gig and then make a Swap that was 2 times the size
of your RAM.  Then Format the two new partitions as EXT3 and SWAP.
Insert the LiveCD and Install Ubuntu on the ~60 Gig Partition being sure
to let Grub write to the XP MBR. (Supergrub can rewrite it back to normal
for XP).

Then I'd load what ever I wanted in Ubuntu.  ENJOY!

LK

---

### Post by texla on 2009-08-13
> **lkraemer said:**
> 
Typically XP is always the first Partition, and the RECOVERY Partition is
immediately after the OS.  Why yours appears different is confusing.
Maybe a check of Manage Disks will give you more information as to the
naming convention, and order, etc.

Since XP is booting properly, I'd remove the SWAP partition after
disabling it and remove the Ubuntu partition also.  I'd then gather up
all the un-allocated areas, and resize XP to make room for Ubuntu.
After the resize be sure to boot XP so it can is notified of the changes.
I'd give Ubuntu 60-80Gig and then make a Swap that was 2 times the size
of your RAM.  Then Format the two new partitions as EXT3 and SWAP.
Insert the LiveCD and Install Ubuntu on the ~60 Gig Partition being sure
to let Grub write to the XP MBR. (Supergrub can rewrite it back to normal
for XP).

Then I'd load what ever I wanted in Ubuntu.  ENJOY!

LK

Thanks again!  That did it - now it's all good.  XP needed to be restored again of course after I used GParted to get all the partitions back to normal.  However the new xp install worked a lot better with the Ubuntu installer than the one that was corrupted.  This time I had the side by side option and used it along with the handy lttle slider to choose 80GB for ubuntu.  There was no option to pick the swap size but I figure it knows what its doing.  And it looks like it does.  I let everything run automatically from the installer disk and now on startup I have the ubuntu as default but also two different windows options:  windows/nt/200/xp (which I now know is my factory restore) and windows media center - which is my clean install of xp.   Just what I hoped to do.  Thanks again for everyone's help here.  Now I'm off to ubuntuland and seeing what I can see - already it moves around 2-3x faster than the xp does and no bloatware to remove is a plus! - seeya' later:popcorn:

---

### Post by lkraemer on 2009-08-13
Now you just need to load some of the following:
1. K3B - DVD/CD Burner
2. ISO Master - Work on or Edit ISO's
3. PDFedit - PDF Editor
4. VLC - Media Player
5. Keepassx - Password Keeper
6. HTMLDOC - HTML to DOC file
7. Filezilla - FTP Xfers
8. Crossover - Runs Quicken - Must Purchase
9. Amarok - Muisc/MP3 Player
10. VirtualBox - PUEL Version - Allows running Windows after install
11. Meld - Diff Viewer
12. Gnome-PPP - Dialup support
13. PSI or Pidgin - IM support
14. WINE - Allows running some Windows Software

That will keep you busy for a night or two.

Never Look Back, Because you WON'T be going BACK!

LK

---

