---
title: "Ubuntu dualboot problem"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by kaloasd on 2011-07-22
When I start the computer after the first screen it shows something in German :

```
Der Bootsektor dieser Diskette Wurde neu erstellt.
Benutzen Sie den DOS-Befehl SYS um diese Diskette bootfähig zu machen!
Bitte legen Sie nun eine Systemdiskette ins Laufwerk und drücken Sie eine Teste
```Google translation (probably not very good):

```
The boot sector of floppy disk was created.
 Use to make the DOS SYS command to the disk bootable!
 Now put a system disk into the drive and press a Test
```Then it something about not being able to find a bootable file and entering a bootable medium. The Windows antivirus might have done something to GRUB so do I reinstall it trough a bootable flash.
When i try to install GRUB trough the software center it says it has to remove some other grub.

---

### Post by oldfred on 2011-07-22
Some computer (BIOS) require a boot flag (active partition in windows) on a primary partition. Even though grub does not need a boot flag check that you have one.

Post this to see entire configuration:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by kaloasd on 2011-07-22
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........?.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1411176 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sda: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda has 0 
                       sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2107 MB, 2107637760 bytes
65 heads, 62 sectors/track, 1021 cylinders, total 4116480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     4,114,629     4,114,568   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       1cad40f1-adce-4fa3-bfb4-d5837030cea2   ext3       
/dev/sda                                                vfat       
/dev/sdb1        F0E2-ECB8                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda

