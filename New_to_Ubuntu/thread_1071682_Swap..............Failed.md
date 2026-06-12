---
title: "Swap..............Failed"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by mikebravo on 2009-02-16
A couple of years ago I built a computer for the fun of it, and with references like 'Linux for the Brain Dead' and Ubuntu for the Terminally Stupid', I installed Fiesty as a learning experience. I have upgraded with each new release, fully expecting I would mung something up to the point I would have to blow it away and start over. Strangely, that hasn't happened. Ubuntu is reasonably forgiving, but I recall that at one time I had followed someones instructions on how to change a file so that I could watch the boot process instead of a boring splash screen. All was cool but alas, it disappeared with the next upgrade. I am a 'set it and forget it' fan (i.e. can't remember what I did) so the hell with it, but them, I recently discovered StartUp-Manager which is almost as good. The trouble is that in StartUp-manager, just after a line that says"Setting Kernel Variables...OK" and just before a line that says "Checking Root File System...OK" it gives me a line that says "Activating Swap....Fail".
   I have searched around the forum and found mcduck's reply to Bendihossan asking 'Is my swap working?'.  In short, I think mine is but I have appended the files most likely to matter in case someone would be kind enough to comment.



mike@mike-linux:~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	4883720	5120	-1
/dev/sdb5                               partition	4883720	0	-2
mike@mike-linux:~$ 


mike@mike-linux:~$ sudo blkid
[sudo] password for mike: 
/dev/sda1: UUID="d7f2743e-5dc0-434a-8fa1-3625b2204c32" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="bf145a28-5fae-43a0-907f-f8bd2d2fd1bc" 
/dev/sdb1: UUID="BBA0-0073" TYPE="vfat" 
/dev/sdb5: TYPE="swap" UUID="b7ca8233-a229-4104-8c9c-beddc2bf876c" 
/dev/sdb3: UUID="7F701E343F8049D5" TYPE="ntfs" 
/dev/sda6: UUID="16b005ab-a5d9-4b48-bf0b-87bcec653968" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="daaf74c7-2149-48ad-8285-9626df99ec40" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="60c57548-b534-49a2-aa7b-847e678a2a1b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="ee812a1f-9c79-4986-9c0d-30fccdee7f1f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="63E4-C9C6" TYPE="vfat" 
/dev/sda2: UUID="b1ef39e9-7e43-493a-bf2f-166cd9fbb7e1" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="CANON_DC" UUID="6EDD-59F7" TYPE="vfat" 
mike@mike-linux:~$ 


mike@mike-linux:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1008        951         56          0         16        472
-/+ buffers/cache:        463        544
Swap:         9538          5       9533
mike@mike-linux:~$ 

mike@mike-linux:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00015cda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13        2444    19535040   83  Linux
/dev/sda3            2445       30407   224612797+   5  Extended
/dev/sda5            2445        3052     4883728+  82  Linux swap / Solaris
/dev/sda6            3053        4268     9767488+  83  Linux
/dev/sda7            4269        4876     4883728+  83  Linux
/dev/sda8            4877        6092     9767488+  83  Linux
/dev/sda9            6093       24328   146480638+  83  Linux
/dev/sda10          24329       30407    48829536    b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001dd79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+   b  W95 FAT32
/dev/sdb2            2433        3040     4883760    5  Extended
/dev/sdb3            3526        4861    10731420    7  HPFS/NTFS
/dev/sdb5            2433        3040     4883728+  82  Linux swap / Solaris
mike@mike-linux:~$ 

mike@mike-linux:~$ sudo blkid -c /dev/null
[sudo] password for mike: 
/dev/sda1: UUID="d7f2743e-5dc0-434a-8fa1-3625b2204c32" TYPE="ext3" 
/dev/sda2: UUID="b1ef39e9-7e43-493a-bf2f-166cd9fbb7e1" TYPE="ext3" 
/dev/sda5: UUID="bf145a28-5fae-43a0-907f-f8bd2d2fd1bc" TYPE="swap" 
/dev/sda6: UUID="16b005ab-a5d9-4b48-bf0b-87bcec653968" TYPE="ext3" 
/dev/sda7: UUID="daaf74c7-2149-48ad-8285-9626df99ec40" TYPE="ext3" 
/dev/sda8: UUID="60c57548-b534-49a2-aa7b-847e678a2a1b" TYPE="ext3" 
/dev/sda9: UUID="ee812a1f-9c79-4986-9c0d-30fccdee7f1f" TYPE="ext3" 
/dev/sda10: UUID="63E4-C9C6" TYPE="vfat" 
/dev/sdb1: UUID="BBA0-0073" TYPE="vfat" 
/dev/sdb3: UUID="7F701E343F8049D5" TYPE="ntfs" 
/dev/sdb5: UUID="b7ca8233-a229-4104-8c9c-beddc2bf876c" TYPE="swap" 
mike@mike-linux:~$ free
             total       used       free     shared    buffers     cached
Mem:       1032336     990228      42108          0      22032     475644
-/+ buffers/cache:     492552     539784
Swap:      9767440       5096    9762344
mike@mike-linux:~$ 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                        0  0
# /dev/sda2
UUID=b1ef39e9-7e43-493a-bf2f-166cd9fbb7e1  /               ext3         defaults,errors=remount-ro,relatime      0  1
# /dev/sda1
UUID=d7f2743e-5dc0-434a-8fa1-3625b2204c32  /boot           ext3         defaults,relatime                        0  2
# /dev/sdb1
UUID=BBA0-0073                             /dos            vfat         defaults,utf8,umask=007,gid=46  0  1
# /dev/sda9
UUID=ee812a1f-9c79-4986-9c0d-30fccdee7f1f  /home           ext3         defaults,relatime                        0  2
# /dev/sda6
UUID=16b005ab-a5d9-4b48-bf0b-87bcec653968  /tmp            ext3         defaults,relatime                        0  2
# /dev/sda8
UUID=60c57548-b534-49a2-aa7b-847e678a2a1b  /usr            ext3         defaults,relatime                        0  2
# /dev/sda7
UUID=daaf74c7-2149-48ad-8285-9626df99ec40  /var            ext3         defaults,relatime                        0  2
# /dev/sda10
UUID=63E4-C9C6                             /windows        vfat         defaults,utf8,umask=007,gid=46  0  1
# /dev/sda5
UUID=bf145a28-5fae-43a0-907f-f8bd2d2fd1bc  none            swap         sw                              0  0
# /dev/sdb5
UUID=b7ca8233-a229-4104-8c9c-beddc2bf876c  none            swap         sw                              0  0
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec                0  0
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec             0  0
/dev/sdb5                                  /media/sdb5     swap         sw                              0  0
/dev/sdb1                                  /media/sdb1     vfat         defaults                        0  0
/dev/sdb3                                  /media/sdb3     ntfs         defaults                        0  0

---

### Post by wolfen69 on 2009-02-16
on the second page of [this]("http://ubuntuforums.org/showthread.php?t=365530") thread, a problem like yours was solved.

---

### Post by ajgreeny on 2009-02-16
You can easily check if your swap is enabled by running ```
free -m
``` in terminal.  This is my output with the last line showing the current state of swap usage.  If yours is not enabled the size will be nil (0)
```
 total       used       free     shared    buffers     cached
Mem:          1011        995         15          0         15        573
-/+ buffers/cache:        406        604
Swap:         1192         38       1153

```

---

### Post by taurus on 2009-02-16
> **mikebravo said:**
> 
mike@mike-linux:~$ sudo blkid
[sudo] password for mike: 
/dev/sda1: UUID="d7f2743e-5dc0-434a-8fa1-3625b2204c32" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="bf145a28-5fae-43a0-907f-f8bd2d2fd1bc" 
/dev/sdb1: UUID="BBA0-0073" TYPE="vfat" 
/dev/sdb5: TYPE="swap" UUID="b7ca8233-a229-4104-8c9c-beddc2bf876c" 
/dev/sdb3: UUID="7F701E343F8049D5" TYPE="ntfs" 
/dev/sda6: UUID="16b005ab-a5d9-4b48-bf0b-87bcec653968" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="daaf74c7-2149-48ad-8285-9626df99ec40" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="60c57548-b534-49a2-aa7b-847e678a2a1b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="ee812a1f-9c79-4986-9c0d-30fccdee7f1f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="63E4-C9C6" TYPE="vfat" 
/dev/sda2: UUID="b1ef39e9-7e43-493a-bf2f-166cd9fbb7e1" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="CANON_DC" UUID="6EDD-59F7" TYPE="vfat" 
mike@mike-linux:~$ 


mike@mike-linux:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1008        951         56          0         16        472
-/+ buffers/cache:        463        544
Swap:         9538          5       9533
mike@mike-linux:~$ 

mike@mike-linux:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00015cda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13        2444    19535040   83  Linux
/dev/sda3            2445       30407   224612797+   5  Extended
/dev/sda5            2445        3052     4883728+  82  Linux swap / Solaris
/dev/sda6            3053        4268     9767488+  83  Linux
/dev/sda7            4269        4876     4883728+  83  Linux
/dev/sda8            4877        6092     9767488+  83  Linux
/dev/sda9            6093       24328   146480638+  83  Linux
/dev/sda10          24329       30407    48829536    b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001dd79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+   b  W95 FAT32
/dev/sdb2            2433        3040     4883760    5  Extended
/dev/sdb3            3526        4861    10731420    7  HPFS/NTFS
/dev/sdb5            2433        3040     4883728+  82  Linux swap / Solaris
mike@mike-linux:~$ 

mike@mike-linux:~$ sudo blkid -c /dev/null
[sudo] password for mike: 
/dev/sda1: UUID="d7f2743e-5dc0-434a-8fa1-3625b2204c32" TYPE="ext3" 
/dev/sda2: UUID="b1ef39e9-7e43-493a-bf2f-166cd9fbb7e1" TYPE="ext3" 
/dev/sda5: UUID="bf145a28-5fae-43a0-907f-f8bd2d2fd1bc" TYPE="swap" 
/dev/sda6: UUID="16b005ab-a5d9-4b48-bf0b-87bcec653968" TYPE="ext3" 
/dev/sda7: UUID="daaf74c7-2149-48ad-8285-9626df99ec40" TYPE="ext3" 
/dev/sda8: UUID="60c57548-b534-49a2-aa7b-847e678a2a1b" TYPE="ext3" 
/dev/sda9: UUID="ee812a1f-9c79-4986-9c0d-30fccdee7f1f" TYPE="ext3" 
/dev/sda10: UUID="63E4-C9C6" TYPE="vfat" 
/dev/sdb1: UUID="BBA0-0073" TYPE="vfat" 
/dev/sdb3: UUID="7F701E343F8049D5" TYPE="ntfs" 
/dev/sdb5: UUID="b7ca8233-a229-4104-8c9c-beddc2bf876c" TYPE="swap" 
mike@mike-linux:~$ free
             total       used       free     shared    buffers     cached
Mem:       1032336     990228      42108          0      22032     475644
-/+ buffers/cache:     492552     539784
Swap:      9767440       5096    9762344
mike@mike-linux:~$ 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                        0  0
# /dev/sda2
UUID=b1ef39e9-7e43-493a-bf2f-166cd9fbb7e1  /               ext3         defaults,errors=remount-ro,relatime      0  1
# /dev/sda1
UUID=d7f2743e-5dc0-434a-8fa1-3625b2204c32  /boot           ext3         defaults,relatime                        0  2
# /dev/sdb1
UUID=BBA0-0073                             /dos            vfat         defaults,utf8,umask=007,gid=46  0  1
# /dev/sda9
UUID=ee812a1f-9c79-4986-9c0d-30fccdee7f1f  /home           ext3         defaults,relatime                        0  2
# /dev/sda6
UUID=16b005ab-a5d9-4b48-bf0b-87bcec653968  /tmp            ext3         defaults,relatime                        0  2
# /dev/sda8
UUID=60c57548-b534-49a2-aa7b-847e678a2a1b  /usr            ext3         defaults,relatime                        0  2
# /dev/sda7
UUID=daaf74c7-2149-48ad-8285-9626df99ec40  /var            ext3         defaults,relatime                        0  2
# /dev/sda10
UUID=63E4-C9C6                             /windows        vfat         defaults,utf8,umask=007,gid=46  0  1
# /dev/sda5
UUID=bf145a28-5fae-43a0-907f-f8bd2d2fd1bc  none            swap         sw                              0  0
# /dev/sdb5
UUID=b7ca8233-a229-4104-8c9c-beddc2bf876c  none            swap         sw                              0  0
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec                0  0
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec             0  0
/dev/sdb5                                  **[COLOR="Red"]/media/sdb5[/COLOR]**     swap         sw                              0  0
/dev/sdb1                                  /media/sdb1     vfat         defaults                        0  0
/dev/sdb3                                  /media/sdb3     ntfs         defaults                        0  0

The mount point is wrong.  Should have said **none**.

---

### Post by mikebravo on 2009-02-17
> **wolfen69 said:**
> on the second page of [this]("http://ubuntuforums.org/showthread.php?t=365530") thread, a problem like yours was solved.

On the third page of that post, NeoFax said that can be caused by mixing PATA with SATA as I have done.

---

### Post by mikebravo on 2009-02-19
Changed mount point as tarus suggested. No joy. Still get Activating Swap....Failed.   Change to fstab as shown:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                        0  0
# /dev/sda2
UUID=b1ef39e9-7e43-493a-bf2f-166cd9fbb7e1  /               ext3         defaults,errors=remount-ro,relatime      0  1
# /dev/sda1
UUID=d7f2743e-5dc0-434a-8fa1-3625b2204c32  /boot           ext3         defaults,relatime                        0  2
# /dev/sdb1
UUID=BBA0-0073                             /dos            vfat         defaults,utf8,umask=007,gid=46  0  1
# /dev/sda9
UUID=ee812a1f-9c79-4986-9c0d-30fccdee7f1f  /home           ext3         defaults,relatime                        0  2
# /dev/sda6
UUID=16b005ab-a5d9-4b48-bf0b-87bcec653968  /tmp            ext3         defaults,relatime                        0  2
# /dev/sda8
UUID=60c57548-b534-49a2-aa7b-847e678a2a1b  /usr            ext3         defaults,relatime                        0  2
# /dev/sda7
UUID=daaf74c7-2149-48ad-8285-9626df99ec40  /var            ext3         defaults,relatime                        0  2
# /dev/sda10
UUID=63E4-C9C6                             /windows        vfat         defaults,utf8,umask=007,gid=46  0  1
# /dev/sda5
UUID=bf145a28-5fae-43a0-907f-f8bd2d2fd1bc  none            swap         sw                              0  0
# /dev/sdb5
UUID=b7ca8233-a229-4104-8c9c-beddc2bf876c  none            swap         sw                              0  0
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec                0  0
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec             0  0
/dev/sdb5                                  [COLOR="Red"]none[/COLOR]            swap         sw                              0  0
/dev/sdb1                                  /media/sdb1     vfat         defaults                        0  0
/dev/sdb3                                  /media/sdb3     ntfs         defaults                        0  0



How come there exists this line for the swap on sdb5 but not a matching line for sda5 ?   I think I need to talk to neofax.

---

### Post by taurus on 2009-02-19
I would remove that line since you already have an entry for that swap partition, using UUID (/dev/sdb5).

```
/dev/sdb5 none swap sw 0 0
```

---

