---
title: "Can you murder a hard drive?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by DigiTan on 2009-03-07
The last time I tried to re-partiton an NTFS volume, it worked for a few hours but in the long run it failed so bad even the manufacturer's boot disc couldn't read, write, or erase the hard disk.  Basically, it could communicate its serial and firmware information to the BIOS.  Otherwise, the hard drive was 100% bricked.

This weekend, it's my second attempt.  Same strategy, new disk model.  On the off-chance that I might be doing something wrong, I want to ask: 

**Is it possible I render a disk totally inoperable using fdisk, ntfsfix, or Windows chkdisk?**  Maybe I somehow overwrote the firmware?

---

### Post by DGortze380 on 2009-03-07
> **DigiTan said:**
> The last time I tried to re-partiton an NTFS volume, it worked for a few hours but in the long run it failed so bad even the manufacturer's boot disc couldn't read, write, or erase the hard disk.  Basically, it could communicate its serial and firmware information to the BIOS.  Otherwise, the hard drive was 100% bricked.

This weekend, it's my second attempt.  Same strategy, new disk model.  On the off-chance that I might be doing something wrong, I want to ask: 

**Is it possible I render a disk totally inoperable using fdisk, ntfsfix, or Windows chkdisk?**  Maybe I somehow overwrote the firmware?


No

---

### Post by T.J. on 2009-03-07
No, that's pretty much impossible. =)  You need a special program to rewrite or even touch firmware.

It is probable that if the manufacturer's diagnostic disc does not recognize the drive that either the drive is defective (which can happen), that the cable connecting the drive to the motherboard is bad (highly unlikely, but the old IDE ribbon cables loved to get kinks in them, for example) or not connected properly (possible, since we are all human).

Are you a hardware "do it yourself" sort of person?

---

### Post by st33med on 2009-03-08
When you repartitioned your NTFS drive, did you erase over half the partition memory?  I have been told a many times that causes problems.

---

### Post by DigiTan on 2009-03-08
> **T.J. said:**
> No, that's pretty much impossible. =)  You need a special program to rewrite or even touch firmware.

It is probable that if the manufacturer's diagnostic disc does not recognize the drive that either the drive is defective (which can happen), that the cable connecting the drive to the motherboard is bad (highly unlikely, but the old IDE ribbon cables loved to get kinks in them, for example) or not connected properly (possible, since we are all human).

Are you a hardware "do it yourself" sort of person?

Eh, sort of.  This is my second HDD upgrade on this machine and those drives still worked when I cabled them where the failed drive used to be.  That particular series of HDD has a small history of firmware issues, but mostly for large capacities (~1TB).

> When you repartitioned your NTFS drive, did you erase over half the partition memory? I have been told a many times that causes problems.
Basically all I did was expand the partition size from 40GB to 240GB.  That 40GB partition was the only one on the disk, and rest was empty space.  It's a good thing I cloned all the data before it was lost.  The **dd** command is probably the top reason I got Linux in the first place, other than curiosity.

---

### Post by randalph on 2009-03-08
If it's a recent drive, first run a SMART check [http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)
if it fails, RMA it. if it succeeds then it's not bricked.

If by "repartitioning NTFS" you mean reducing an existing NTFS partitions size to make room for linux that's probably more prone to failure than wiping the disk and making fresh partitions for windows & linux. Then reinstall windows. Then install linux.

If you are working with a windows recovery disk that came with your computer (as opposed to a "full" version of windows), they sometimes leave part of the recovery data on a separate partition on the hard drive itself, or it be overly zealous in making sure you're running the same system and the fact that you changed the partitions makes it think you're not on the original machine. if you think that's the case find a full version but still use your product key.

---

### Post by HavocXphere on 2009-03-08
If I had to guess, I'd say its not spinning up. This would suggest that the freezer trick might help (the plastic bag version). Assuming of course that there is important data on it. If not then I wouldn't bother. And its not a risk free procedure either.

Sounds like pure coincidence to me that the drive failed close to the partitioning...so I think you'll be fine with the new drive.

btw. If the new/old drive is a 500gb Seagate then you might want to google it...there are serious issues with those.

And just FYI:
There is a writeable area besides the firmware and data area. In front of the data area there is some more info. Not 100% sure what it does, but it doesn't get wiped with a format and its not in the eeeprom either. To wipe it you'd need to do a low-level format (not to be attempted by mere mortals).

---

