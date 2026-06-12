---
title: "Dual Booting MBR issues"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by Daktyl198 on 2011-08-31
I have a bit of a problem. . . 

I'm new to Ubuntu and linux in general. I bought this laptop a couple years ago and it came with Windows Vista Home Premium. I first installed Ubuntu 10.10, then later upgraded to 11.04 when it came out.

I didn't like having an experiment as an OS when I'm new to linux so I decided to go to 10.04 as it was the LTS so I was guessing it was the most stable. In the process I also learned I have a 64-bit processor and have been running 32-bit Vista and Ubuntu.
As I uninstalled 11.04 I decided to merge the now empty partition with another partition that was left over from a recovery when I first got my computer. After I did that, I used a program to change the MBR so that Ubuntu wouldn't be an option any longer (I didn't think it through).

Somehow, by removing the option of booting from /dev/sda3 (named Ubuntu) I somehow corrupted my MBR so now instead of booting directly to windows from the MBR, it gives me an option named Ubuntu that supposedly leads to Vista, but is corrupt. Luckily I was able to install 64-bit 10.04 and grub is now first in the booting process, but I need vista for several reasons.

I need to know a way to restore the MBR leading to Vista, without a Vista CD and preferably from Ubuntu.

Specs:
Acer Aspire 6930
Intel Core 2 Duo 2.00 CPU T5800 @ 2.00GHz
3GB DDR2 RAM
Intel Mobile 4 Series Chipset Integrated Graphics Controller Graphics card

---

### Post by oldfred on 2011-08-31
You can make some repairs from Ubuntu, but you can only run chkdsk and some major repairs from a windows repairCD.

Lets see what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Once you get into Vista make a repair CD.
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.

---

### Post by Daktyl198 on 2011-09-01
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     20,973,568   323,055,615   302,082,048   7 NTFS / exFAT / HPFS
/dev/sda3         323,067,150   625,137,344   302,070,195  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7C3821F93821B2D6                       ntfs       PQSERVICE
/dev/sda3        413cc81d-99c0-449d-80aa-a0360184c192   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=413cc81d-99c0-449d-80aa-a0360184c192 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=413cc81d-99c0-449d-80aa-a0360184c192 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=413cc81d-99c0-449d-80aa-a0360184c192 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=413cc81d-99c0-449d-80aa-a0360184c192 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 413cc81d-99c0-449d-80aa-a0360184c192
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7C3821F93821B2D6
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 584ADE4F4ADE2A10
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=413cc81d-99c0-449d-80aa-a0360184c192 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 164.221613884 = 176.331615232  boot/grub/core.img                             1
 268.195090294 = 287.972285440  boot/grub/grub.cfg                             2
 164.214468956 = 176.323943424  boot/initrd.img-2.6.32-33-generic              1
 164.308218956 = 176.424606720  boot/initrd.img-2.6.32-34-generic              1
 166.098067284 = 178.346441728  boot/vmlinuz-2.6.32-33-generic                 1
 164.218245506 = 176.327998464  boot/vmlinuz-2.6.32-34-generic                 1
 164.308218956 = 176.424606720  initrd.img                                     1
 164.214468956 = 176.323943424  initrd.img.old                                 1
 164.218245506 = 176.327998464  vmlinuz                                        1
 166.098067284 = 178.346441728  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  4d 47 52 20 69 73 20 63  |.....,DcMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


```There is the results. /dev/sda1 is atually a recovery partition, not vista itself. /sda2 is vista, and as you can see, it doesn't even recognize it. I don't want to recover because I would loose all of my files, which I know are fine because I can access them via Ubuntu.
EDIT: I cannot access my Vista files anymore. I could access them from the LiveUSB, and I think I could access them when I first installed 10.04

---

### Post by oldfred on 2011-09-01
The partition boot sector of all NTFS partition have to have a NTFS signature and refer to the system booting and partition info similar to the partition table. That is what the boot script is not seeing.

If you had a windows repair Cd fixboot would be the command. 

From Linux you can find the backup boot sector and see if it is still vaild. Testdisk can recover the backup. If backup is not valid, testdisk can mak a new boot sector, but I am not sure if it is 100% bootable or still needs a fixboot.

This discusses having grub in the PBR, but you have similar issue in the PBR is damaged.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Daktyl198 on 2011-09-01
```
                                  TestDisk 6.11, Data Recovery Utility, April 2009  
 Christophe GRENIER <grenier@cgsecurity.org>  
 http://www.cgsecurity.org  
 

 Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63  
      Partition                  Start        End    Size in sectors  
  2 * HPFS - NTFS           1305 138 50 20109  71 58  302082048  
 

 filesystem size           302082048  
 sectors_per_cluster       8  
 mft_lcn                   786432  
 mftmirr_lcn               2647975  
 clusters_per_mft_record   -10  
 clusters_per_index_record 1  
 Extrapolated boot sector and current boot sector are identical.
 
```This is the output from the testdisk. When I tried booting into windows, It still wouldn't work. It keeps saying a file called (I think) ntfs_linux.(something) is missing or corrupt.

---

### Post by oldfred on 2011-09-01
This is the screen I get and under dump you can compare old and new. Should have .R.NTFS at beginning and 055aa  at end.

---

### Post by Daktyl198 on 2011-09-01
```
Boot sector                        Backup boot sector
0000 eb52904e 54465320   .R.NTFS   eb52904e 54465320   .R.NTFS

```Is the code at the beginning.

```
01F8 809db2ca 000055aa   ......U.  809db2ca 000055aa   ......U.

```Is the code at the end. Is that what you meant?

---

### Post by oldfred on 2011-09-02
It now looks like it has the proper NTFS signature, but sometimes it need chkdsk which can only be run from a windows repair CD. Sometimes you can get to the Windows internal repair by pressing f8 as you boot windows. With grub it can be tricky as it is very quick and you may have to try several times. So click on windows in grub and press f8 as quick as you can.

Can you see your windows files from Ubuntu?

---

### Post by Daktyl198 on 2011-09-02
Yeah, I couldn't earlier, but I restarted to test Vista after running testdisk and now I can see them again.

---

### Post by Daktyl198 on 2011-09-02
Ok, well my friend said he would loan me an external hard-drive to back up my files on to so I can just restore Vista. Now my new questions are:

If I restore Vista while Ubuntu is installed will it
A) remove Ubuntu as Vista originally controlled both partitions?
B) remove grub as the first bootloader or remove it all together
?

---

### Post by YesWeCan on 2011-09-02
If you have fixed the Vista boot sector by restoring it using testdisk it might boot.
In Ubuntu, first try to readd Vista to the Grub menu:
sudo update-grub
You should see Vista listed towards the end.

---

### Post by Daktyl198 on 2011-09-02
Well the problem isn't that Grub doesn't show it, it is that after selecting Vista in grub the MBR stops me from booting. I somehow corrupted the MBR on accident and I don't have a recovery disk. I do have a restore disk I made a while ago. I want to use that but not if it messes with Ubuntu or Grub.

Hence my earlier "new" questions.

---

### Post by YesWeCan on 2011-09-02
Things have changed since you ran testdisk. So Grub needs updating. Try this.

If you do  Vista recovery the standard MBR code will be restored and only Vista will boot. So you'll need a live CD to reinstall the special Grub MBR code. This is easy to do.

---

### Post by Daktyl198 on 2011-09-02
But besides Vista booting first, nothing on the Ubuntu Partition will change right?

---

