---
title: "Grub rescue"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by MathMcC on 2010-05-31
On my primary drive I have windows 7 installed. I installed Ubuntu on a secondary driver. Then, just as a test, I installed ubuntu again on a partition primary drive to see whether it was a bit snappier. It wasn't so (and this was a major error I'm sure) I deleted that partition from windows 7.

I assumed that when I rebooted GRUB simply wouldn't show that ubuntu install as an option. However immediately I'm taken to the grub-rescue prompt and told that no such partition exists.

I need to revise for imminent computing(! - how embarassing) exams so if anyone can help that'd be fab. I've googled around but I'm not sure which situation applies to me. Should I simply boot from my win 7 cd and do a repair?

---

### Post by camporter1 on 2010-05-31
I believe grub is looking for your grub folder in the partion you just deleted. You can try changing the grub configuration to the correct hard drive, or you can try reinstalling grub using the ubuntu install disc.

---

### Post by MathMcC on 2010-05-31
> **camporter1 said:**
> You can try changing the grub configuration to the correct hard drive

How might I go about this from grub-rescue cmd prompt?

---

### Post by camporter1 on 2010-05-31
To repair grub (assuming grub2), try [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by drs305 on 2010-05-31
Your Grub files may still be on the original partition so using the instructions for booting from the command line and pointing to the old install may work for you. 

The Rescue section is contained in the same link posted by *camporter1*.

If you can boot from the rescue prompt you should reinstall/reconfigure Grub2. If you can't, reinstalling from the LiveCD should work.

---

### Post by MathMcC on 2010-05-31
> **camporter1 said:**
> To repair grub (assuming grub2), try [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

thanks - trying to figure which is the ubuntu installation i didnt delete. it will be ext4 format, right?

---

### Post by drs305 on 2010-05-31
> **MathMcC said:**
> thanks - trying to figure which is the ubuntu installation i didnt delete. it will be ext4 format, right?

If you are at the grub prompt (and not the livecd) you can explore your partitions with these commands:

```
ls  # This command will show your drives and partitions. 
```

```
ls (hd0,5)/boot/grub   
```
# This would show the files located in /boot/grub of sda5. Try the different partitions until you find the one with lots of *.mod files in /boot/grub.

If you aren't having immediate success, it would probably be easier to reinstall Grub2 from the LiveCd. Of course, you will still have to find the correct partition, but you should be more comfortable exploring your drives from the Desktop.

---

### Post by MathMcC on 2010-05-31
I tried booting from the second hdd. And it takes me straight to the grub> command line...

---

### Post by MathMcC on 2010-05-31
> **drs305 said:**
> If you are at the grub prompt (and not the livecd) you can explore your partitions with these commands:

```
ls  # This command will show your drives and partitions. 
``````
ls (hd0,5)/boot/grub   
```# This would show the files located in /boot/grub of sda5. Try the different partitions until you find the one with lots of *.mod files in /boot/grub.

If you aren't having immediate success, it would probably be easier to reinstall Grub2 from the LiveCd. Of course, you will still have to find the correct partition, but you should be more comfortable exploring your drives from the Desktop.

Ok. I'm posting from the live cd now. Here is what I get if I put "sudo fdisk -l" in the terminal:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9151    73503321+  83  Linux
/dev/sdb2           18237       18844     4883760   83  Linux
/dev/sdb3           18845       18966      979965   82  Linux swap / Solaris
/dev/sdb4            9151       18236    72976385    5  Extended
/dev/sdb5            9151       17860    69956608   83  Linux
/dev/sdb6           17861       18236     3018752   82  Linux swap / Solaris

```Surely its sdbl1 that has the ubuntu install because its the only bootable one. (By the way just to confuse things I know there is an attempted arch-linux install on here (i.e. I made the partitions for it but didnt manage to install. This was before I installed ubuntu so perhaps ubuntu is sdb4 or sdb5 - which I'll try now). 

I tried ```
sudo mount /dev/sdb1 /mnt
``` and ```
sudo grub-install --root-directory=/mnt/ -/dev/sdb
``` but it just took me back to grub-rescue and ```
sudo update-grub
``` made no difference.

But I'll try the above commands with sdb4.

---

### Post by MathMcC on 2010-05-31
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ -/dev/sdb
Unrecognized option `-/dev/sdb'
```

Here's a problem.

---

### Post by MathMcC on 2010-05-31
> **drs305 said:**
> If you are at the grub prompt (and not the livecd) you can explore your partitions with these commands:

```
ls  # This command will show your drives and partitions. 
``````
ls (hd0,5)/boot/grub   
```# This would show the files located in /boot/grub of sda5. Try the different partitions until you find the one with lots of *.mod files in /boot/grub.


Well I tried this approach and the only two partitions with lots of mod files in were hdd(0,1) and hdd(0,5) -- sda1 and sda5, which are both on the primary drive. Which I can't fathom.

I'm not terribly clear on how to boot from the grub command prompt so I'm going to try installing grub to one of these from the live cd.

EDIT: Argh! sda1 is of course my windows install - an ntfs formatted drive, so how on earth has it got the mod files on it. And using fdisk -l from the terminal shows that sda5 doesnt exist!!! I think somethings mixed up in the naming of these partitions.

---

### Post by Sethalos on 2010-05-31
> **MathMcC said:**
> On my primary drive I have windows 7 installed. I installed Ubuntu on a secondary driver. Then, just as a test, I installed ubuntu again on a partition primary drive to see whether it was a bit snappier. It wasn't so (and this was a major error I'm sure) I deleted that partition from windows 7.

I assumed that when I rebooted GRUB simply wouldn't show that ubuntu install as an option. However immediately I'm taken to the grub-rescue prompt and told that no such partition exists.

I need to revise for imminent computing(! - how embarassing) exams so if anyone can help that'd be fab. I've googled around but I'm not sure which situation applies to me. Should I simply boot from my win 7 cd and do a repair?

I'm pretty much suffering from the same thing, only I installed on a USB drive, however now I can't boot directly into Win 7 without the USB.  I get that same grub error.

---

### Post by MathMcC on 2010-05-31
OK the only drive that has a vmlinuz file in the boot folder is hd(0,5) and yet if I try ```
**linux /boot/vmlinuz root=/dev/sda5  ro**
```
I get a file not found error.

---

### Post by drs305 on 2010-05-31
Try it this way:

Added:
> 
set prefix=(hd0,5)/boot/grub
linux /vmlinuz root=/dev/sda5  ro
Same with the initrd line, without the '/boot'

---

### Post by MathMcC on 2010-05-31
> **drs305 said:**
> Try it this way:

Same with the initrd line, without the '/boot'

nope - no joy.

---

### Post by drs305 on 2010-05-31
It's time to reinstall Grub2 from the LiveCD.

And while you are there, posting the information provided by this bootinfo script should help us get things working:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by MathMcC on 2010-05-31
> **drs305 said:**
> It's time to reinstall Grub2 from the LiveCD.

And while you are there, posting the information provided by this bootinfo script should help us get things working:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I eventually managed to boot from sda5. Wasn't getting the error regarding vlinuz etc. I hit boot - It seemed to be doing something and then came up with an error that sda5 did not exist. Is that theoretically possible?

Still unsure as to where I should attempt to install grub from within the livecd...

---

### Post by MathMcC on 2010-05-31
> **drs305 said:**
> It's time to reinstall Grub2 from the LiveCD.

And while you are there, posting the information provided by this bootinfo script should help us get things working:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   671,068,527   671,068,465   7 HPFS/NTFS
/dev/sda2         671,070,206   978,993,151   307,922,946   5 Extended
Empty Partition
/dev/sda3         978,993,152 1,798,193,151   819,200,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   147,006,705   147,006,643  83 Linux
/dev/sdb2         292,961,340   302,728,859     9,767,520  83 Linux
/dev/sdb3         302,728,860   304,688,789     1,959,930  82 Linux swap / Solaris
/dev/sdb4         147,007,486   292,960,255   145,952,770   5 Extended
/dev/sdb5         147,007,488   286,920,703   139,913,216  83 Linux
/dev/sdb6         286,922,752   292,960,255     6,037,504  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5EFCFF2CFCFEFD59                       ntfs       Operating System              
/dev/sda2: PTTYPE="dos" 
/dev/sda3        7AC8B9DAC8B994BB                       ntfs       Music and Films               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3a905120-2785-4581-869f-28b94d9224c7   ext3                                     
/dev/sdb2        f0dd16c3-e96e-4542-8015-c97a8c0a892a   ext3                                     
/dev/sdb3        6ad0a5b1-4cc6-4676-942a-e4dbf5e622ed   swap                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        db3e6888-0efe-4605-a992-39d952178e4b   ext4                                     
/dev/sdb6        25566bd1-6665-4da1-81ec-c8d0975c4012   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sdb1/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sdb1 / ext3 defaults 0 1
/dev/sdb2 /boot ext3 defaults 0 1
/dev/sdb3 swap swap defaults 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  47.1GB: boot/grub/core.img

============================= sdb2/grub/menu.lst: =============================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd1,1)
kernel /vmlinuz26 root=/dev/sdb1 ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd1,1)
kernel /vmlinuz26 root=/dev/sdb1 ro
initrd /kernel26-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

=================== sdb2: Location of files loaded by Grub: ===================


 154.4GB: grub/menu.lst
 154.3GB: grub/stage2
 150.0GB: vmlinuz26

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set db3e6888-0efe-4605-a992-39d952178e4b
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set db3e6888-0efe-4605-a992-39d952178e4b
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set db3e6888-0efe-4605-a992-39d952178e4b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=db3e6888-0efe-4605-a992-39d952178e4b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set db3e6888-0efe-4605-a992-39d952178e4b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=db3e6888-0efe-4605-a992-39d952178e4b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set db3e6888-0efe-4605-a992-39d952178e4b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set db3e6888-0efe-4605-a992-39d952178e4b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5efcff2cfcfefd59
    chainloader +1
}
menuentry "Arch Linux (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set f0dd16c3-e96e-4542-8015-c97a8c0a892a
    linux /vmlinuz26 root=/dev/sdb1 ro
    initrd /kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set f0dd16c3-e96e-4542-8015-c97a8c0a892a
    linux /vmlinuz26 root=/dev/sdb1 ro
    initrd /kernel26-fallback.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=db3e6888-0efe-4605-a992-39d952178e4b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=25566bd1-6665-4da1-81ec-c8d0975c4012 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 131.2GB: boot/grub/core.img
 103.3GB: boot/grub/grub.cfg
 131.3GB: boot/initrd.img-2.6.32-21-generic
 131.2GB: boot/vmlinuz-2.6.32-21-generic
 131.3GB: initrd.img
 131.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on sda2

00000000  61 2a 94 34 65 b6 08 0a  93 97 34 d3 43 f4 f8 25  |a*.4e.....4.C..%|
00000010  b2 36 4a ce 30 0a 6f 2b  0f 41 80 87 bf ff 78 3c  |.6J.0.o+.A....x<|
00000020  01 41 61 58 91 ad 6a 9c  30 0b d0 61 e0 3c 07 f0  |.AaX..j.0..a.<..|
00000030  e0 f0 10 39 83 09 6d 69  78 33 40 c5 e0 78 7a 06  |...9..mix3@..xz.|
00000040  99 cc d4 8c b2 0c 20 0e  fc af e1 d7 81 8b 04 b0  |...... .........|
00000050  34 9c 3d 05 47 82 f8 6c  18 0f 83 c1 7f 8e 5e 08  |4.=.G..l......^.|
00000060  00 ab 50 3d 4c 10 18 00  dd 48 20 7c 3c 1d 2b 2f  |..P=L....H |<.+/|
00000070  f8 fb df 2d 2c 2c f8 31  5f 83 a0 60 49 37 54 35  |...-,,.1_..`I7T5|
00000080  9a 20 e6 86 c1 61 59 bb  ba 0a c0 26 16 b6 aa b0  |. ...aY....&....|
00000090  34 10 0b b5 bd 63 31 4e  ee 88 0c 67 bc 5b ff 87  |4....c1N...g.[..|
000000a0  bf f8 14 0e c1 89 c6 02  40 07 b0 9d 4a 74 da c2  |........@...Jt..|
000000b0  56 14 eb 0c 88 1b e5 65  85 9f 0f 55 7c b0 0a f8  |V......e...U|...|
000000c0  0a f8 18 12 92 1f 8f c1  81 56 d2 66 c3 86 14 82  |.........V.f....|
000000d0  a0 5a 3e 56 0c 10 99 1e  83 0f 47 85 ec 0f 81 8b  |.Z>V......G.....|
000000e0  00 f3 00 f0 5f f2 e8 f4  0e 02 08 8e 10 04 75 61  |...._.........ua|
000000f0  07 df 06 1b 2b 12 8b 8b  07 c3 f1 f2 7f 03 07 7f  |....+...........|
00000100  4e d3 6d 85 ec 39 64 af  18 d5 18 66 0e 33 54 6e  |N.m..9d....f.3Tn|
00000110  e2 9d c0 b5 b1 76 36 3e  56 54 c2 75 0a 46 d9 a1  |.....v6>VT.u.F..|
00000120  e0 30 c3 e2 d0 ce 0f 01  fb 48 3c 07 f1 e0 70 1e  |.0.......H<...p.|
00000130  02 07 90 42 1e b6 10 53  89 49 40 fb 23 e6 41 c0  |...B...S.I@.#.A.|
00000140  80 0a 04 ba 0c b8 07 fc  3a 2c 2c f1 6f fc 3e 02  |........:,,.o.>.|
00000150  3f 03 0d 03 1a 6c 18 f8  c8 1e 03 f7 70 78 0f d5  |?....l......px..|
00000160  c4 60 78 08 1f d4 88 4c  6b 00 a5 04 34 e3 ed 06  |.`x....Lk...4...|
00000170  1c 0f 12 33 e5 60 ca 0b  c3 df 7f e0 1a 58 1e 26  |...3.`.......X.&|
00000180  f7 bf ff 01 a4 de 07 82  ff a5 28 e1 b1 c8 31 e0  |..........(...1.|
00000190  6a b4 90 19 90 60 43 11  f0 18 7a 0c 07 44 bd 10  |j....`C...z..D..|
000001a0  c6 c9 04 04 a5 b8 af c5  c5 a1 e1 72 a5 5e f7 81  |...........r.^..|
000001b0  54 3e f7 fe 1e 05 c4 2a  54 39 cc d5 1b 81 00 00  |T>.....*T9......|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb4

00000000  6b c6 af 5c bd 7e e2 32  9b 61 6d a9 35 f5 ec 65  |k..\.~.2.am.5..e|
00000010  ad 72 6e 99 2d d1 65 b6  55 47 fb bf 5c 59 16 ce  |.rn.-.e.UG..\Y..|
00000020  cd 05 8f b9 3d 5f 68 5f  a7 2e b2 b9 66 cc b1 56  |....=_h_....f..V|
00000030  74 5a a1 6d 10 2b 6c 36  b7 39 d6 d1 a7 cb b5 2f  |tZ.m.+l6.9...../|
00000040  bc ca 6c 7f b4 29 0d 6f  9c 0b dd 73 ef cf b7 79  |..l..).o...s...y|
00000050  8e 9c 63 3d 7c 7f 81 76  9d 6f b9 ed e1 bc 39 d6  |..c=|..v.o....9.|
00000060  10 59 1f ed a9 33 73 6c  ce d6 39 d6 dd 5f 06 d7  |.Y...3sl..9.._..|
00000070  2f bd 36 d7 56 56 35 c7  3a c3 d2 b7 fe f2 82 a5  |/.6.VV5.:.......|
00000080  36 c5 bd d9 d6 98 15 3d  eb 87 3d a9 b0 bd 39 b5  |6......=..=...9.|
00000090  d6 3a 9c f2 dc 32 60 91  6d c2 dd 55 d6 05 f4 2c  |.:...2`.m..U...,|
000000a0  97 61 4b 6c 49 21 eb ac  c0 f9 80 64 c6 81 f9 b6  |.aKlI!.....d....|
000000b0  06 e7 d5 56 c5 9d 05 da  8e 49 e5 b6 93 d1 ab ad  |...V.....I......|
000000c0  fe 06 27 68 e9 d0 77 9e  cd b7 fd 6a eb a4 0d 93  |..'h..w....j....|
000000d0  d8 aa ed 73 6d ab ce af  b1 6e 74 ee 25 42 d7 a5  |...sm....nt.%B..|
000000e0  b6 be 73 57 59 fb fe 39  81 1d bd 67 a9 6d c9 c7  |..sWY..9...g.m..|
000000f0  d5 d6 7b 6b be 11 7f 54  97 85 0b f3 95 3b e7 33  |..{k...T.....;.3|
00000100  7d df 2c b3 91 f5 1b aa  7d 07 7f bf 2c dc bb 44  |}.,.....}...,..D|
00000110  08 63 56 6f 2b b3 4d 7f  b2 c1 1c a6 4c 5f 20 d5  |.cVo+.M.....L_ .|
00000120  37 ae b6 76 eb f7 8d a8  34 2f 80 96 cb 5e af b1  |7..v....4/...^..|
00000130  16 7f df 4b b4 ff 9e 71  b9 93 f0 f5 f7 8c 53 75  |...K...q......Su|
00000140  cb 6c 37 fe 99 a9 fb a5  95 59 ab 9c 51 69 6b b1  |.l7......Y..Qik.|
00000150  bc 44 37 cb 4f 66 91 c5  57 da d6 17 4f 0d af 5f  |.D7.Of..W...O.._|
00000160  75 79 4c 59 78 cd 2a 45  fb a4 fc af 3f 7e f0 f1  |uyLYx.*E....?~..|
00000170  33 74 ca e6 e9 44 b2 65  8e 4d 62 90 ba 45 e6 a0  |3t...D.e.Mb..E..|
00000180  e5 c8 ac f9 36 29 dd f8  83 5c d0 4e f6 e0 1a c1  |....6)...\.N....|
00000190  73 cc 0a dd da 9b 11 6c  7e f3 3c 9b cf db 55 ba  |s......l~.<...U.|
000001a0  4b e6 f6 da eb 92 a5 b6  e9 74 fe 50 79 34 bb 5a  |K........t.Py4.Z|
000001b0  b5 c4 36 99 43 d9 d3 12  9d b6 cb d6 0a db 00 fe  |..6.C...........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e8 56 08 00 fe  |............V...|
000001d0  ff ff 05 fe ff ff c6 e8  56 08 3c 27 5c 00 00 00  |........V.<'\...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```I take it from this sdb5 is what we should be concentrating on. Nice tool. Thanks for the help so far.

Quick question: Is hd0 always the drive I've booted from?

---

### Post by drs305 on 2010-05-31
Grub2 is currently installed on sda but looks to the non-reported sda5, so it can't find the files there.

Grub2 is also installed on sdb but looks at sdb1, which mentions Arch and doesn't appear to contain all the G2 files.

sdb5 is where your existing linux install resides. From the LiveCD, do this to install Grub2 on sdb (the drive, not a partition). It will write to the sdb MBR and put the appropriate files into sdb5:

```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

```

Reboot and let us know if it's successful. If it is, run "sudo update-grub" to ensure your Windows install was found.

---

### Post by MathMcC on 2010-05-31
> **drs305 said:**
> Grub2 is currently installed on sda but looks to the non-reported sda5, so it can't find the files there.

**Grub2 is also installed on sdb but looks at sdb1, which mentions Arch and doesn't appear to contain all the G2 files.**

sdb5 is where your existing linux install resides. From the LiveCD, do this to install Grub2 on sdb (the drive, not a partition). It will write to the sdb MBR and put the appropriate files into sdb5:

```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

```Reboot and let us know if it's successful. If it is, run "sudo update-grub" to ensure your Windows install was found.

This makes some sense because iirc arch came before the original ubuntu install in the list of potential os's to boot into. Though its strange because before installing the second version of ubuntu, arch did not come before ubuntu in the list. If this makes any sense.

Also I found that hd0,1 (when I booted into sdb) had the all the mod files but not vmlinuz probably because I didnt complete the arch installation. It got late and I didn't really know what I was doing so i quit part way through!

Pretty sure I tried your suggestion earlier this evening with sdb5, but am about to try again now. Fingers crossed!

---

### Post by MathMcC on 2010-05-31
Success! I can't thank you enough :) Let's hope I've learnt a thing or two along the way.

---

### Post by drs305 on 2010-05-31
> **MathMcC said:**
> Success! I can't thank you enough :) Let's hope I've learnt a thing or two along the way.

:-)

A final note about Grub2. Since you are now booting Grub2 off of sdb, if you notice a delay before the Grub menu appears you can probably reduce it by changing the BIOS to boot the sdb drive first.

Once you are sure everything boots as you want, including Windows, and don't have any other issues with this topic, please mark this thread SOLVED with the Thread Tools link at the top right of the first post.

---

### Post by MathMcC on 2010-05-31
> **drs305 said:**
> :-)

