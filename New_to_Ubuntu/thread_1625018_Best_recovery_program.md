---
title: "Best recovery program"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-18
Which is the best recovery program..?

---

### Post by Zzl1xndd on 2010-11-18
Do you mean back up and recovery, recovering erased data, or something else?

If back up I use Déjà Dup.

---

### Post by ppv on 2010-11-18
Hard disk recovery....???
It depends on what is the problem...and not all programs would give the same results...
There are probably more options for recovery under windows than under linux.
One recovery program is testdisk.

---

### Post by karthick87 on 2010-11-18
> **tweakedenigma said:**
> Do you mean back up and recovery, recovering erased data, or something else?

If back up I use Déjà Dup.


Recovering erased data.

---

### Post by rcayea on 2010-11-18
I just asked a similar question and here are the programs I was referenced to:

photorec
testdisk
recuva
Easeus file recovery
ddrescue


I found, actually, if you have access to a windows machine and can slave the dead drive that testdisk worked best.

---

### Post by rcayea on 2010-11-18
Although, for windows, Recuva is the best, in my opinion.

---

### Post by alphaamanitin on 2010-11-18
Depends on your needs.  Do you actually need to recover data?  What situation are you envisioning yourself recovering data?

AlphaA

---

### Post by endotherm on 2010-11-18
the question you need to ask yourself is why does the data need recovered. 
if you just need undelete, then tools like recuva are great.
if your whole partition has disappeared, then TestDisk is the best bet.
if the drive is failing, then your first step is to make an image of it, so you can get it off the bad hardware, using a tool like ddrescue or partimage. 

in basically all cases, you need another drive with free space  >=  to the drive you are recovering off of. it is a very terrible idea to ever recover data to the same drive it was lost on, as you will be over writing the very files you wish to recover, which will make the recovery process much harder, or likely impossible.

---

### Post by usererror on 2010-11-22
I just made a major blunder and want to give "two thumbs up" to "PHOTOREC"

I accidentally deleted 10GB worth of photos.  The .Trash-1000 folder was empty.  I installed the APT package "testdisk" and used "photorec" to scan for lost files and it got back 99% of my files back.  I am quite pleased.  Recovery time was several hours, but it worked great!

The only downside was that the file names were not the same as before but the EXIF data from the .jpg files was still intact.

---

### Post by Ruy Benton on 2010-11-22
> **karthick87 said:**
> Which is the best recovery program..?

Hi,

I work in a recover company.

And we would like to move completely to UBUNTU, but some tools are found in another OS.

We use ddrescue to copy HD (the best)
testdisk very good.

But for RAID 0, 5 and .... We don't have many.

Best Regards,

Ruy

---

