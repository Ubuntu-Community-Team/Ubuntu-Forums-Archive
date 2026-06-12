---
title: "Installing Ubuntu on HP 4 Partition Machines"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by miradus on 2011-04-10
Hi everyone,

I'm new to these forums and I'm trying to figure out how to load Ubuntu onto an HP Netbook Mini 5102. I have some knowledge of what i'm doing but here's the dilemma..

I have 4 pre-loaded partitions on this HP machine, and I could just wipe the drive and put Ubuntu on there no problem, but I'd like to keep the recovery partition and Windows 7 installed in addition. The 4 partitions are as follows:

Windows 7 loader part 300mb - ntfs
Windows 7 141gb -ntfs
Hp recovery 16gb -ntfs
HP TOOLS 2gb - fat32

Since I'm limited to 4 partitions per disk, I wanted to format the HP tools (HP quickweb and such) 2gb one and throw Ubuntu on it. The real problem is 2gb is just not enough for the install. 

What on earth do I do?  :p

---

### Post by Jerry N on 2011-04-10
> **miradus said:**
> Hi everyone,

I'm new to these forums and I'm trying to figure out how to load Ubuntu onto an HP Netbook Mini 5102. I have some knowledge of what i'm doing but here's the dilemma..

I have 4 pre-loaded partitions on this HP machine, and I could just wipe the drive and put Ubuntu on there no problem, but I'd like to keep the recovery partition and Windows 7 installed in addition. The 4 partitions are as follows:

Windows 7 loader part 300mb - ntfs
Windows 7 141gb -ntfs
Hp recovery 16gb -ntfs
HP TOOLS 2gb - fat32

Since I'm limited to 4 partitions per disk, I wanted to format the HP tools (HP quickweb and such) 2gb one and throw Ubuntu on it. The real problem is 2gb is just not enough for the install. 

What on earth do I do?  :p

You could eliminate the HP Tools partition.  I am not sure of the downside of this action and haven't had the nerve to try it on my Mini 210 yet.

After cutting out one partition, use the Win 7 tools to reduce the size of the 141gb NTFS partition, maybe to 80gb.  Then us9ng gparted create an extended partition in the 60 or so gb of unallocated space just created.  Now using gparted, create logical partitions in the extended partition to install Ubuntu.

Jerry

---

### Post by TeoBigusGeekus on 2011-04-10
> **miradus said:**
> I wanted to format the HP tools (HP quickweb and such) 2gb one and throw Ubuntu on it. p

Do this and "steal" some space from the other ntfs partitions in order to give a bit more room to your ubuntu partition.
But do all this from windows 7 (disk management) and not with gparted, to avoid damaging windows.

---

### Post by miradus on 2011-04-10
> **TeoBigusGeekus said:**
> Do this and "steal" some space from the other ntfs partitions in order to give a bit more room to your ubuntu partition.
But do all this from windows 7 (disk management) and not with gparted, to avoid damaging windows.

So when I goto install I should be able to format the entire amount of unallocated space within the installation of ubuntu? Or should i format the unallocated space to fat32 or w/e in windows?

Lastly, do I need to worry about a SWAP partition i've been reading about?

---

### Post by miradus on 2011-04-10
> **Jerry N said:**
> You could eliminate the HP Tools partition.  I am not sure of the downside of this action and haven't had the nerve to try it on my Mini 210 yet.

After cutting out one partition, use the Win 7 tools to reduce the size of the 141gb NTFS partition, maybe to 80gb.  Then us9ng gparted create an extended partition in the 60 or so gb of unallocated space just created.  Now using gparted, create logical partitions in the extended partition to install Ubuntu.

Jerry

If i'm using Gparted, i can create more than 4 partitions? But they need to be logical? Havn't quite grasped this one yet. :)

---

### Post by TeoBigusGeekus on 2011-04-10
The ubuntu installer will take care of the formatting - I'd suggest ext4 format for your ubuntu partitions.

IMO, you should create a swap partition, if you want to suspend or hibernate your netbook.

One more thing; during installation, when you reach the partitioner, choose manual partitioning:
1)Create one partition of ~1-2gb for swap
2)Another one of ~10-15gb for root (mount point:/, format:ext4)
3)A third one (the rest of your space) for your home folder (mount point:/home, format:ext4).

