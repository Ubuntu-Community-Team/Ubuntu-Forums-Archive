---
title: "Problems Installing from Live CD"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by ecmatter on 2009-06-29
I'm trying to Dual Boot Windows ME and Ubuntu/Xubuntu on an older HP Pavilion desktop (1 Ghz Pentium III, 256 Mb RAM).

I installed Windows ME first, allowing the OEM restore disks to reformat the hard drive.  That gave me a single 30 Gb FAT 32 Partition with ME.

Then I used the gparted Live CD to shrink the partition to 12 Gb and create a second 18 Gb ext 2 partition.

To that point everything worked fine.

Then I tried to install Ubuntu Hardy to the ext 2 partition from a Live CD (checksum good).  The CD loads to the menu, and I choose "Try out Ubuntu without making any changes to your computer" and wait for the desktop to load.  An hour later I have the desktop wallpaper on screen, but no taskbar and no icons.  

Figuring that I don't have enough RAM for Ubuntu, I try the Xubuntu Live CD.  After an hour or so, I have desktop wallpaper, desktop icons, a semi-functional mouse, and no taskbar.  Same deal if I choose to install from the menu; the desktop partially loads.

Am I right to assume that I don't have enough RAM to run the Live CD?  The minimum system requirement for Xubuntu is 194 Mb (I have 256 Mb).  Is there a way to install without the Live CD?  Is there another distro that requires less from your system than Xubuntu, but has more features than one of the mini-distros like Puppy or DSL?  Any suggestions on a next step would be appreciated.

---

### Post by steeleyuk on 2009-06-29
You might want to try the alternate install disc. Loading up the entire desktop on using a Live CD is very resource heavy on a machine that age, even if you are over the minimum specification.

---

### Post by ecmatter on 2009-06-29
How did I miss that...?  I would have tried the alternate CD the first time had I known such a thing existed.  Thanks.

---

### Post by ecmatter on 2009-06-29
Good News: The alternate install cd worked!

Bad News:  Xubuntu = sloooooow.  I either need more RAM, a faster processor, or more RAM *and* a faster processor.  I can double the RAM for under twenty bucks, so I might try that before deleting Xubuntu and trying Puppy or DSL.

Thanks again for the help.

---

