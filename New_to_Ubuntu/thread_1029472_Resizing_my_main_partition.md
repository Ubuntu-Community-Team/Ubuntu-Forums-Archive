---
title: "Resizing my main partition"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-03
So I recently upgrade my main hardrive instead of reformatting I simply cloned the old one into the new one, how ever I still have the same size partition as the old hdd with unallocated space taking up the rest... any one have any idea how I can add the other 40 gigs to my main partition? GParted refuses to resize it for some reason... (Live CD) anyone have any other software (or can Ubuntu do it?) to resize my partition?

~Jeff

---

### Post by handydan918 on 2009-01-03
> **beastrace91 said:**
> So I recently upgrade my main hardrive instead of reformatting I simply cloned the old one into the new one, how ever I still have the same size partition as the old hdd with unallocated space taking up the rest... any one have any idea how I can add the other 40 gigs to my main partition? GParted refuses to resize it for some reason... (Live CD) anyone have any other software (or can Ubuntu do it?) to resize my partition?

~Jeff

If the unallocated space is not formatted, then you may need to format it first. Can't think of any reason gparted wouldn't work from a live cd on an unmounted partition...

---

### Post by teh_yodeler on 2009-01-03
Maybe you need to use GParted to format the unused space to the same filesystem (such as ext3) as the rest of your Ubuntu install.  Then try to resize the partition.

If that doesn't work, would it be too much of a hassle to back up your files to external media, and try a re-install, this time letting Ubuntu use the entire disk?

---

### Post by beastrace91 on 2009-01-03
Yea downloading the 64bit live CD to reformat now...

~Jeff

---