All the above of course mean that you should first create an extended partition.

---

### Post by miradus on 2011-04-10
> **TeoBigusGeekus said:**
> The ubuntu installer will take care of the formatting - I'd suggest ext4 format for your ubuntu partitions.

IMO, you should create a swap partition, if you want to suspend or hibernate your netbook.

One more thing; during installation, when you reach the partitioner, choose manual partitioning:
1)Create one partition of ~1-2gb for swap
2)Another one of ~10-15gb for root (mount point:/, format:ext4)
3)A third one (the rest of your space) for your home folder (mount point:/home, format:ext4).

All the above of course mean that you should first create an extended partition.

Ok so doing an extended partition with the whole of the remainder of disk space will allow me to not worry about the 4 partition rule then? Ill give this a shot

---

### Post by Hedgehog1 on 2011-04-10
Another option is to create 2 sets of the recovery DVDs, and sacrifice the 16 gig **Hp recovery 16gb -ntfs** partition instead:


When all four primary partitions are taken (the HP install)

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create your sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-04-10
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

### Post by Miljet on 2011-04-10
> Ok so doing an extended partition with the whole of the remainder of disk space will allow me to not worry about the 4 partition rule then?

The 4 partition rule is always in effect. But one of those 4 primary partitions can be an extended partition. And the extended partition can contain multiple partitions, which are called logical partitions. In other words, an extended partition is just a container for logical partitions.

---

### Post by TeoBigusGeekus on 2011-04-10
@Hedgehog
Now that's what I call a tutorial...

---

### Post by Hedgehog1 on 2011-04-10
> **TeoBigusGeekus said:**
> @Hedgehog
Now that's what I call a tutorial...

***Thank You*** TeoBigusGeekus!  That means a lot coming from an experienced forum member like yourself :D


***The Hedge***

:KS

---

### Post by TeoBigusGeekus on 2011-04-10
> **Hedgehog1 said:**
> ***Thank You*** TeoBigusGeekus!  That means a lot coming from an experienced forum member like yourself :D


***The Hedge***

:KS

I'm definitely experienced... in blunders :lolflag:

Keep up the good work; the forums need people like you!!!

---

### Post by miradus on 2011-04-10
> **Hedgehog1 said:**
> ***Thank You*** TeoBigusGeekus!  That means a lot coming from an experienced forum member like yourself :D


***The Hedge***

:KS

Thank you for the tutorial, very very very helpful. Installation seems to have gone well, the only issue im having is now it only boots to windows 7 after the installation. Could the boot log not have copied for some reason? Or did i mess something up   ;)

---

### Post by JKyleOKC on 2011-04-10
> **miradus said:**
> If i'm using Gparted, i can create more than 4 partitions? But they need to be logical? Havn't quite grasped this one yet.The area of the disk where the partition table is stored only has room for four entries. That's what limits the number of partitions that can be stored there. To do away with the bottleneck, the "extended partition" was invented. It's a container rather than a true partition, and defines another area of the disk that can hold many more partition entries. These are called "logical" partitions because while they are partitions, they are not in the primary table.

To make room for the extended entry, one of the existing partitions must be eliminated, and HP Tools is the obvious choice. However it's not large enough in itself, so space must be stolen from the other partitions as well, and then partitions must be moved around to bring all of the unallocated space together as one large area. Then you can define that area as an extended partition, and move ahead.

All of this should be done from Win7 with its tools. Once the extended partition exists, you can let the Ubuntu installer do the definition of its partitions within that space. It does not have to be formatted first.

EDIT: Not meant to upstage Hedge's excellent tutorial! We were typing at the same time...

---

### Post by Quackers on 2011-04-10
Nice tutorial Mr Hedge :-)

miradus,
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by miradus on 2011-04-10
incoming code post

