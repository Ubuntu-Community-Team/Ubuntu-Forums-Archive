---
title: "Determining system partition during grub2 reinstall?"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by apoikola on 2011-03-24
From my bootloader menu I choose the "wrong windows" and I got a big red error -message. I say "wrong windows vista", because this had happened me earlier. I knew that in my boot-loader menu there was one windows vista link that works fine and the other-one that causes the crash.

Last time when it crashed I reinstalled ubuntu, but now I'm not able to do even that.

The big red error looked like this: [http://www4.slikomat.com/10/0313/j9x-SNC000.jpg](http://www4.slikomat.com/10/0313/j9x-SNC000.jpg)

And after reboot:
```

error: no such partition
grub rescue>
```

I did a Ubuntu 10.10 LiveCD on a usb-stick and started to follow these instructions: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I tried the first method titled:  "SIMPLEST - Copy GRUB 2 Files from the LiveCD"

As I'm more or less newbie in linux administration (basic user I would say) I am not completely sure which is my system partition?

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1531       19182   141787996    7  HPFS/NTFS
/dev/sda3           19182       53117   272579075    f  W95 Ext'd (LBA)
/dev/sda5           31931       53117   170179525+   7  HPFS/NTFS
```

So far I've tried to re-install grub to sda1 , sda2 and sda5 (in that order). sda3 I can't mount. I assume that at least the first trial with sda1 was a mistake :/

Now I get in reboot:
```
[Minimal BASH-like blah blah blah.... ]
grub>
```

I was ready to give up and reinstall ubuntu again, but probably because of some corrupt partitioning the installation hangs in the "preparing to install ubuntu" phase. Same issue as here: [http://ubuntuforums.org/showthread.php?t=1615558](http://ubuntuforums.org/showthread.php?t=1615558)

I'm helpless, and will appriciate all advices.

The boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) says the following:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,579,449    24,579,387  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     24,579,450   308,155,441   283,575,992   7 HPFS/NTFS
/dev/sda3         308,156,414   853,314,563   545,158,150   f W95 Ext d (LBA)
/dev/sda5         512,955,513   853,314,563   340,359,051   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7958 MB, 7958691840 bytes
151 heads, 15 sectors/track, 6862 cylinders, total 15544320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192    15,544,319    15,536,128   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7ae06a40-0f27-154b-b036-cdf80310840b   ext2       casper-rw                     
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        84FCA943FCA92FFA                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        80E201CA29389E39                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14E0-3A3D                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  20 05 00 00 98 95 03 97  01 4b 28 27 00 00 00 00  | ........K('....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  98 00 00 00 00 00 00 00  01 00 00 00 68 00 00 00  |............h...|
00000030  00 00 00 00 00 00 00 00  14 00 14 00 28 00 38 00  |............(.8.|
00000040  60 00 38 00 4c 01 01 00  00 00 f0 01 00 00 08 00  |`.8.L...........|
00000050  15 00 00 00 00 00 00 00  68 91 08 00 00 00 00 00  |........h.......|
00000060  d1 b1 59 8b 7d 29 ca 01  29 63 6d 56 84 29 ca 01  |..Y.})..)cmV.)..|
00000070  29 63 6d 56 84 29 ca 01  d1 b1 59 8b 7d 29 ca 01  |)cmV.)....Y.})..|
00000080  00 80 39 00 00 00 00 00  a9 70 39 00 00 00 00 00  |..9......p9.....|
00000090  20 00 00 00 00 00 00 00  d1 b1 59 8b 7d 29 ca 01  | .........Y.})..|
000000a0  c9 01 6b 56 84 29 ca 01  c9 01 6b 56 84 29 ca 01  |..kV.)....kV.)..|
000000b0  d1 b1 59 8b 7d 29 ca 01  00 80 39 00 00 00 00 00  |..Y.})....9.....|
000000c0  d0 70 39 00 00 00 00 00  20 00 00 00 00 00 00 00  |.p9..... .......|
000000d0  1a 4b 28 27 00 00 00 00  01 4b 28 27 00 00 00 00  |.K('.....K('....|
000000e0  01 4b 28 27 00 00 00 00  98 00 00 00 00 00 00 00  |.K('............|
000000f0  01 00 00 00 68 00 00 00  00 00 00 00 00 00 00 00  |....h...........|
00000100  14 00 14 00 28 00 38 00  60 00 38 00 4c 01 01 00  |....(.8.`.8.L...|
00000110  00 00 18 05 00 00 08 00  15 00 00 00 00 00 00 00  |................|
00000120  68 91 08 00 00 00 00 00  d1 b1 59 8b 7d 29 ca 01  |h.........Y.})..|
00000130  29 63 6d 56 84 29 ca 01  29 63 6d 56 84 29 ca 01  |)cmV.)..)cmV.)..|
00000140  d1 b1 59 8b 7d 29 ca 01  00 80 39 00 00 00 00 00  |..Y.})....9.....|
00000150  a9 70 39 00 00 00 00 00  20 00 00 00 00 00 00 00  |.p9..... .......|
00000160  d1 b1 59 8b 7d 29 ca 01  c9 01 6b 56 84 29 ca 01  |..Y.})....kV.)..|
00000170  c9 01 6b 56 84 29 ca 01  d1 b1 59 8b 7d 29 ca 01  |..kV.)....Y.})..|
00000180  00 80 39 00 00 00 00 00  d0 70 39 00 00 00 00 00  |..9......p9.....|
00000190  20 00 00 00 00 00 00 00  33 4b 28 27 00 00 00 00  | .......3K('....|
000001a0  1a 4b 28 27 00 00 00 00  00 00 00 00 00 00 00 00  |.K('............|
000001b0  28 00 00 00 00 00 00 00  01 00 00 00 68 00 00 fe  |(...........h...|
000001c0  ff ff 07 fe ff ff 7b fc  34 0c 8b 77 49 14 00 00  |......{.4..wI...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 10 ed 00 12 76 00 00  00 00 00 00 02 00 00 00  |.....v..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3d 3a e0 14 4e  4f 20 4e 41 4d 45 20 20  |..)=:..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 48  ec 00 00 66 ba 00 00 00  |..E}.f.H...f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sda2: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by cariboo on 2011-03-24
According to fdisk and the boot info script, you don't have any linux partitions. What type of install did you do? Wubi-inside Windows, or a separate partition?

---

### Post by apoikola on 2011-03-25
I had a separate partition installed from Ubuntu 10.04 liveCD and later upgraded to 10.10. I find it confusing as well that the Linux partition seem to have disappeared?

```
sudo gparted
```

shows that on my 500 Gib harddrive there seem to be two rather big "unallocated" blocks 97.66 Gib and the other 58.87 Gib (screenshot in attachment).

Could it be that my linux used to be in the space that is now unallocated?

---

### Post by Dutch70 on 2011-03-25
> **apoikola said:**
> I had a separate partition installed from Ubuntu 10.04 liveCD and later upgraded to 10.10. I find it confusing as well that the Linux partition seem to have disappeared?

```
sudo gparted
```

shows that on my 500 Gib harddrive there seem to be two rather big "unallocated" blocks 97.66 Gib and the other 58.87 Gib (screenshot in attachment).

Could it be that my linux used to be in the space that is now unallocated?

It is likely that Ubuntu was installed on one of those partitions. You would need to create 2 partitions for Ubuntu & format them to ext4 to reinstall. One for Swap, equal to the size of your physical RAM, and however much space you want for "/" aka "root". You can also have a separate /home, but you need to figure out what you want to do with the unallocated space first. I can't see any logical way that Ubuntu would have used both of those partitions, considering their size.

---

### Post by Quackers on 2011-03-25
Does Windows still boot?
I ask because currently you have /boot/grub/core.img in sda1, sda2 and sda5. These are Grub2 files and should be removed.
Do you have a Windows repair disc or installation disc (not a set of recovery dvd's)?

---

### Post by apoikola on 2011-03-25
> **Quackers said:**
> Does Windows still boot?
I ask because currently you have /boot/grub/core.img in sda1, sda2 and sda5. These are Grub2 files and should be removed.
Do you have a Windows repair disc or installation disc (not a set of recovery dvd's)?


No windows doesn't boot (at least I don't know how to). All I get is the grub minimal bash. I can access to all my windows files from the Ubuntu LiveCD, but I can't access to my Ubuntu files because the partition is lost.

I have a laptop with no cd/dvd drive and no windows repair/installation disc.

The grub files here and there are probably result of my grub reinstallation trials. Is it ok to just delete the folders?

How is it possible that the whole Ubuntu installation just disappeared?

---

### Post by Quackers on 2011-03-25
I have no idea why the Ubuntu installation has disappeared. That is very strange! I am just asking somebody else for suggestions for your problem. Installing lilo may get Windows booting, but will confirm that shortly, I hope.
I would assume that Ubuntu will need to be installed again though.

---

### Post by oldfred on 2011-03-25
If you delete the extra grub files, installing lilo should get you booting windows again. If you want to recover anything from your old install you may want to try testdisk as it has a function to recover missing partitions.
You should not install grub to partitions.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

In sda1, your grub is in the same /boot folder as the BCD. Besure not to delete the BCD. 
In sda2 you have the /Boot & /boot case sensitive issue. Windows gets confused as it is not case sensitive. See link above.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

That may be all that is required to fix windows, but you should have one of these as long as you have windows.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Quackers on 2011-03-25
After seeking guidance (thanks drs305) I suggest the following.
Boot from the Ubuntu usb and select "try ubuntu" and when the desktop loads, connect to the internet.
Then open a terminal and run this
```
gksudo nautilus
```
Then go to the Places menu and see if the Windows partition (sda2) appears. If it does click on it. You should see it appear on the desktop as a HDD icon.
Double-click on it and a window should open with all your Windows files in it.
In the root there should be a folder named "boot". Open that folder and report waht is in it, please.
There may possible be a second folder called "boot" or "/boot", not sure, please report.

---

### Post by apoikola on 2011-03-26
Hi,

Thanks for all help so far, this Ubuntu community really is a community!

Quackers: Attached is a screenshot from my windows/boot/grub and  windows/Boot -folders ... interesting is that there in the grub -folder  should be some  grub.cfg -file, but there isn't.

Oldfred: I will try out your hints after my saturday-household-shopping-responsabilities are done.

---

### Post by apoikola on 2011-03-26
> **oldfred said:**
>  In sda1, your grub is in the same /boot folder as the BCD. Besure not to delete the BCD. 
In sda2 you have the /Boot & /boot case sensitive issue. Windows gets confused as it is not case sensitive.

Ok I renamed the /boot/grub folders on sda1, sda2 and sda5 to grub_deactivated

> **oldfred said:**
> 
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR


Did this---- last bits from my terminal

```
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
```

> **oldfred said:**
> 
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)


Thanks for the download links. As I don't have cd/dvd -drive, so I used my girlfriends Vista computer and created bootable Vista recovery USB following these instructions

[http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/](http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/)

Going to reboot now. If everything goes fine I'll post from recovered windows next time. Then I will reinstall Ubuntu. Let's see...

---

### Post by apoikola on 2011-03-26
Thanks Oldfred! With your advice Windows started normally and also the created Windows recovery usb-stick worked although I didn't need it (yet).

Now I'm trying to figure out what would be the best partitioning scheme for installing Ubuntu again. Could it be that the Ubuntu partition disappeared in the crash because it was not one of the primary partitions... it was logical partition?

Should I use gparted and create the partitions beforehand or trust the Ubuntu automatic intallation?

---

### Post by oldfred on 2011-03-26
Primary or logical should not make any difference. I always prefer to create partitions in advance with gparted. I sometimes use a gparted liveCD or the Ubuntu liveCD to create partitions. Then I use manual install to choose / (root), swap, & /home with formats.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Installs -----------------------
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

### Post by apoikola on 2011-03-27
Now after 4 days of struggle I am back to square one... functioning dualboot and ticking "time-bomb" in the Grub2 bootloadermenu.

Link to image from my bootloader menu: [https://picasaweb.google.com/lh/photo/5Sb6XTCAUBSQn_fV7Mf4xgGMoXmLwCSPDZFTQx1RaOo?feat=directlink](https://picasaweb.google.com/lh/photo/5Sb6XTCAUBSQn_fV7Mf4xgGMoXmLwCSPDZFTQx1RaOo?feat=directlink)
[IMG]https://picasaweb.google.com/lh/photo/5Sb6XTCAUBSQn_fV7Mf4xgGMoXmLwCSPDZFTQx1RaOo?feat=directlink[/IMG]
"Windows Vista" and "Windows Recovery Environment" seem to be labelled incorrectly (should be other way round?) in my Grub2 bootloader menu.

Additionally,  if one by accident chooses the option "Windows Vista (loader) (on  /dev/sda1) bad things will happend! This is what I made before starting this thread.

I assume that there is a way to edit the Grub-menu and take the "time-bomb" option away from there. This is my next thing to figure out.

---

### Post by Quackers on 2011-03-27
Choosing the sda1 entry should not cause a problem. If you choose it by accident just shutdown and start again. Alternatively allow it to start but then just reboot again.
It's easier of course to not choose it :-)
Yes, grub usually names Vista entries the wrong way round.
Just be careful :wink:

---

### Post by oldfred on 2011-03-27
I have only edited the grub menu manually, but that was before some of the new tools were available.

Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by apoikola on 2011-03-28
> **oldfred said:**
> 
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)


This one worked perfectly for me. Case solved and looking forward to the new Ubuntu soon :)

---

