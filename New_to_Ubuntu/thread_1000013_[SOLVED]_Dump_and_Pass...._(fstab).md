---
title: "[SOLVED] Dump and Pass....? (fstab)"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by markwaypoint on 2008-12-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71938af6-77ca-48ff-bd1d-ad391d700121 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0e4b8799-6fd9-4d9c-99d2-37a5cc466477 none           swap    sw              0       0
# /dev/sdb1
UUID=f6a74353-6d94-46c8-8e5a-f66a5d76a173 /media/sdb1 ext2 defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0       0


Again fstab. Above you see my fstab. What do I need to do with dump and pass...? /dev/sda1 is my Linux HD and sdb1 is another hard drive which will be accessed via samba.

Lars

---

### Post by Dedoimedo on 2008-12-02
Maybe I'm stupid, but what are you trying to achieve, please?
Dedoimedo

---

### Post by vanadium on 2008-12-02
You normally leave dump to 0, but I would normally set the last digit to 2 in order to have the disk checked at boot time. However, your drive is an ext2, not an ext3 drive. Thus, checking will take some time and slow down booting. If you leave it to 0, you will need the discipline to check the disk yourself manually from time to time.

---

### Post by bodhi.zazen on 2008-12-02
Dump is a somewhat outdated method of backup.

pass = check at boot 

[http://docs.hp.com/en/B2355-90696/fstab.4.html](http://docs.hp.com/en/B2355-90696/fstab.4.html)

> pass number

    Used by the fsck command to determine the order in which file system checks are done. The root file system should be specified with a pass number of 1, to be checked first, and other file systems should have larger numbers. (A file system with a pass number of zero is ignored by the fsck command.)

    File systems within a drive should be assigned different pass numbers, but file systems on different drives can be checked on the same pass, to utilize possible parallelism available in the hardware. If pass number is not present, fsck checks each such file system sequentially after all eligible file systems with pass numbers have been checked.

[http://www.cptec.inpe.br/sx4/sx4man2/g1ah03e/dump.1m.html](http://www.cptec.inpe.br/sx4/sx4man2/g1ah03e/dump.1m.html)

In general you do not need to modify these numbers.

---

### Post by markwaypoint on 2008-12-02
Thanks,

@Dedoimedo: I just wanted to know what would be best to enter there... (and just some extra info... probably of no deeper sense).

Tanks though!

Lars

---

