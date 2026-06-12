---
title: "Grub Error 17 oF DOOM"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by cerealtx on 2009-02-09
okay so yah, used my laptop this morning just fine, come home turn it on grub error 17... im on live cd right now, partion editor just shows that the entier drive is unallocated, i looked for information on it burned a copy of super grub fooled with that but with no luck, really hoping i don't have to reinstall
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   230246400   234438655     2096128    c  W95 FAT32 (LBA)
/dev/sda2       224829675   234436544     4803435    5  Extended
/dev/sda5       224829738   234436544     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
anyone know what i should do or where to look

---

### Post by unplugged23 on 2009-02-09
Hmmm, I thought error 17 just meant it was having an issue with the boot history. At least thats what it was in my case, nothing major and easily fixable. Sounds a little suspicious to be honest, but i guess i still have a little windows paranoia hanging around. sorry i cant help much, but i really am interested seeing as i had the same error before and it was only because i had changed a partition flag and the issue was fixed within minutes.

---

### Post by kansasnoob on 2009-02-09
Was this a Wubi install?

---

### Post by cerealtx on 2009-02-09
> **kansasnoob said:**
> Was this a Wubi install?

no was not the only thing i have on the drive is ubuntu, i do have a virtualbox xp setup on it

---

### Post by cerealtx on 2009-02-09
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```
my menu.lst is empty... im sure this is not good

---

### Post by caljohnsmith on 2009-02-09
> **cerealtx said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   230246400   [COLOR="Red"]234438655[/COLOR]     2096128    c  W95 FAT32 (LBA)
/dev/sda2       [COLOR="Red"]224829675[/COLOR]   234436544     4803435    5  Extended
/dev/sda5       224829738   234436544     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

I don't know what happened, but your partition table is corrupt; the sda1 overlaps with your sda2 extended partition. Also, there is a really large chunk of unused space on your HDD that I would imagine is where one or more partitions are supposed to be. In order to recover your correct partition table, I would recommend downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and of the partitions that give you a listing, let me know which ones you want to recover. We can work from there if you want.

---

### Post by cerealtx on 2009-02-09
thank you very much yah it does look like its goign to take some time will post when its done, thank you!
edit:it should just be 1 partition only partition i know of is the swap and the main

---

### Post by unplugged23 on 2009-02-09
So out of curiosity and to prevent myself and others from getting this into that situation; how would that happen?

---

### Post by caljohnsmith on 2009-02-09
> **unplugged23 said:**
> So out of curiosity and to prevent myself and others from getting this into that situation; how would that happen?
I would like to know that too; maybe cerealtx can give us some clues what he was doing prior to getting the Grub error 17 that led to corrupting his HDD's partition table. :)

---

### Post by cerealtx on 2009-02-09
like i said, nothing, i went to school loaded it up surfed some checked email, came home loaded laptop up, and poof grub error 17 didn't do anything, didn't even update the repo cache i have no idea why it happened

---

### Post by unplugged23 on 2009-02-09
Like i said, brings back a little windows paranoia for me, but i guess i need to learn to just shake it off. has anyone else had an experience with error 17?

---

### Post by cerealtx on 2009-02-09
```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 13994 254 59  224829608
D HPFS - NTFS              0   1  1 14591 254 63  234420417
D HPFS - NTFS           3264   1  1 14592 254 63  182000322
D Linux Swap            5219   1  1  5470 254 42    4048296
D HPFS - NTFS           5471   1  1 14592 254 63  146544867 [New Volume]
D Linux Swap           13995   1  1 14592 254 40    9606784
D Linux Swap           14199   1  1 14331 254 41    2136560
D FAT32 LBA            14332  44 49 14593  33 32    4192256 [MEDIADIRECT]

```

i think this is the right one

```
   D Linux                    0   1  1 13994 254 59  224829608
Directory /

