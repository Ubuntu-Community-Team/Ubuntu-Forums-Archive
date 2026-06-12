---
title: "NTFS defrag / move files to one end of partition"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by silkstone on 2009-03-24
I'm used to Ubuntu as a stand-alone OS but would like to install 8.10 (or maybe 9.04) as dual boot on a machine with a 500GB HD that already has XP installed.

The Windows defrag utility leaves some files stuck in the middle of the drive, however often I run it. Can anyone recommend a utility that will shift these to one end so I can do a better job of partitioning the drive?

Thanks.

---

### Post by kellemes on 2009-03-24
Could very well be these "unmovable files" are only files in use at the time of defragging.. so it's possibly you can simply resize this partition afterworths.

I'd first try defragging from safe-mode.

---

### Post by silkstone on 2009-03-24
Thanks - I'll give that a try. The rogue files are not shown as immovable, but they're not fragmented and are stuck in the middle of the drive.

---

### Post by BDNiner on 2009-03-24
I would perform a backup and then resize the partition. I would use a full disk backup utility like Acronis True Image or Norton Ghost to make an image of the entire disk. that way you can restore it afterwards if things do not go as planned.

---

### Post by StarWarrior on 2009-04-22
I just had the same problem and thought I should post a solution, should anyone come across this post:

The green unmovable parts are paging and hibernating files. Which cannot be moved.

You could try to defrag them with [PageDefrag]("http://www.microsoft.com/technet/sysinternals/FileAndDisk/PageDefrag.mspx") from Sysinternals. (Didn't try that)

Also, you can disable the paging files in system settings. The green files will go away. I found more details [here]("http://www.techsupportforum.com/microsoft-support/windows-xp-support/198023-xp-disk-defragmenter-unmovable-files.html#post1185215"). Which worked great for me.

Red files are mostly files that are in use. You could try to defrag in Recovery Mode.

Hope this helped.

---