```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2004 MB, 2004353024 bytes
16 heads, 32 sectors/track, 7646 cylinders, total 3914752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     3,914,751     3,914,720   e W95 FAT16 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       616,447       614,400   7 HPFS/NTFS
/dev/sdb2             616,448   174,524,415   173,907,968   7 HPFS/NTFS
/dev/sdb3         276,924,416   308,381,695    31,457,280   7 HPFS/NTFS
/dev/sdb4         174,530,221   276,912,404   102,382,184   5 Extended
/dev/sdb5         174,530,223   178,626,734     4,096,512  82 Linux swap / Solaris
/dev/sdb6         178,626,798   209,343,014    30,716,217  83 Linux
/dev/sdb7         209,343,078   276,912,404    67,569,327  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4BD6-FF41                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        20AC504EAC502098                       ntfs       SYSTEM                        
/dev/sdb2        78C652C1C6527F76                       ntfs                                     
/dev/sdb3        2E083010082FD59D                       ntfs       HP_RECOVERY                   
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        2be20baa-8666-4df5-996e-e6c97f2b9030   swap       swap                          
/dev/sdb6        ff051eb5-a113-4c0d-b5a5-d6f3121210fc   ext4                                     
/dev/sdb7        c0a76f8a-300f-442f-89e9-4005abb8b51d   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set ff051eb5-a113-4c0d-b5a5-d6f3121210fc
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set ff051eb5-a113-4c0d-b5a5-d6f3121210fc
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set ff051eb5-a113-4c0d-b5a5-d6f3121210fc
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ff051eb5-a113-4c0d-b5a5-d6f3121210fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set ff051eb5-a113-4c0d-b5a5-d6f3121210fc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ff051eb5-a113-4c0d-b5a5-d6f3121210fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set ff051eb5-a113-4c0d-b5a5-d6f3121210fc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set ff051eb5-a113-4c0d-b5a5-d6f3121210fc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 2e083010082fd59d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=ff051eb5-a113-4c0d-b5a5-d6f3121210fc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=c0a76f8a-300f-442f-89e9-4005abb8b51d /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=2be20baa-8666-4df5-996e-e6c97f2b9030 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  95.9GB: boot/grub/core.img
  93.9GB: boot/grub/grub.cfg
  95.9GB: boot/initrd.img-2.6.32-21-generic
  95.9GB: boot/vmlinuz-2.6.32-21-generic
  95.9GB: initrd.img
  95.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  74 6f 72 3e 0a 20 20 20  20 20 20 20 20 20 20 3c  |tor>.          <|
00000010  63 63 3a 41 67 65 6e 74  3e 0a 20 20 20 20 20 20  |cc:Agent>.      |
00000020  20 20 20 20 20 20 3c 64  63 3a 74 69 74 6c 65 3e  |      <dc:title>|
00000030  46 72 61 6e 6b 20 53 6f  6c 65 6e 73 6b 79 3c 2f  |Frank Solensky</|
00000040  64 63 3a 74 69 74 6c 65  3e 0a 20 20 20 20 20 20  |dc:title>.      |
00000050  20 20 20 20 3c 2f 63 63  3a 41 67 65 6e 74 3e 0a  |    </cc:Agent>.|
00000060  20 20 20 20 20 20 20 20  3c 2f 64 63 3a 63 72 65  |        </dc:cre|
00000070  61 74 6f 72 3e 0a 20 20  20 20 20 20 20 20 3c 64  |ator>.        <d|
00000080  63 3a 73 75 62 6a 65 63  74 3e 0a 20 20 20 20 20  |c:subject>.     |
00000090  20 20 20 20 20 3c 72 64  66 3a 42 61 67 3e 0a 20  |     <rdf:Bag>. |
000000a0  20 20 20 20 20 20 20 20  20 20 20 3c 72 64 66 3a  |           <rdf:|
000000b0  6c 69 3e 77 65 61 74 68  65 72 3c 2f 72 64 66 3a  |li>weather</rdf:|
000000c0  6c 69 3e 0a 20 20 20 20  20 20 20 20 20 20 20 20  |li>.            |
000000d0  3c 72 64 66 3a 6c 69 3e  66 65 77 2d 63 6c 6f 75  |<rdf:li>few-clou|
000000e0  64 73 3c 2f 72 64 66 3a  6c 69 3e 0a 20 20 20 20  |ds</rdf:li>.    |
000000f0  20 20 20 20 20 20 20 20  3c 72 64 66 3a 6c 69 3e  |        <rdf:li>|
00000100  6e 69 67 68 74 3c 2f 72  64 66 3a 6c 69 3e 0a 20  |night</rdf:li>. |
00000110  20 20 20 20 20 20 20 20  20 20 20 3c 72 64 66 3a  |           <rdf:|
00000120  6c 69 3e 6d 6f 6f 6e 3c  2f 72 64 66 3a 6c 69 3e  |li>moon</rdf:li>|
00000130  0a 20 20 20 20 20 20 20  20 20 20 20 20 3c 72 64  |.            <rd|
00000140  66 3a 6c 69 3e 32 33 30  3c 2f 72 64 66 3a 6c 69  |f:li>230</rdf:li|
00000150  3e 0a 20 20 20 20 20 20  20 20 20 20 3c 2f 72 64  |>.          </rd|
00000160  66 3a 42 61 67 3e 0a 20  20 20 20 20 20 20 20 3c  |f:Bag>.        <|
00000170  2f 64 63 3a 73 75 62 6a  65 63 74 3e 0a 20 20 20  |/dc:subject>.   |
00000180  20 20 20 3c 2f 63 63 3a  57 6f 72 6b 3e 0a 20 20  |   </cc:Work>.  |
00000190  20 20 20 20 3c 63 63 3a  4c 69 63 65 6e 73 65 0a  |    <cc:License.|
000001a0  20 20 20 20 20 20 20 20  20 72 64 66 3a 61 62 6f  |         rdf:abo|
000001b0  75 74 3d 22 68 74 74 70  3a 2f 2f 63 72 65 00 fe  |ut="http://cre..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 82 3e 00 00 fe  |............>...|
000001d0  ff ff 05 fe ff ff 02 82  3e 00 78 b1 d4 01 00 00  |........>.x.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-04-10
It appears that grub has not installed.
I take it that the 2GB flash drive is your Ubuntu live usb?
In that case, from the live desktop please open up a terminal and copy/paste the following commands into it, one line at a time and pressing enter after each line.
```
sudo mount /dev/sdb6 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
This should report that no errors were made.
If it does, please reboot, taking out the flash drive.
Ubuntu should now boot directly (no grub menu).
That's ok. If it does, please open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to see if the Windows Loader is recognised. If it is, reboot and see if Windows boots from the new grub menu.

