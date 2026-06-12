---
title: "Which HDD format is Best?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by nnjond on 2009-12-12
Hi,

I have x many divers files on an ancillary hdd which i'm transfering to a larger drive. should i switch from FAT 32 format to something else?

Thanks.

---

### Post by SuperSonic4 on 2009-12-12
> **nnjond said:**
> Hi,

I have x many divers files on an ancillary hdd which i'm transfering to a larger drive. should i switch from FAT 32 format to something else?

Thanks.

Yes, Fat32 is terribly old now. What to change it to depends on who needs to access it

Linux Only - normal size - ext4
           - large size  - xfs

Windows    - For large compatability - ntfs
           - For just a couple of local machines - ext3 + fs-driver

---

### Post by nnjond on 2009-12-12
Thanks for your advice.

My new ancillary HDD is a 500gb for my own Linux desktop; I take it that's normal and ext4 is most appropriate.

---

### Post by SuperSonic4 on 2009-12-12
> **nnjond said:**
> Thanks for your advice.

My new ancillary HDD is a 500gb for my own Linux desktop; I take it that's normal and ext4 is most appropriate.

Most likely but by size I was referring to the size of the files you were going to put on it. If, for example it's standard music files than ext4 is best (~6mb) but if it's going to be CD/DVD ISOs(700mb/4gb) than xfs would be better

Ultimately it's up to you, ext4 does work well for all sizes and it's never had a problem on my system but ext3 has had the benefit of years of improvement

---

### Post by The Cog on 2009-12-12
I have my doubts about ext4 - I believe it is prone to massive data loss on occasions, system crashes particularly. I have seen this personally several times in the 6 weeks or so of using ext4 (before removing it again), although I have not seen any data loss on other Linux filesystem (mostly reiserfs and jfs, some ext3) in more than 5 years.

So I would advise using ext3 rather than ext4. I can't personally vouch for ext3 as I have not used it much although I know it has a long and respectable history. Actually, I use jfs for my internal and extenal disks, and have survived a number of system crashes without any damage. I can recommend jfs through personal experience.

---

### Post by ezsit on 2009-12-12
I would stick with ext3 or XFS, both of which I have used and have never had any issues with either. ext3 has been the default for so long and has the benefit of being usable by any version of Linux that I fail to see a need for another choice. ext4 still gets reports of trouble with storing large files, multi-gigabyte sized files, and has been known to hang the system when copying or moving such large files.

---

