---
title: "Converting Data Drives from ext3 to ext4"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Marko723 on 2011-01-01
Hello,

I recently upgraded my media server with a new MB/CPU combo (Dumped the old P4).  Also used this opportunity to installed a new boot drive and do a fresh install.  I ported all my data drives over to the new box and brought everything backup on-line

10.04LTS is reporting my boot drive as ext4, my data drives (all separate stand-alone physical - NO RAID) are still ext3.  I'd like to convert to ext4.

Found some, what appears to be easy commands to achieve this.```
# cd /; umount /dev/sdb1
# tune2fs -O extents,uninit_bg,dir_index /dev/sdb1
```

Question #1)  I assume this can be done on a drive containing data?  Can this be done safely?  Am I better off backing things up, and just reformatting with ext4?
 
Question #2) My fstab listing is below.  Can I just change the ext3 to a 4 and leave the rest the same, or do I have to make additional modifications?
```
/dev/sdb1 /mnt/H1 ext3 defaults 1 1
/dev/sdc1 /mnt/H2 ext3 defaults 1 1
/dev/sdd1 /mnt/H3 ext3 defaults 1 1
/dev/sde1 /mnt/H4 ext3 defaults 1 1
/dev/sdf1 /mnt/WD1 ext3 defaults 1 1
/dev/sdg1 /mnt/WD2 ext3 defaults 1 1
/dev/sdh1 /mnt/WD3 ext3 defaults 1 1
/dev/sdi1 /mnt/WD4 ext3 defaults 1 1
/dev/sdj1 /mnt/WD5 ext3 defaults 1 1
/dev/sdk1 /mnt/WD6 ext3 defaults 1 1
```

Thanks
Mark

---

### Post by TeoBigusGeekus on 2011-01-01
1) I think you'd be better off doing a backup and reformatting (at least that's what I'd do).

2) Just change ext3 to ext4 and you should be fine. Why don't you change the final 1 to 2 on every entry, so that the volumes are checked after a number of remounts?

---

### Post by Marko723 on 2011-01-01
> **TeoBigusGeekus said:**
> 1) I think you'd be better off doing a backup and reformatting (at least that's what I'd do).

2) Just change ext3 to ext4 and you should be fine. Why don't you change the final 1 to 2 on every entry, so that the volumes are checked after a number of remounts?

Thanks for the reply.  I started off leaning towards a format, but thought I would check with some experts before starting down that road. 
 
As for #2, I'll have to look deeper in to this.   I was just following a HOW-TO I found a while back, it's served well.  

Thanks again. 
Mark

---

