---
title: "Partition help"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Alex De Duck on 2010-02-03
So I was trying to make a dual boot with Vista and Linux. I put on Linux first, used the advanced option to split the hard disk. I had one ntfs part for Windows, made sure it was large enough, and then put Linux on the ex3thingamabob. It worked, but windows refuses to acknowledge the ntfs part, saying it does not meet criteria. It's larger than 50 Gb, and it's an ntfs, and it's a primary partition... I noticed something about logical being the one I need. So how do I fix this please, or undo it to start again?

---

### Post by Grenage on 2010-02-03
Ideally you would install Vista first, but regardless: What is Vista's exact error message?

---

### Post by Alex De Duck on 2010-02-03
Literally that the space does not meet criteria. No code, nothing.

---

### Post by Grenage on 2010-02-03
This looks like a Vista problem, so I don't know how much help I will be.  Does the partition have the 'active' flag set?

---

### Post by Alex De Duck on 2010-02-03
I didn't see any flags or Active notations to be honest. I'll try and see if I can find any vista savvy people somewhere, thanks though!

---

### Post by Grenage on 2010-02-03
No problem.  If all else fails let vista partition the disc (under your guidance), then install Ubuntu afterwards.  The benefit of doing it that way is that Vista won't fit, and the grub bootloader will automatically link to Vista and Ubuntu.

---

### Post by Zimmer on 2010-02-03
[http://www.multibooters.co.uk/quirks.html](http://www.multibooters.co.uk/quirks.html)
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

Some reading for you, and the rest of the site may give you a clue as to how to recover.

and
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

My own dual boot Vista Linux setup has run for over 18 months now. Vista installed first.
Free space created using Vista.
Partitioning of free space via Ubuntu Live CD (gparted).
Install Ubuntu  /  AND install GRUB to same partition (not MBR).
Install EasyBCD to Vista and create Ubuntu entry there ...

The Win bootloader then shows an Ubuntu entry that actually points to GRUB . GRUB menu controls Linux boot... 

There are other ways (so I am led to believe) without the use of EasyBCD, but personally I have not yet found the definitive guide to them..  

It depends on what you want as to whether you take the simple route of installing Vista first  and letting it sort the disk problem or searching further and fixing the issue you currently have.
Best Regards
Zimmer

---

### Post by jbruced on 2010-02-03
If you boot into ubuntu and use gparted to delete your ntfs partition, windows should recognize it as available space and reformat and install there.

This will clobber grub, so you'll need to redo that.

+1 for start fresh, install windows first, then install ubuntu if it's not too much of a hassle.

---