00000000  eb 48 90 49 42 4d 20 41  56 34 30 00 02 01 01 00  |.H.IBM AV40.....|
00000010  02 e0 00 40 0b f0 09 00  12 00 02 00 00 00 00 00  |...@............|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  00 00 00 00 00 00 00 00  00 00 8c c8 8e d8 fa 8e  |................|
00000050  d0 bc fe ff fb be 77 7c  fc ac 0a c0 74 0b 56 b4  |......w|....t.V.|
00000060  0e bb 07 00 cd 10 5e eb  f0 32 e4 cd 16 b4 0f cd  |......^..2......|
00000070  10 32 e4 cd 10 cd 19 0d  0a 20 20 20 20 20 20 20  |.2.......       |
00000080  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
000000a0  20 20 20 20 0d 0a 0a 44  65 72 20 42 6f 6f 74 73  |    ...Der Boots|
000000b0  65 6b 74 6f 72 20 64 69  65 73 65 72 20 44 69 73  |ektor dieser Dis|
000000c0  6b 65 74 74 65 20 77 75  72 64 65 20 6e 65 75 20  |kette wurde neu |
000000d0  65 72 73 74 65 6c 6c 74  2e 20 20 20 20 20 20 20  |erstellt.       |
000000e0  20 0d 0a 42 65 6e 75 74  7a 65 6e 20 53 69 65 20  | ..Benutzen Sie |
000000f0  64 65 6e 20 44 4f 53 2d  42 65 66 65 68 6c 20 53  |den DOS-Befehl S|
00000100  59 53 20 75 6d 20 64 69  65 73 65 20 44 69 73 6b  |YS um diese Disk|
00000110  65 74 74 65 20 62 6f 6f  74 66 84 68 69 67 20 7a  |ette bootf.hig z|
00000120  75 20 6d 61 63 68 65 6e  21 0d 0a 42 69 74 74 65  |u machen!..Bitte|
00000130  20 6c 65 67 65 6e 20 53  69 65 20 6e 75 6e 20 65  | legen Sie nun e|
00000140  69 6e 65 20 53 79 73 74  65 6d 64 69 73 6b 65 74  |ine Systemdisket|
00000150  74 65 20 69 6e 73 20 4c  61 75 66 77 65 72 6b 20  |te ins Laufwerk |
00000160  75 6e 64 20 0d 0a 64 72  81 63 6b 65 6e 20 53 69  |und ..dr.cken Si|
00000170  65 20 65 69 6e 65 20 54  61 73 74 65 2e 00 00 00  |e eine Taste....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
hexdump: FD/sda/??~?;²?.ë?': Input/output error
hexdump: FD/sda/??~?;²?.ë?': Input/output error
hexdump: FD/sda/??~?;²?.ë?': Input/output error
hexdump: FD/sda/(?œ\èé.?: Input/output error
hexdump: FD/sda/(?œ\èé.?: Input/output error
hexdump: FD/sda/(?œ\èé.?: Input/output error
hexdump: FD/sda/?º0?[8n?.?uó: Input/output error
hexdump: FD/sda/?º0?[8n?.?uó: Input/output error
hexdump: FD/sda/?º0?[8n?.?uó: Input/output error
hexdump: FD/sda/*0?K=".?¡ô: Input/output error
hexdump: FD/sda/*0?K=".?¡ô: Input/output error
hexdump: FD/sda/*0?K=".?¡ô: Input/output error
hexdump: FD/sda/öùŒ???1=.?: Input/output error
hexdump: FD/sda/öùŒ???1=.?: Input/output error
hexdump: FD/sda/öùŒ???1=.?: Input/output error
hexdump: FD/sda/?é?º«??.1iŒ: Input/output error
hexdump: FD/sda/?é?º«??.1iŒ: Input/output error
hexdump: FD/sda/?é?º«??.1iŒ: Input/output error
hexdump: FD/sda/??????1.n,: Input/output error
hexdump: FD/sda/??????1.n,: Input/output error
hexdump: FD/sda/??????1.n,: Input/output error
hexdump: FD/sda/????°ß?.«2: Input/output error
hexdump: FD/sda/????°ß?.«2: Input/output error
hexdump: FD/sda/????°ß?.«2: Input/output error
hexdump: FD/sda/?ú??!÷..?2u: Input/output error
hexdump: FD/sda/?ú??!÷..?2u: Input/output error
hexdump: FD/sda/?ú??!÷..?2u: Input/output error
hexdump: FD/sda/?3???J.v?ö: Input/output error
hexdump: FD/sda/?3???J.v?ö: Input/output error
hexdump: FD/sda/?3???J.v?ö: Input/output error
hexdump: FD/sda/²5???>.?A: Input/output error
hexdump: FD/sda/²5???>.?A: Input/output error
hexdump: FD/sda/²5???>.?A: Input/output error
hexdump: FD/sda/?5s.*?: Input/output error
hexdump: FD/sda/?5s.*?: Input/output error
hexdump: FD/sda/?5s.*?: Input/output error
hexdump: FD/sda/?5¡VD]öò._: Input/output error
hexdump: FD/sda/?5¡VD]öò._: Input/output error
hexdump: FD/sda/?5¡VD]öò._: Input/output error
hexdump: FD/sda/âò7¡??b.^«:: Input/output error
hexdump: FD/sda/âò7¡??b.^«:: Input/output error
hexdump: FD/sda/âò7¡??b.^«:: Input/output error
hexdump: FD/sda/??à7ç[.CªY: Input/output error
hexdump: FD/sda/??à7ç[.CªY: Input/output error
hexdump: FD/sda/??à7ç[.CªY: Input/output error
hexdump: FD/sda/?7?u't·S.hì#: Input/output error
hexdump: FD/sda/?7?u't·S.hì#: Input/output error
hexdump: FD/sda/?7?u't·S.hì#: Input/output error
hexdump: FD/sda/œa??0???.?: Input/output error
hexdump: FD/sda/œa??0???.?: Input/output error
hexdump: FD/sda/œa??0???.?: Input/output error
hexdump: FD/sda/Caâ£N??.d?: Input/output error
hexdump: FD/sda/Caâ£N??.d?: Input/output error
hexdump: FD/sda/Caâ£N??.d?: Input/output error
hexdump: FD/sda/d?L Öå.?Ü?: Input/output error
hexdump: FD/sda/d?L Öå.?Ü?: Input/output error
hexdump: FD/sda/d?L Öå.?Ü?: Input/output error
hexdump: FD/sda/??Ea?pÖ.??J: Input/output error
hexdump: FD/sda/??Ea?pÖ.??J: Input/output error
hexdump: FD/sda/??Ea?pÖ.??J: Input/output error
hexdump: FD/sda/?]????e.ußà: Input/output error
hexdump: FD/sda/?]????e.ußà: Input/output error
hexdump: FD/sda/?]????e.ußà: Input/output error
hexdump: FD/sda/æóg'p2.fñ?: Input/output error
hexdump: FD/sda/æóg'p2.fñ?: Input/output error
hexdump: FD/sda/æóg'p2.fñ?: Input/output error
hexdump: FD/sda/gy??îf9.µ?â: Input/output error
hexdump: FD/sda/gy??îf9.µ?â: Input/output error
hexdump: FD/sda/gy??îf9.µ?â: Input/output error
hexdump: FD/sda/è?gZê?*.3v1: Input/output error
hexdump: FD/sda/è?gZê?*.3v1: Input/output error
hexdump: FD/sda/è?gZê?*.3v1: Input/output error
hexdump: FD/sda/?$H??6F.?Ní: Input/output error
hexdump: FD/sda/?$H??6F.?Ní: Input/output error
hexdump: FD/sda/?$H??6F.?Ní: Input/output error
hexdump: FD/sda/?iDºy?h.}h_: Input/output error
hexdump: FD/sda/?iDºy?h.}h_: Input/output error
hexdump: FD/sda/?iDºy?h.}h_: Input/output error
hexdump: FD/sda/k?c?'ß??.I?#: Input/output error
hexdump: FD/sda/k?c?'ß??.I?#: Input/output error
hexdump: FD/sda/k?c?'ß??.I?#: Input/output error
hexdump: FD/sda/`?$?K??.d$ù: Input/output error
hexdump: FD/sda/`?$?K??.d$ù: Input/output error
hexdump: FD/sda/`?$?K??.d$ù: Input/output error
hexdump: FD/sda/Lœ?]á5?.%r: Input/output error
hexdump: FD/sda/Lœ?]á5?.%r: Input/output error
hexdump: FD/sda/Lœ?]á5?.%r: Input/output error
hexdump: FD/sda/?ëímé???.???: Input/output error
hexdump: FD/sda/?ëímé???.???: Input/output error
hexdump: FD/sda/?ëímé???.???: Input/output error
hexdump: FD/sda/N?ñj5P5.: Input/output error
hexdump: FD/sda/N?ñj5P5.: Input/output error
hexdump: FD/sda/N?ñj5P5.: Input/output error
hexdump: FD/sda/o!Ç'???.2ö: Input/output error
hexdump: FD/sda/o!Ç'???.2ö: Input/output error
hexdump: FD/sda/o!Ç'???.2ö: Input/output error
hexdump: FD/sda/o?µ?ñ?,m.??Æ: Input/output error
hexdump: FD/sda/o?µ?ñ?,m.??Æ: Input/output error
hexdump: FD/sda/o?µ?ñ?,m.??Æ: Input/output error
hexdump: FD/sda/???O?v?.???: Input/output error
hexdump: FD/sda/???O?v?.???: Input/output error
hexdump: FD/sda/???O?v?.???: Input/output error
hexdump: FD/sda/?üp?b?.«}¿: Input/output error
hexdump: FD/sda/?üp?b?.«}¿: Input/output error
hexdump: FD/sda/?üp?b?.«}¿: Input/output error
hexdump: FD/sda/*p?U?.x&«: Input/output error
hexdump: FD/sda/*p?U?.x&«: Input/output error
hexdump: FD/sda/*p?U?.x&«: Input/output error
hexdump: FD/sda/qs?ìœá~?.???: Input/output error
hexdump: FD/sda/qs?ìœá~?.???: Input/output error
hexdump: FD/sda/qs?ìœá~?.???: Input/output error
hexdump: FD/sda/??óœú?r,.Å?: Input/output error
hexdump: FD/sda/??óœú?r,.Å?: Input/output error
hexdump: FD/sda/??óœú?r,.Å?: Input/output error
hexdump: FD/sda/Rçî}2?Vg.??': Input/output error
hexdump: FD/sda/Rçî}2?Vg.??': Input/output error
hexdump: FD/sda/Rçî}2?Vg.??': Input/output error
hexdump: FD/sda/?s5+`m^ö.:îç: Input/output error
hexdump: FD/sda/?s5+`m^ö.:îç: Input/output error
hexdump: FD/sda/?s5+`m^ö.:îç: Input/output error
hexdump: FD/sda/s8?vH?¢.?¥%: Input/output error
hexdump: FD/sda/s8?vH?¢.?¥%: Input/output error
hexdump: FD/sda/s8?vH?¢.?¥%: Input/output error
hexdump: FD/sda/s÷ró?].?mr: Input/output error
hexdump: FD/sda/s÷ró?].?mr: Input/output error
hexdump: FD/sda/s÷ró?].?mr: Input/output error
hexdump: FD/sda/SW?4²Ç_@.œ?: Input/output error
hexdump: FD/sda/SW?4²Ç_@.œ?: Input/output error
hexdump: FD/sda/SW?4²Ç_@.œ?: Input/output error
hexdump: FD/sda/âTfÅ?ß}Æ.y??: Input/output error
hexdump: FD/sda/âTfÅ?ß}Æ.y??: Input/output error
hexdump: FD/sda/âTfÅ?ß}Æ.y??: Input/output error
hexdump: FD/sda/?\? ?¬|?.?Å«: Input/output error
hexdump: FD/sda/?\? ?¬|?.?Å«: Input/output error
hexdump: FD/sda/?\? ?¬|?.?Å«: Input/output error
hexdump: FD/sda/°uMa¬3û.?²?: Input/output error
hexdump: FD/sda/°uMa¬3û.?²?: Input/output error
hexdump: FD/sda/°uMa¬3û.?²?: Input/output error
hexdump: FD/sda/uà?p!ï.?P8: Input/output error
hexdump: FD/sda/uà?p!ï.?P8: Input/output error
hexdump: FD/sda/uà?p!ï.?P8: Input/output error
hexdump: FD/sda/{ä??ux2.?: Input/output error
hexdump: FD/sda/{ä??ux2.?: Input/output error
hexdump: FD/sda/{ä??ux2.?: Input/output error
hexdump: FD/sda/"v???@è.5ùê: Input/output error
hexdump: FD/sda/"v???@è.5ùê: Input/output error
hexdump: FD/sda/"v???@è.5ùê: Input/output error
hexdump: FD/sda/|.xx«œ?.(??: Input/output error
hexdump: FD/sda/|.xx«œ?.(??: Input/output error
hexdump: FD/sda/|.xx«œ?.(??: Input/output error
hexdump: FD/sda/ym~???.k?: Input/output error
hexdump: FD/sda/ym~???.k?: Input/output error
hexdump: FD/sda/ym~???.k?: Input/output error
hexdump: FD/sda/????? .Z??: Input/output error
hexdump: FD/sda/????? .Z??: Input/output error
hexdump: FD/sda/????? .Z??: Input/output error
hexdump: FD/sda/zí?3æj?.?: Input/output error
hexdump: FD/sda/zí?3æj?.?: Input/output error
hexdump: FD/sda/zí?3æj?.?: Input/output error

```

---

### Post by kaloasd on 2011-07-22
I just found out that GRUB is not insatalled is that normal when booting from a LiveUSB

---

### Post by The Cyph3r on 2011-07-22
Booting from a live USB will send you straight to the OS on the USB, as long as the "USB floppy" or w/e it's called is set to the first position in the BIOS. You wont even get the option to use the GRUB

---

### Post by oldfred on 2011-07-22
Is the BIOS seeing the drive correctly.  I have not seen a drive appearing as a FD??

---

### Post by kaloasd on 2011-07-22
the problem is that it doesn't recognize ```
sudo grub
``` and when I just write grub it says I should install it

---

### Post by kaloasd on 2011-07-22
> **oldfred said:**
> Is the BIOS seeing the drive correctly.  I have not seen a drive appearing as a FD?? I don't know. How do I check

---

### Post by kaloasd on 2011-07-22
When I open the main hard drive on the label it says 165 GB Filesystem but in properties it says 1.3MB used and 130 KB free

---

### Post by oldfred on 2011-07-22
BIOS should how drives. Look at what drives it sees.

Your 130KB sounds like it is just a floppy drive. Did you reformat hard drive as floppy drive somehow?

If you use testdisk does it show anything?

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by kaloasd on 2011-07-23
Thanks for the help.


:)


I recovered the win partitions but I cant seem to get to the Linux one

Any ideas?

---

### Post by oldfred on 2011-07-23
If testdisk was not able to recover it and you have no important data that was not backed up, I would just reinstall. Usually you can install in under an hour.

If you have data you did not backup stop using drive and use photorec. But it is a long tedious process. ( I have used it and I now backup more often).

---

### Post by kaloasd on 2011-08-08
Thanks, I got all of my important files using testdisk and reinstalled. :)

---

