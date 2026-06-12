---
title: "Ext4 and NTFS issues..."
date: 2010-06-09
forum: New to Ubuntu
---

### Post by gallifrey on 2010-06-09
Hello all,
            I have been using Ubuntu for quite a while now, and love what they have done with 10.04. I have been using it exclusively as my personal and professional system. However, my company recently purchased new software which only works under Windoze, so I have had to install W7 and the new software onto a partition on my hard drive. 

The problem I have is that whereas I can access the NTFS partition from Ubuntu when I need to, the reverse is not true, and Windoze won't even let me see my Ext4 home partition, which is where most of my data is kept. 

I have experimented with certain programs, like Ext2Explore, Ext2Fsd and Ext2 IFS, but with limited success. The only other thought I am having now is that for convenience' sake, I convert my home partition to NTFS, but from what I can gather, this would impact my Linux system's performance, which I really do not want. Likewise if I downgraded from Ext4 to Ext3.

I don't care about the performance from the W7 point of view, as I only need it for work. 

Please, if somebody has another way, or any suggestions, I would be most grateful. Thank you!

---

### Post by John Bean on 2010-06-09
If you need r/w access from Windows then forget ext4 (and many ext3) filesystems. I find ext2explorer reads  ext4 reliably though.

My solution is to run Windows (XP in my case) in a VM like VirtualBox rather than dual-booting. The host filesystem is exposed to the client Windows system as CIFS shares with remarkably little loss of performance and complete safety.

---

### Post by alphacrucis2 on 2010-06-09
> **gallifrey said:**
> Hello all,
            I have been using Ubuntu for quite a while now, and love what they have done with 10.04. I have been using it exclusively as my personal and professional system. However, my company recently purchased new software which only works under Windoze, so I have had to install W7 and the new software onto a partition on my hard drive. 

The problem I have is that whereas I can access the NTFS partition from Ubuntu when I need to, the reverse is not true, and Windoze won't even let me see my Ext4 home partition, which is where most of my data is kept. 

I have experimented with certain programs, like Ext2Explore, Ext2Fsd and Ext2 IFS, but with limited success. The only other thought I am having now is that for convenience' sake, I convert my home partition to NTFS, but from what I can gather, this would impact my Linux system's performance, which I really do not want. Likewise if I downgraded from Ext4 to Ext3.

I don't care about the performance from the W7 point of view, as I only need it for work. 

Please, if somebody has another way, or any suggestions, I would be most grateful. Thank you!

As far as I know there is no software currently available that allows windows to properly access ext4 partitions. It is possible to convert ext3 to ext4 using tune2fs but I don't think it is possible to go the other way. You would probably have to recreate the partition as ext3 and do a reinstall. Another possibility might be to create a shared ntfs or fat32 partition that both OS's can access.

---

### Post by gallifrey on 2010-06-09
Doh! I never thought of a VM!! That would be an ideal solution. I run Solaris in a VM, so I should have thought of that sooner!

Thanks guys!

---

### Post by John Bean on 2010-06-09
> **gallifrey said:**
> Doh!

Now that's something I didn't expect to hear from a Time Lord. Homer Simpson as the next Doctor Who, anyone? ;-)

---

