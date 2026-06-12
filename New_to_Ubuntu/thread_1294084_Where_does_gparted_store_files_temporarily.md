---
title: "Where does gparted store files temporarily"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2009-10-17
So here is the thing, I have two partitions side by side (one NTFS and one ext3) and I was trying to take space from one and give it to the other (from the NTFS to the ext3). Gparted was able to resize the partition but crashed during the transfer or files (unfortunately I didn't copy the error message). When I rebooted my ext3 partition is now full, I'm guessing because it still has all of the temporary files from the NTFS partition. My questions are:

Where does gparted store these files?
Can I just remove the temporary files and get the space back?

Thanks to anyone in advanced for the help

---

### Post by -Zeus- on 2009-10-17
Please post the output of:
```
df -h
du -sh /* 2>/dev/null
```

---

### Post by TadeoDiaz on 2009-10-17
Output of "df -h"

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             101G  4.9G   92G   6% /
tmpfs                 1.3G     0  1.3G   0% /lib/init/rw
varrun                1.3G  308K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
udev                  1.3G  2.8M  1.3G   1% /dev
tmpfs                 1.3G  244K  1.3G   1% /dev/shm
lrm                   1.3G  2.2M  1.3G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda1             101G   81G   16G  84% /home
/dev/sda2              71G   52G   19G  74% /media/Storage
```

Output of "du -sh /* 2>/dev/null"

```
6.1M	/bin
47M	/boot
0	/cdrom
3.0M	/dev
14M	/etc
81G	/home
0	/initrd.img
0	/initrd.img.old
389M	/lib
16K	/lost+found
52G	/media
12K	/mnt
4.0K	/new
4.0K	/old
148M	/opt
0	/proc
7.7M	/root
8.4M	/sbin
32K	/sqlxfy5Fg
4.0K	/srv
0	/sys
84K	/tmp
3.6G	/usr
476M	/var
0	/vmlinuz
0	/vmlinuz.old
```

I was trying to resize /media/Storage (sda2) to 70gb and leave /home (sda1) with 162gb

I attached a screenshot of what partition editor is showing me

Thanks for the quick reply

---

### Post by TadeoDiaz on 2009-10-17
oh btw, my /home data is only 80gb

---

