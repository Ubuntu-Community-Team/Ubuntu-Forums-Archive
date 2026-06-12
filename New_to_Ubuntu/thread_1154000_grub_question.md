---
title: "grub question"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by patchido on 2009-05-09
well i just need to know how to use the map command, because i cant make it work, do i have to run it in the terminal or place it in the menu.lst ?? im lost

---

### Post by swoody on 2009-05-09
It looks like you can use it in the command line, or as a menu entry:

[http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands](http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands)

Just scroll down and click on 'map' for more info about it :D

---

### Post by louieb on 2009-05-09
Map is a GRUB command and is placed in the windows entry of menu.lst when windows installed on a disk that is not 1st in the boot order. 

What it does is make windows think its on the 1st drive in the boot order. 

Example Windows is on the 2nd drive int boot order 

```

title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1


```

---

### Post by patchido on 2009-05-09
whats rootnoverify?

---

### Post by 73ckn797 on 2009-05-09
> **patchido said:**
> whats rootnoverify?

Simply means what it says. Do not verify the root file location. That allows windows to think it is first.

---

### Post by patchido on 2009-05-10
> **louieb said:**
> Map is a GRUB command and is placed in the windows entry of menu.lst when windows installed on a disk that is not 1st in the boot order. 

What it does is make windows think its on the 1st drive in the boot order. 

Example Windows is on the 2nd drive int boot order 

```

title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1


```

i did this, and it got me mbr missing so i changed rootnoverify for hd0.1 or something like that i dont remeber, and now grub wont start in my external, i get the command bash form something like that, and my internal HDD gets me some system testing, im in live cd and cant mount my ext drive!! i even tried with vista cd to fix internal and won work xD im in trouble if i dont fix this

---

### Post by patchido on 2009-05-10
plzz!!! help, dad is going to kill me, i dont know how this could have harmed my internal drive if grub is in the external




i need to fix this now, and i cant find anything that helps me

---

### Post by patchido on 2009-05-10
i have a proyect in my ubuntu partition i cant open, i have to turn it in now!!! plz someone help me

---

### Post by GMachine_24 on 2009-05-10
Hey Patchido:

So, you can't boot to either Windows or Ubuntu and they are both on the same internal hard drive? Or not . .  . ? How are things configured?

--GM

---

### Post by 73ckn797 on 2009-05-10
If you have the XP disk, boot into it and select recovery mode. Once there type "fixmbr" (without quotes) and it will make Windows on the internal drive boot. I do not use any external drives so I cannot help you there.

---