drwxr-xr-x     0     0      4096  4-Feb-2009 14:57 .
drwxr-xr-x     0     0      4096  4-Feb-2009 14:57 ..
drwx------     0     0     16384  9-Jul-2008 03:21 lost+found
drwxr-xr-x     0     0      4096  2-Jul-2008 10:34 var
drwxr-xr-x     0     0     12288  9-Feb-2009 16:43 etc
drwxr-xr-x     0     0      4096  9-Feb-2009 16:14 media
lrwxrwxrwx     0     0        11  9-Jul-2008 03:21 cdrom
drwxr-xr-x     0     0      4096 26-Dec-2008 02:29 bin
drwxr-xr-x     0     0      4096  4-Feb-2009 14:58 boot
drwxr-xr-x     0     0      4096 26-Dec-2008 02:41 dev
drwxr-xr-x     0     0      4096  9-Jul-2008 03:29 home
drwxr-xr-x     0     0      4096  2-Jul-2008 10:16 initrd
drwxr-xr-x     0     0     12288 29-Jan-2009 16:09 lib
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 mnt
drwxr-xr-x     0     0      4096  2-Jul-2008 10:16 opt
drwxr-xr-x     0     0      4096 15-Apr-2008 05:53 proc
drwxr-xr-x     0     0      4096 26-Jan-2009 21:30 root
drwxr-xr-x     0     0      4096 29-Jan-2009 16:10 sbin
drwxr-xr-x     0     0      4096  2-Jul-2008 10:16 srv
drwxr-xr-x     0     0      4096 19-Apr-2008 05:05 sys
drwxrwxrwt     0     0      4096  9-Feb-2009 16:43 tmp
drwxr-xr-x     0     0      4096 26-Dec-2008 02:30 usr
lrwxrwxrwx     0     0        33  4-Feb-2009 14:57 initrd.img
lrwxrwxrwx     0     0        30  4-Feb-2009 14:57 vmlinuz
-rw-r--r--     0     0         5 18-Dec-2008 13:56 .suspended
lrwxrwxrwx     0     0        29 26-Dec-2008 02:43 vmlinuz.27422
                                                   Next

```

---

### Post by kansasnoob on 2009-02-09
> **cerealtx said:**
> no was not the only thing i have on the drive is ubuntu, i do have a virtualbox xp setup on it

My best guess is that it's a bug in Virtualbox!

No "virtual" atmosphere, whether it's Virtualbox, VMWare, or Wubi provides true stability to any solid disc environment!

Multi-booting is much more stable!

---

### Post by caljohnsmith on 2009-02-10
> **cerealtx said:**
> ```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] Linux                    0   1  1 13994 254 59  224829608
[COLOR="Red"]D[/COLOR] HPFS - NTFS              0   1  1 14591 254 63  234420417
[COLOR="Red"]D[/COLOR] HPFS - NTFS           3264   1  1 14592 254 63  182000322
[COLOR="Red"]D[/COLOR] Linux Swap            5219   1  1  5470 254 42    4048296
[COLOR="Red"]D[/COLOR] HPFS - NTFS           5471   1  1 14592 254 63  146544867 [New Volume]
[COLOR="Red"]L[/COLOR] Linux Swap           13995   1  1 14592 254 40    9606784
[COLOR="Red"]D[/COLOR] Linux Swap           14199   1  1 14331 254 41    2136560
[COLOR="Red"]D[/COLOR] FAT32 LBA            14332  44 49 14593  33 32    4192256 [MEDIADIRECT]

```

OK, that's great, it looks like you will most likely be able to recover your partitions just fine. Is it safe to assume you don't want your MEDIADIRECT partition? If you don't, then how about using your up/down arrow keys to select each partition in the deep search results, and then use your right/left arrow keys to mark each partition as I've show highlighted above in red. Once you are sure your partitions are marked exactly as shown above, press enter to get the next screen, and then choose "Write" to write the new partition table. Then reboot your Live CD and please post the output of:
```
sudo fdisk -lu
```
Also, you might need to reinstall Grub to your HDD's MBR (Master Boot Record) to get it working, so how about doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know if you can boot into your Ubuntu install or not. We can work from there.

---

