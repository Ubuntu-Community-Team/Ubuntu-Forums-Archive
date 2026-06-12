---
title: "How do I know if I have: ext2, ext3, reiserfs, xfs, jfs, GNU/Linux, FAT, NTFS?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-19
Hi

How do I know which Filesystem I have, ext2, ext3, reiserfs, xfs, jfs of GNU/Linux, FAT, or NTFS of MS Windows?

Just good to know I guess....

---

### Post by perlluver on 2009-02-19
If you installed it by clicking on guided install, it will be Ext3 by default.  Or in a terminal, Applications>Accessories>Terminal, and then type this ```
cat /etc/fstab
``` and that will show you what the default disk file system is.

---

### Post by feisty on 2009-02-19
sys--->adm.--->sytem monitor--->file systems

---

### Post by listerdl on 2009-02-19
What difference does it make? (Am I asking the most basic question?)

---

### Post by listerdl on 2009-02-19
> **feisty said:**
> sys--->adm.--->sytem monitor--->file systems

amazing thanks...

---

### Post by perlluver on 2009-02-19
If you have ntfs, Linux won't run very good or at all on it.  Unless you installed it through Wubi.  Otherwise Ext3, is stable and pretty fast.  Let me give you a list: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems).

---

### Post by uberg on 2009-02-19
You can also run:
code:
sudo fdisk -l
To print out a list of all the files systems currently on your system.  There is more than one way to do things.  Isn't Linux wonderful.
Joe

---

### Post by listerdl on 2009-02-19
> **uberg said:**
> isn't linux wonderful.


yes!

---

### Post by listerdl on 2009-02-19
> **uberg said:**
> You can also run:
code:
sudo fdisk -l
To print out a list of all the files systems currently on your system.  There is more than one way to do things.  Isn't Linux wonderful.
Joe

I ran the above code and it generated

```
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9172    73674058+  83  Linux
/dev/sda2            9173        9546     3004155    5  Extended
/dev/sda5            9173        9546     3004123+  82  Linux swap / Solaris

```

Is that really standard? It seems to work very well....

---

### Post by uberg on 2009-02-19
i am not sure what you mean by standard.  If you mean if fdisk is standard then yes.  If you mean does your setup look standard then, yes.  At least from a standard install point of view.

---

### Post by perlluver on 2009-02-19
Here is my fdisk -l, so you can compare: ```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         124      995998+  82  Linux swap / Solaris
/dev/sda2             125       24321   194362402+   5  Extended
/dev/sda5             125       24321   194362371   83  Linux
```

---

### Post by uberg on 2009-02-19
Okay, i hate to admit it here is fdisk -l for further comparision.  Don't laugh at me.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bfc9bfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2225    17872281    7  HPFS/NTFS
/dev/sda2            2226       19457   138416040    5  Extended
/dev/sda5            2226        2349      995998+  82  Linux swap / Solaris
/dev/sda6            2350       19457   137419978+  83  Linux
```

---

### Post by bodhi.zazen on 2009-02-19
fdisk is sometimes a bit "Vague" and lists multiple file types as "Linux". Also I ave seen fdisk mis identify a file system.

Other tools are :

1. First mount the partition (the mount command should automagically identify the file system)

```
sudo mkdir /media/tmp
sudo mount /dev/sdxy /media/tmp
```

Where "/dev/sdxy" is the partition in question.

then issue :

```
mount
```

or 

```
df -Th
```

If you like, you can filter teh output with grep :

mount | grep --color=always '/dev/sdxy'

---