### Post by louieb on 2009-05-10
If 73ckn797 suggestion does not fix it. Going to need more information about your setup. Please follow the instructions in this post. [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")
and post back the results.txt file here.

---

### Post by patchido on 2009-05-10
ok, i have vista in my internal, and i am trying to fix boot with cd and it cant, and in my external where my rpoyect is i have the grub with ubuntu and xp, and when i modified the menu.lst i am unable to open any of the three partitions not even the internal and i dont know why, it has to do with the map command or rootnoverify

---

### Post by patchido on 2009-05-11
im really stressed, this is my final essay

---

### Post by patchido on 2009-05-11
> **louieb said:**
> If 73ckn797 suggestion does not fix it. Going to need more information about your setup. Please follow the instructions in this post. [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")
and post back the results.txt file here.
sudo bash ~/Desktop/boot_info_script*.sh

this tells me no directory exists or something like it

---

### Post by louieb on 2009-05-11
Did you download the script 1st?  Check the Firefox preferences to see where it downloads to. IF it doesn't download to the Desktop - copy the script to the Desktop and try again.

note: Linux is case sensitive - desktop is not the same as Desktop.

---

### Post by patchido on 2009-05-11
it stays forever like this ```
 Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
```

and only results in

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

```

---

### Post by Niniel on 2009-05-11
If you need to urgently access a file, use a live CD (if you have one)

---

### Post by patchido on 2009-05-11
LEFT IT FOR A LONG TIME

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 21971007 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65cc02ea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       176,714       176,652   6 FAT16
/dev/sda2             178,176    21,149,695    20,971,520   7 HPFS/NTFS
/dev/sda3          21,149,696   229,195,767   208,046,072   7 HPFS/NTFS
/dev/sda4         229,195,776   234,438,655     5,242,880   f W95 Ext d (LBA)
/dev/sda5         229,197,824   234,438,655     5,240,832  dd 


Drive: sdb ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       176,714       176,652   6 FAT16
/dev/sdb2             178,176    21,149,695    20,971,520   7 HPFS/NTFS
/dev/sdb3          21,149,696   229,195,767   208,046,072   7 HPFS/NTFS
/dev/sdb4         229,195,776   234,438,655     5,242,880   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sdb5     ?   229,195,776   229,195,775                   Unknown
/dev/sdb6     ?   229,195,776   229,195,775                   Unknown

/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb4 ends after the last sector of /dev/sdb
/dev/sdb5 ends after the last sector of /dev/sdb
the logical partition /dev/sdb5 is not contained in the extended partition /dev/sdb4
/dev/sdb6 ends after the last sector of /dev/sdb
the logical partition /dev/sdb6 is not contained in the extended partition /dev/sdb4

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0715" TYPE="vfat" 
/dev/sda2: UUID="4AB01EBEB01EB105" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="FCFE224AFE21FE10" LABEL="OS" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="B827-1424" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="c209b65b-ace7-430f-bda0-e9ee0ac2c2ef" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda3/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff


================================ sda5/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768


================================ sda5/BOOT.INI: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  6e 2f 70 2f 70 69 6c 6f  74 2d 6c 69 6e 6b 2f 70  |n/p/pilot-link/p|
00000010  79 74 68 6f 6e 2d 70 69  73 6f 63 6b 5f 30 2e 31  |ython-pisock_0.1|
00000020  32 2e 33 2d 34 75 62 75  6e 74 75 33 5f 69 33 38  |2.3-4ubuntu3_i38|
00000030  36 2e 64 65 62 0a 53 69  7a 65 3a 20 31 31 35 39  |6.deb.Size: 1159|
00000040  39 36 0a 4d 44 35 73 75  6d 3a 20 30 64 31 62 65  |96.MD5sum: 0d1be|
00000050  33 63 62 63 62 65 30 63  61 31 65 62 36 32 62 30  |3cbcbe0ca1eb62b0|
00000060  63 37 38 37 65 35 34 65  39 65 37 0a 53 48 41 31  |c787e54e9e7.SHA1|
00000070  3a 20 61 65 31 36 37 33  65 36 64 38 65 36 66 32  |: ae1673e6d8e6f2|
00000080  62 61 61 38 31 65 34 32  32 64 64 65 38 31 64 32  |baa81e422dde81d2|
00000090  33 36 39 61 32 64 63 63  61 39 0a 53 48 41 32 35  |369a2dcca9.SHA25|
000000a0  36 3a 20 63 33 32 65 37  38 30 39 34 63 33 33 33  |6: c32e78094c333|
000000b0  37 32 64 35 37 39 65 63  32 36 34 35 64 65 35 39  |72d579ec2645de59|
000000c0  32 65 62 39 65 61 39 66  33 31 33 64 61 64 62 64  |2eb9ea9f313dadbd|
000000d0  62 38 64 39 64 33 32 36  61 35 30 65 38 63 31 39  |b8d9d326a50e8c19|
000000e0  61 39 62 0a 44 65 73 63  72 69 70 74 69 6f 6e 3a  |a9b.Description:|
000000f0  20 50 79 74 68 6f 6e 20  6d 6f 64 75 6c 65 20 74  | Python module t|
00000100  6f 20 63 6f 6d 6d 75 6e  69 63 61 74 65 20 77 69  |o communicate wi|
00000110  74 68 20 50 61 6c 6d 4f  53 20 50 44 41 0a 20 54  |th PalmOS PDA. T|
00000120  68 69 73 20 70 61 63 6b  61 67 65 20 70 72 6f 76  |his package prov|
00000130  69 64 65 73 20 74 68 65  20 70 69 73 6f 63 6b 20  |ides the pisock |
00000140  6d 6f 64 75 6c 65 2c 20  77 68 69 63 68 20 70 72  |module, which pr|
00000150  6f 76 69 64 65 73 20 50  79 74 68 6f 6e 20 70 72  |ovides Python pr|
00000160  6f 67 72 61 6d 73 0a 20  77 69 74 68 20 6d 65 61  |ograms. with mea|
00000170  6e 73 20 6f 66 20 63 6f  6d 6d 75 6e 69 63 61 74  |ns of communicat|
00000180  69 6e 67 20 64 69 72 65  63 74 6c 79 20 77 69 74  |ing directly wit|
00000190  68 20 61 20 50 61 6c 6d  4f 53 20 64 65 76 69 63  |h a PalmOS devic|
000001a0  65 2e 0a 48 6f 6d 65 70  61 67 65 3a 20 68 74 74  |e..Homepage: htt|
000001b0  70 3a 2f 2f 77 77 77 2e  70 69 6c 6f 74 2d 6c 69  |p://www.pilot-li|
000001c0  6e 6b 2e 6f 72 67 2f 0a  50 79 74 68 6f 6e 2d 56  |nk.org/.Python-V|
000001d0  65 72 73 69 6f 6e 3a 20  32 2e 34 2c 20 32 2e 35  |ersion: 2.4, 2.5|
000001e0  0a 42 75 67 73 3a 20 6d  61 69 6c 74 6f 3a 75 62  |.Bugs: mailto:ub|
000001f0  75 6e 74 75 2d 75 73 65  72 73 40 6c 69 73 74 73  |untu-users@lists|
00000200

Unknown BootLoader  on sdb3

00000000  5f 3f bb eb 1f ca ff fb  b2 40 a7 00 04 32 3e 56  |_?.......@...2>V|
00000010  eb 0f 42 e8 a7 e7 da ea  63 2f 5d 4f bc bb 57 a7  |..B.....c/]O..W.|
00000020  bd 2b 62 8b 1f ab a9 8c  3d 74 36 63 99 46 59 13  |.+b.....=t6c.FY.|
00000030  de 30 99 95 e5 82 06 95  bc 44 59 22 e4 69 03 e1  |.0.......DY".i..|
00000040  c6 62 b8 b2 00 bb 28 e0  21 55 8a 65 58 c9 5b 96  |.b....(.!U.eX.[.|
00000050  7f e6 63 62 ad 65 46 f1  a8 c9 a9 f9 5e 7a 4c a1  |..cb.eF.....^zL.|
00000060  62 a2 22 41 4c 89 44 49  d6 52 e3 ec fc 8c c3 10  |b."AL.DI.R......|
00000070  48 c5 68 51 f8 b9 b1 41  ca a0 cc de bf 3c 9f ff  |H.hQ...A.....<..|
00000080  ff ff ff ff ff ff ff ff  65 5a ed 25 24 96 66 b4  |........eZ.%$.f.|
00000090  ce 00 51 5a 09 fc a9 f0  43 bd 22 a2 56 b7 cd 90  |..QZ....C.".V...|
000000a0  24 9b a6 ae a6 5d a7 6e  5f 16 8d 25 53 3b 75 94  |$....].n_..%S;u.|
000000b0  c9 01 e4 94 30 46 e1 97  cb 19 13 ce 00 80 21 08  |....0F........!.|
000000c0  ab 51 69 32 28 09 b1 b7  38 69 54 c3 b1 95 ea 4c  |.Qi2(...8iT....L|
000000d0  ad 50 12 38 85 fd e0 f9  5d 9d 0a e3 84 fd 71 8c  |.P.8....].....q.|
000000e0  c2 de dc cb ba c6 6f 38  19 a4 52 b7 38 65 52 d7  |......o8..R.8eR.|
000000f0  47 75 9d 9a 0e df 78 3a  d6 7e 35 6f 16 db bd 71  |Gu....x:.~5o...q|
00000100  5f ef 8c 6f 74 df ce b5  8f 9b de f2 78 8c 08 39  |_..ot.......x..9|
00000110  c4 40 74 ab 75 41 24 35  ae 5e f4 32 f6 2b 96 29  |.@t.uA$5.^.2.+.)|
00000120  e5 bf ff ff ff ff ff ff  ff ff fc 00 26 36 dc 8d  |............&6..|
00000130  a7 2d b2 4e 40 d0 88 b1  0a f0 03 2f c9 fc 90 35  |.-.N@....../...5|
00000140  9b 72 c9 d4 19 31 27 46  3d 60 50 64 e8 b3 59 9a  |.r...1'F=`Pd..Y.|
00000150  a7 4e 05 9c a1 26 2b 6a  da d0 a6 65 88 da 22 f2  |.N...&+j...e..".|
00000160  12 f5 a5 e3 a0 e8 e3 08  0d 1a 9e c2 e3 0d 1f 44  |...............D|
00000170  fd 23 79 12 a4 2c 6a f4  da 36 dd 5e 3c ce ec 75  |.#y..,j..6.^<..u|
00000180  c0 b8 32 23 18 50 44 30  fd c4 87 38 50 27 36 45  |..2#.PD0...8P'6E|
00000190  71 85 67 7a 6b 42 ca 53  7a e2 a5 6e 70 b1 61 33  |q.gzkB.Sz..np.a3|
000001a0  c8 db 62 be 55 1f ff ff  ff ff ff ff e8 8a b3 92  |..b.U...........|
000001b0  5c 92 4a 54 68 11 65 f4  b6 c3 10 7e d2 98 35 62  |\.JTh.e....~..5b|
000001c0  d4 c2 da 64 f2 e8 b6 9c  16 d7 a4 65 90 2c 4a 14  |...d.......e.,J.|
000001d0  88 9e 7c 48 00 88 41 82  01 11 83 68 e6 5d c1 42  |..|H..A....h.].B|
000001e0  1a 55 f2 ab 52 d9 76 ce  b1 e9 c5 f4 f5 39 6f eb  |.U..R.v......9o.|
000001f0  32 51 09 f2 18 d4 54 73  15 43 2b 22 e1 3c 65 2c  |2Q....Ts.C+".<e,|
00000200

Unknown BootLoader  on sdb4


Unknown BootLoader  on sdb5


Unknown BootLoader  on sdb6



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb6: No such file or directory
hexdump: /dev/sdb6: No such file or directory
```

---

### Post by louieb on 2009-05-12
Not going to be of much help here. Did notice something. The partition table on sdb ( the external drive I'm guessing) is not right. The end of sda5 and sda6 is before the start. Thats probably why the Linux partition is unreadable.

```
/dev/sdb4         229,195,776   234,438,655     5,242,880   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sdb5     ?   [COLOR=Red]229,195,776   229,195,775 [/COLOR]                  Unknown
/dev/sdb6     ?   [COLOR=Red]229,195,776   229,195,775 [/COLOR]                  Unknown
```

These are probably the Linux install partition and swap partition, just a guess. 
There is a program **testdisk** that in some cases can fix a broken partition table. Its available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page").

---

### Post by patchido on 2009-05-12
im doomed >S what about my vista?

---

### Post by zeex on 2009-05-12
> **patchido said:**
> im doomed >S what about my vista?

hi, 

Have you tried booting from live CD, mounting the drive containing your project and making a backup? It'll take more time to resolve your grub issues than to extract your project from the drive. Try this if you already haven't tried it.

---

### Post by patchido on 2009-05-12
> **zeex said:**
> hi, 

Have you tried booting from live CD, mounting the drive containing your project and making a backup? It'll take more time to resolve your grub issues than to extract your project from the drive. Try this if you already haven't tried it.
 i have, and it says the drive of 60 gibs is of 9.8 mb and wont nount it, im not that noob ;)

---

### Post by patchido on 2009-05-12
here's a screenshot

---

### Post by louieb on 2009-05-12
> **patchido said:**
> im doomed >S what about my vista?
What OS(s) do you have on the internal drive? Looks like theres more that one copy of some type of  MS windows. 

Unplug the external drive and see what happens when it boots.  Describe what it does and what messages are displayed. Please be as accurate as possible.

---

### Post by patchido on 2009-05-12
> **louieb said:**
> What OS(s) do you have on the internal drive? Looks like theres more that one copy of some type of  MS windows. 

Unplug the external drive and see what happens when it boots.  Describe what it does and what messages are displayed. Please be as accurate as possible.

ive done this,. i have vista in my INT and I get some utility from DELL cause the laptop is dell, i get 3 options, system check, disk check and exit, ive tried everything inside of it and wont work. form the livecd i can see everything inside, ive tried to fix it with my vista cd and cant

---

### Post by Don1500 on 2009-05-12
Patchido, are you still alive???:confused:

Anyway. The best I can think of is to unplug your ext drive and work on just getting vista to work. Use your VISTA live cd to boot and then use FIXMBR to get your boor record correct. this should get you up and running. I would then only hook up the EXT drive when you want Ubuntu, at least until you figure out how you want to set the system up. (P.S> Get to work earning some cash and get your own unit.):wink:

---

### Post by GMachine_24 on 2009-05-14
I imagine you've either solved your problem or maybe given up by now. But if not, I've found the live version of "Puppy Linux" mounts all hard drives/partitions to the desktop when it boots up - even ones I could not get to mount using other Linux versions.

[http://www.puppylinux.com/](http://www.puppylinux.com/)

Then you can look at the hard drive and see if the information you want is there.

Hope this helps.

---

### Post by Don1500 on 2009-05-16
Ya, Puppy works anywhere, I have it on a 256 meg pen drive.

---

### Post by patchido on 2009-05-18
i tried to run puppy and i got this 
```
Kernel panic - not syncing: VPS Unable to mount root fs on unknown-block(8,17)
```

---

