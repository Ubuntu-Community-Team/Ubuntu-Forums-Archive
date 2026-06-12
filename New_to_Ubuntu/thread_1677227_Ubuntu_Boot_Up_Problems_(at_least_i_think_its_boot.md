---
title: "Ubuntu Boot Up Problems (at least i think its boot problems)"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Spyderkid on 2011-01-28
I did have Ubuntu on my computer and it worked fine but then all of a  sudden i switched it on once and the screen said "out of range" and  wouldn't boot up no matter what I did it wouldn't start. So I tried to  reinstall and it said lots of things about unknows user ID, 1/0 error,  can't find file..................., this does it on any CD, DVD i use  even the LXF DVD from the linux format magazine. So I had a OpenSUSE DVD  tried it worked fine isntalled great but i hate OpenSUSE its  complicated and doesn't have a good Software Centre like Ubuntu. But  still the problem remains about all these errors when i boot up the  DVD/CD of Ubuntu for version 10.04 and 10.10. 

Heres a boot analyser software thing this is the output:...


I have noticed that there is an unknown boot loader at the bottem of the   output. also there are other things please have a look and any   suggestions on what to do?

(I've highlighted somethings in red that i think are strange but there are bound to be other things aswell)

```

                Boot Info Script 0.55    dated February 15th, 2010                       

============================= Boot Info Summary:    ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1:    _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
[COLOR=Red]sda2:    _________________________________________________________________________

[/COLOR] [COLOR=Red]     File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  [/COLOR]
sda5:    _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda3:    _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3    and 
                       looks at sector 33852512 of the same hard drive    for 
                       the stage2 file. A stage2 file is at this    location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4:    _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info:    =============================

Drive: sda ___________________    _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     4,208,639     4,206,592  82 Linux swap    / Solaris
/dev/sda2         312,393,726   312,580,095       186,370   5 Extended
/dev/sda5         312,393,728   312,580,095       186,368  82 Linux swap    / Solaris
/dev/sda3    *      4,208,640    46,153,727    41,945,088  83 Linux
/dev/sda4          46,153,728   312,391,679   266,237,952  83 Linux


blkid -c /dev/null:    ____________________________________________________________

Device           UUID                                   TYPE       LABEL                            

/dev/sda1        59b43196-a970-4827-a56b-a04fa16da0ee   swap                                        
/dev/sda2: PTTYPE="dos" 
/dev/sda3        e497b058-760f-4759-a14a-d2befda5c459   ext4                                        
/dev/sda4        5d7d8ded-833c-4c44-865f-23ca7ec9d1c5   ext4                                        
/dev/sda5        b70815a5-7b03-496f-9244-cb0d9dde9224   swap                                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:    ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,acl,user_xattr)
/dev/sda4        /home                    ext4       (rw,acl,user_xattr)


=========================== sda3/boot/grub/menu.lst:    ===========================

# Modified by YaST2. Last modification on Wed Jan 26 20:26:16 GMT 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in    /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.3
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.34-12-default    root=/dev/disk/by-id/ata-ST3160215AS_5RA52Z1T-part3    resume=/dev/disk/by-id/ata-ST3160215AS_5RA52Z1T-part1 splash=silent    quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.34-12-default

###Don't change this comment - YaST2 identifier: Original name:    failsafe###
title Failsafe -- openSUSE 11.3
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.34-12-default    root=/dev/disk/by-id/ata-ST3160215AS_5RA52Z1T-part3 showopts apm=off    noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off    processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.34-12-default

=============================== sda3/etc/fstab:    ===============================

/dev/disk/by-id/ata-ST3160215AS_5RA52Z1T-part1 swap                 swap          defaults              0 0
/dev/disk/by-id/ata-ST3160215AS_5RA52Z1T-part5 swap                 swap          defaults              0 0
/dev/disk/by-id/ata-ST3160215AS_5RA52Z1T-part3 /                    ext4          acl,user_xattr        1 1
/dev/disk/by-id/ata-ST3160215AS_5RA52Z1T-part4 /home                ext4          acl,user_xattr        1 2
proc                 /proc                proc       defaults                 0 0
sysfs                /sys                 sysfs      noauto                   0 0
debugfs              /sys/kernel/debug    debugfs    noauto                   0 0
devpts               /dev/pts             devpts     mode=0620,gid=5          0 0

=================== sda3: Location of files loaded by Grub:    ===================


  17.5GB: boot/grub/menu.lst
  17.3GB: boot/grub/stage2
  17.6GB: boot/initrd
  17.6GB: boot/initrd-2.6.34-12-default
  17.3GB: boot/vmlinuz
  17.3GB: boot/vmlinuz-2.6.34-12-default
=========================== [COLOR=Red]Unknown MBRs/Boot Sectors/etc  [/COLOR]  =======================

[COLOR=Red]Unknown BootLoader  on sda2

00000000  de 19 c2 c2 6c 2b b1 84  d2 04 1c 30 c9 98 10 41     |....l+.....0...A|[/COLOR] [COLOR=Red]
00000010  01 28 2d 00 b2 50 93 50  20 0c 3a cd 00 cd 09 12  |.(-..P.P    .:.....|
00000020  88 99 0a b4 12 24 b0 83  06 34 c1 50 21 2c b9 2a     |.....$...4.P!,.*|
00000030  92 41 61 82 9d ca 44 43  a8 30 c0 8d 1d 91 2c 00     |.Aa...DC.0....,.|
00000040  35 62 30 c4 10 13 32 64  32 65 30 52 0a 48 90 02     |5b0...2d2e0R.H..|
00000050  60 90 59 a8 12 09 20 80  00 10 26 49 2a 92 92 4e  |`.Y...    ...&I*..N|
00000060  c4 40 9d 8d 00 00 b1 db  c1 e6 c7 11 3e 0c 7c 48     |.@..........>.|H|
00000070  df 63 3f b9 e7 04 de d2  61 77 09 90 fe eb ce 06     |.c?.....aw......|
00000080  eb 7f 4d 83 89 c7 34 1e  78 1d ea ca 65 d2 14 22     |..M...4.x...e.."|
00000090  ee 56 0f e2 1d 48 9d 15  12 84 dc fe 89 f5 c2 c8     |.V...H..........|
000000a0  0e 26 0e 89 d1 a5 84 e0  16 f5 a9 31 36 87 97 30     |.&.........16..0|
000000b0  48 62 7c 21 b5 94 53 11  a1 24 c5 d6 86 a0 64 bc     |Hb|!..S..$....d.|
000000c0  09 36 36 21 85 5a 20 61  51 3c 11 81 a6 da 69 09  |.66!.Z    aQ<....i.|
000000d0  2c 0c 6d d6 db 6d 8e 0c  0e 62 4a e7 b5 56 5f 13     |,.m..m...bJ..V_.|
000000e0  57 71 7c 4e d5 97 c4 d5  dc 5f 13 bf 35 f9 db 1d     |Wq|N....._..5...|
000000f0  46 7b 79 bb 75 18 0f cd  2d 3e 3e 68 8e 23 ac a9     |F{y.u...->>h.#..|
00000100  82 42 4d 29 32 99 41 a8  ec 51 54 20 c4 00 34 22  |.BM)2.A..QT    ..4"|
00000110  90 d4 69 29 d4 88 84 80  25 a1 81 35 48 14 b4 d5     |..i)....%..5H...|
00000120  50 41 64 00 09 30 d0 90  34 01 11 27 44 19 32 08     |PAd..0..4..'D.2.|
00000130  11 06 ab c1 cd f5 45 6c  6c 25 18 e8 3f 64 a1 8c     |......Ell%..?d..|
00000140  2a 53 d7 91 30 a8 fe e3  47 32 b2 c9 35 8e be e0     |*S..0...G2..5...|
00000150  69 a5 00 c6 86 c8 63 1b  1a 69 08 41 52 2e 7a d5     |i.....c..i.AR.z.|
00000160  4e 2e 5d cb d6 d5 38 b9  77 2f 5b ca 1d 2f c7 c5     |N.]...8.w/[../..|
00000170  5c 00 3f 80 92 92 92 62  50 52 0c 16 20 00 2a 50     |\.?....bPR.. .*P|
00000180  1a 53 51 88 c3 28 5a a0  3b 0f 90 61 09 e3 c0 78     |.SQ..(Z.;..a...x|
00000190  25 c0 65 f5 05 29 00 61  a4 d4 7b 8e 24 57 19 63     |%.e..).a..{.$W.c|
000001a0  2f b3 17 16 12 43 6d b8  07 de 85 9c 45 11 39 8e     |/....Cm.....E.9.|
000001b0  27 3d 97 73 3b 8b c8 89  f6 07 de 94 5a f6 00 fe     |'=.s;.......Z...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 02 00 00 00     |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00     |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa     |..............U.|
00000200


=============================== StdErr Messages:    ===============================[/COLOR]  [COLOR=Red]

[/COLOR] [COLOR=Red]   No volume groups found
mdadm: No arrays found in config file or automatically[/COLOR]


```

---

### Post by QLee on 2011-01-28
> **Spyderkid said:**
> I did have Ubuntu on my computer and it worked fine but then all of a  sudden i switched it on once and the screen said "out of range" and  wouldn't boot up no matter what I did it wouldn't start. So I tried to  reinstall and it said lots of things about unknows user ID, 1/0 error,  can't find file..................., this does it on any CD, DVD i use  even the LXF DVD from the linux format magazine. So I had a OpenSUSE DVD  tried it worked fine isntalled great but i hate OpenSUSE its  complicated and doesn't have a good Software Centre like Ubuntu. But  still the problem remains about all these errors when i boot up the  DVD/CD of Ubuntu for version 10.04 and 10.10. 

Heres a boot analyser software thing this is the output:...


I have noticed that there is an unknown boot loader at the bottem of the   output. also there are other things please have a look and any   suggestions on what to do?

(I've highlighted somethings in red that i think are strange but there are bound to be other things aswell)



This is the same problem that you posted in the General forum under the title Massive ubuntu problems, please don't cross-post, especially when you change titles.
[http://ubuntuforums.org/showthread.php?t=1676667](http://ubuntuforums.org/showthread.php?t=1676667)

---

### Post by howefield on 2011-01-28
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1676667](http://ubuntuforums.org/showthread.php?t=1676667)

---

