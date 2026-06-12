---
title: "Partitions."
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Trentality on 2011-01-13
So! I set aside this netbook just to learn the basic's of ubuntu and poke around the gui. There's a bit of a problem, It wont install! Right now im in the Try before install mode, My entire harddrive is erased. 

The problem is, Whenever i attempt to install Ubuntu Netbook, Ubuntu 10.10, or Xubuntu i come across this. 
"Formatting swap space in partition #5 of SCI1 (0,0,0) (sdb)"  And it will hang here for hours. Giving me a real headache. Ive tried manually partitioning, unless theres something im missing, still doesnt work. 

I do really apologise if this has been answered before, or if my termonology is way off. But any help would be GREATLY appreiciated! :confused:

---

### Post by Quackers on 2011-01-13
Welcome to UF.
How has the drive been erased? By accident, or by design? How do you know it has? You said that you have tried manual partitioning, was that from inside the installer?
Has the hard drive ever been used in a raid array? Has it been used (or formatted) using a Mac computer?

---

### Post by Trentality on 2011-01-13
Thanks for the reply! Well, I installed ubuntu netbook once before on here, and selected to Format and install ubuntu. It worked absolutely perfect until i forgot my password, I tried everything but decided to format/reinstall.  If i boot up without the USB, the screen is forever black. Im assuming its erased. And yes, I partitioned from inside the installer.

I havnt done anything with a mac.:confused:

---

### Post by Quackers on 2011-01-13
Ok, thanks. So now you are on the live cd desktop, yes?
Please go to System > Admin > gparted and open that. After a few seconds it will scan your hard drive for partition details. If it shows anything, please post a screenshot of that window.

---

### Post by Trentality on 2011-01-14
[http://img502.imageshack.us/img502/1439/screenshotam.png](http://img502.imageshack.us/img502/1439/screenshotam.png)

[http://img502.imageshack.us/i/screenshotam.png/](http://img502.imageshack.us/i/screenshotam.png/)


Here you go!
[IMG]http://http://img502.imageshack.us/i/screenshotam.png/[/IMG]

---

### Post by Trentality on 2011-01-14
[http://img585.imageshack.us/img585/3323/screenshotmm.png](http://img585.imageshack.us/img585/3323/screenshotmm.png)

And here's the screen it hangs at.

---

### Post by Quackers on 2011-01-14
Your hard drive is not even appearing in gparted. 
From the live cd desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Trentality on 2011-01-14
```
 is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2021 MB, 2021654016 bytes
64 heads, 63 sectors/track, 979 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *            129     3,907,007     3,906,879   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   306,440,191   306,438,144  83 Linux
/dev/sdb2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sdb5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1615-2257                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        666153e4-7f04-40b8-b2fd-13f610b6d542   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        dd381e40-b1ca-49c8-b295-9b15bdabdfaf   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 81 00 00 00  |........?.......|
00000020  3f 9d 3b 00 e0 0e 00 00  00 00 00 00 02 00 00 00  |?.;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 57 22 15 16 4e  4f 20 4e 41 4d 45 20 20  |..)W"..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 e8 1d 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script055.sh: line 892: 14612 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error
```

---

### Post by Quackers on 2011-01-14
You missed the top bit of the boot script output off :-) It doesn't matter for the moment though.
Your main Ubuntu partition is not mounting. I don't know why that may be.
Try going to System > Admin > Disk Utility and see if that picks any partitions up.

---

