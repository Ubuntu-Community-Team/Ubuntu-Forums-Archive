---
title: "getting back windows from grub"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by dagarshali on 2010-03-05
Hi,
I have ubuntu karmic and windows 7 installed on my machine and since i rarely use windows 7 and it was taking a lot of hard disk space, i logged into windows and resized the partition.

Now, i am not able to log into windows via grub...

Can anybody help getting that back..

Best Regards,
Vishwa

---

### Post by Ozymandias_117 on 2010-03-05
Have you tried running ```
sudo update-grub
```

---

### Post by dagarshali on 2010-03-05
i tried it now and this is the output..

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/Boot: No such file or directory
ls: cannot access /var/lib/os-prober/mount/Windows: No such file or directory
done

---

### Post by dagarshali on 2010-03-05
and when i see the partitions in gparted..the partition that i was making in windows wasn't successful at all..I see yellow triangle next to the windows partition in gparted..

---

### Post by clapton on 2010-03-05
Hello, do you know how to use gedit?

You should mount the first partition of windows7 (about 120 mb)

Next you should open it and you'll see 2 folders /boot. One /boot other /Boot.
Rename /boot and update-grub.

I'm sorry, but I can't use linux at work, I don't know CLI commands :D

---

### Post by dagarshali on 2010-03-05
Hi,
this what i get for fdisk -l

should i mount the ntfs one?

And when i did, i don't see any folders that were there before..all i see is a folder called Intel
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19559   157099176    7  HPFS/NTFS
/dev/sda2           21941       33002    88855515    f  W95 Ext'd (LBA)
/dev/sda3           33003       38913    47480107+  83  Linux
/dev/sda5           21941       22462     4192933+  82  Linux swap / Solaris
/dev/sda6           22463       25073    20972826   83  Linux
/dev/sda7           25074       33002    63689661   83  Linux

---

### Post by clapton on 2010-03-05
> **dagarshali said:**
> Hi,
this what i get for fdisk -l

should i mount the ntfs one?

And when i did, i don't see any folders that were there before..all i see is a folder called Intel
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19559   157099176    7  HPFS/NTFS
/dev/sda2           21941       33002    88855515    f  W95 Ext'd (LBA)
/dev/sda3           33003       38913    47480107+  83  Linux
/dev/sda5           21941       22462     4192933+  82  Linux swap / Solaris
/dev/sda6           22463       25073    20972826   83  Linux
/dev/sda7           25074       33002    63689661   83  Linux

Do you install windows in fat32 system?
If the answer is yes, you need mount this one
/dev/sda1   *           1       19559   157099176    7  HPFS/NTFS

---

### Post by dagarshali on 2010-03-05
my apologies..i was able to see all the stuff when i did

sudo mount /dev/sda1 /mnt
these are the contents listed.. i didn't fine /boot.. The file Boot is empty

> AtmApInit.txt           msdia80.dll          RHDSetup.log
BIOS                    MSOCache             RtkApoApi.dll
Boot                    pagefile.sys         setup.log
bootmgr                 _PartitionInfo       stapi32.dll
BOOTSECT.BAK            PerfLogs             swshare
Config.Msi              ProgramData          sysiclog.txt
Documents and Settings  Program Files        sysiclog.txt.bak
Drivers                 Program Files (x86)  System Volume Information
hiberfil.sys            Python25             Users
ICAutoUpdate.log.bak    QUARANTINE           VJVod_Cache
Intel                   Recovery             Windows


---

### Post by clapton on 2010-03-05
I'm not using ubuntu. I can't see it.

One folder boot is empty, folder BOOT is not empty and has the main files to boot windows :)

---

