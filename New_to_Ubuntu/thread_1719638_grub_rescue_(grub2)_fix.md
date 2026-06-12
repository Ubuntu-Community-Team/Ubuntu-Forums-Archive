---
title: "grub rescue (grub2) fix"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Rambokill on 2011-04-02
I used testdisk to write a new table and now when I boot my pc it will show me this "grub rescue>".The other time I got this I found some commands in this forum and when I wrote them in the terminal using ubuntu live cd and restarted the problem was fixed.Note:I still have ubuntu live cd and I am running grub2 so don't give me the commands of grub.

---

### Post by Rubi1200 on 2011-04-02
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Rambokill on 2011-04-02
I didnt get what you meant but here it is are the results:
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              12,663     4,209,029     4,196,367   5 Extended
/dev/sda5              12,678     4,209,029     4,196,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2016 MB, 2016411648 bytes
128 heads, 32 sectors/track, 961 cylinders, total 3938304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             61     3,936,255     3,936,195   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda5        9E520B0B520AE83B                       ntfs       WINRE                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1                                               vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/WINRE             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 01 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 f1 00  20 00 80 00 3d 00 00 00  |........ ...=...|
00000020  c3 0f 3c 00 00 00 29 00  00 00 00 20 20 20 20 20  |..<...)....     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 00 00  |      FAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 fa fc 31 c9 8e d1  |............1...|
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
00000100  7d 00 66 b8 c3 00 16 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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


```

---

### Post by Rambokill on 2011-04-02
Eh now what do I do?

---

### Post by Rubi1200 on 2011-04-02
The boot info script can be used to help diagnose booting/installation issues.

The results suggest that partitions 2-4 are no longer there. You have an extended partition with Windows in it, but not all the boot files that Windows needs.

What led you to use Testdisk to do this? 

Do you have backups?

Where was Ubuntu installed?

GRUB is installed in the MBR of sda, but, again, it is pointing to sda5 which is being reported as a Windows partition (probably boot partition).

I am not sure what function you used in Testdisk, but you may want to consider using the Deeper Search function to try and recover what was there:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Rambokill on 2011-04-02
I wanted to extend my windows 7 partition so I unmounted it but it was showing that the partition was damaged and unknown .So I used testdisk to recover that partition.I dont have any backups.Ubuntu was installed in another partition I made from the free space partition.

---

### Post by Rubi1200 on 2011-04-02
The best advice I can offer right now is that you wait and be patient.

I will ask some other users to take a look and offer advice on the best way to proceed forward.

This is a tricky situation and I suspect you may have lost your actual Windows install.

---

### Post by Rambokill on 2011-04-02
Before I proceeded with testdisk I downloaded a pirated windows 7 hp 64 bit version if that is of any use in the near future.I ve also tried to grow the windows 7 partition with gparted but I cancelled.I think that might have caused some trouble.

---

### Post by coffeecat on 2011-04-02
Hi Rambokill, a couple of comments.

Most important: You have admitted that your copy of Windows is pirated. The code of  conduct of this forum does not allow members to give advice on illegal  activity. You will not get any advice directly related to getting that copy of Windows running again.

As far as Ubuntu is concerned, running testdisk again might help to restore the Ubuntu partitions, but testdisk itself can produce partition table irregularities in these circumstances which themselves need fixes from other utilities. In the circumstances, so long as you don't have lost data, a complete wipe and reinstall of Ubuntu might be quicker and easier for you. We can help you with that. We cannot help you with a pirated version of Windows.

---

### Post by Rambokill on 2011-04-02
No my windows 7 copy(The first one was legal).It was already installed and I just had to enter some information and that was it.It was installed.It didnt came with a live cd of windows 7.That's why I downloaded the pirated version just to be safe if anything would have happened.Also how I am gonna run testdisk if it doesnt even let me install it.

---

### Post by Rambokill on 2011-04-02
I reinstalled ubuntu and when I got to choose what partition I should be using two partitions were present .The first one was about 2 gb and the othe was 317 gb free space.Does this mean that all of my files were deleted?Also if I put a live cd of windows 7 and reinstall them will thety be back like the one before?

---

### Post by Rambokill on 2011-04-02
I ve borrowed a friend's windows 7 live cd (I dont know which version but it has blue color as background so I think is home premium as mine).When I boot my pc it takes me to a menu which says install or repair.I chose repair but it doesnt find any operating systems to fix.There is a load drivers option but I dont know how to use it.

---