A final note about Grub2. Since you are now booting Grub2 off of sdb, if you notice a delay before the Grub menu appears you can probably reduce it by changing the BIOS to boot the sdb drive first.

Once you are sure everything boots as you want, including Windows, and don't have any other issues with this topic, please mark this thread SOLVED with the Thread Tools link at the top right of the first post.

Done. :)

I had to boot directly from sdb --- sda still takes me to the rescue prompt.

What's the safest way to format that arch linux partition. To be honest my partitions are really messy now - I suppose that's a result of me stupidly trying to manage my linux partitions in windows.

```
sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
```
Is it safe to say that these three are all to do with my arch linux install and seen as i wasn't successful with it and would need to start over anyway I can delete them all?

---

### Post by drs305 on 2010-05-31
> **MathMcC said:**
> Done. :)
Is it safe to say that these three are all to do with my arch linux install and seen as i wasn't successful with it and would need to start over anyway I can delete them all?

The first two aren't needed unless you have data on them. The third (swap) may or may not be currently used. It shouldn't be needed, as your current swap partition should be sdb3, but check first.

Gparted is a great partitioning tool. If you don't already have it installed:
```
sudo apt-get install gparted
```
To start it: System, Administration, Gparted

Once you start it while running Ubuntu normally (not from the LiveCD), look at sda3 and see if it is mounted (it would have a *key* icon next to it in the lower pane if it's mounted). Check to see if there are any other *swap* partitions. Check sdb as well. If there is another one and it's mounted, you can delete the sda3 swap partition provided it is not mounted.
 
You can also check which swap partition is being used with this command, which will show you which partitions are mounted:
```
mount
```

Note: If you still have questions you can remove the SOLVED tag and put it back when you are done, since this is your thread.

---

