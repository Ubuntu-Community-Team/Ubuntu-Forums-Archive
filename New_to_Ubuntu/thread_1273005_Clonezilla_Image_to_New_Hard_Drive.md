---
title: "Clonezilla Image to New Hard Drive"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-09-22
Hi Everyone,

I had an XP system that I made into a dual boot Jaunty/XP system (with both partitions on the same HD). 

I have saved the Jaunty image with Clonezilla and would like to install it on a freshly formatted "blank" HD. 

I thought this would be a rather straight forward process but I can't seem to get the partition to  "load" to the new HD. Am I missing something? Does my new hard drive need have the exact same partition table as the old one? I reformatted the whole thing with G Parted so that it is EXT3 fileformat. 

If anyone knows the steps I would need to take to do this I would be most appreciative. 

Presence already helped me through one mess and now it seems like I found myself another ;)

---

### Post by virtualsamana on 2009-09-22
It looks like Clonezilla is looking for both the Grub directory and the NTFS boot partition and couldn't find either because this is a "freshly" formatted HD unlike my old HD which had both Jaunty and XP on it.

Presence1960 graciously showed me how to make sure that GRUB was installed in the right place but it looks like Clonezilla is looking for the same boot managers that my old system had in order to restore my Jaunty image.

Also I should clarify that I only saved the Jaunty image and not the xp image.

---

### Post by lkraemer on 2009-09-23
Typically one would boot from a LiveCD of Clonezilla to do copies of
Partitions or Drives, because it takes care of Mount/Unmount problems.

If I ASSUME your NEW Hard drive is of equal size, or LARGER than the
existing drive, AND if you want both OS's on the New Drive, I'd suggest
just copy Drive to Drive, then when it is done, boot Gparted LiveCD,
and resize the Partitions as needed.  Followed by a Boot of both OS's
to let them find the new sizes.

I'd also suggest you "Disk Clean" the Winders Partition of all trash,
Defrag it.....a couple of times, before using Clonezilla.

If you just want a FRESH install of Ubuntu on the New drive, just install
Ubuntu, then copy your data files from the OLD Partition to the new
install after installing all your required software.  That would be the
best way to use the New Drive.  Then if you need XP, use VirtualBox
(PUEL Version) to install a new VDI of XP.  You'll not boot XP much
after working with Ubuntu for 12 months.......the way it should be....
Winders will become a whole lot less important.

OR, you can try installing GRUB to get the copied Partition booting.
I'd recommend Searching the Forum for HOWTO: GRUB.  It should be easy
to install Grub.  Or search for Tutorial & Grub.

Ref:
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

Shouldn't take long at all.

lk

---

### Post by virtualsamana on 2009-09-27
Hey lkraemer,

Thanks so much for the great info. I ended up following your suggestion and have XP running on Virtualbox. So far so good. :P

---

### Post by virtualsamana on 2009-09-27
Thanks guys. I'll try both those suggestions out. 
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