---

### Post by miradus on 2011-04-10
> **Quackers said:**
> It appears that grub has not installed.
I take it that the 2GB flash drive is your Ubuntu live usb?
In that case, from the live desktop please open up a terminal and copy/paste the following commands into it, one line at a time and pressing enter after each line.
```
sudo mount /dev/sdb6 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```This should report that no errors were made.
If it does, please reboot, taking out the flash drive.
Ubuntu should now boot directly (no grub menu).
That's ok. If it does, please open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to see if the Windows Loader is recognised. If it is, reboot and see if Windows boots from the new grub menu.

Thank you so much, trying right now!

---

### Post by Quackers on 2011-04-10
Have fun :-)

---

### Post by srs5694 on 2011-04-11
> **JKyleOKC said:**
> To make room for the extended entry, one of the existing partitions must be eliminated, and HP Tools is the obvious choice. However it's not large enough in itself, so space must be stolen from the other partitions as well, and then partitions must be moved around to bring all of the unallocated space together as one large area. Then you can define that area as an extended partition, and move ahead.

All of this should be done from Win7 with its tools.

I advise extreme caution about this last point. Under certain circumstances, Windows permits creations of more than four "primary" partitions; but when it does so, it converts *all* of the partitions from "basic" partitions to "dynamic" partitions. Unfortunately, "dynamic" partitions are a Windows-only concept, similar to Linux's Logical Volume Manager (LVM). If Windows converts from "basic" to "dynamic" format, you'll have dug yourself into a much deeper hole than you're in with four primary partitions. I've seen several posts on this forum from people who've unknowingly done precisely this, so it's a real danger.

It's fairly safe to delete basic partitions in Windows, and resizing the boot partition is most safely done from Windows because Windows tends to be very fussy about it's boot partition. I recommend *not* creating any new partitions in the Windows partitioning tool, though; leave that to the Linux installer, or use a Linux emergency disc and GParted, fdisk, or some other tool.

---

