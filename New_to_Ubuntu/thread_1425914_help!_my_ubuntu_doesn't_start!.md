---
title: "help! my ubuntu doesn't start!"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by ububiginner on 2010-03-09
First time turned on, nothing happens.  Just cursor brinking in the upper left corner.
 
Second time turned on, GRUB menue opens.  I select a karenel and screen goes to blank.  Again just a cursor brinking in the usual corner.
 
Third time turned on, GRUB menue opens. I press "e" and delete "quiet splash".  Lines of message appear.  One of them says "ata3: SATA link down".  
 
Forth times turned on, Ubuntu starts like there is no problem.  But I never see GRUB menue again.  
 
This is happening everytime I turn on my computer for the first time of the day.
 
Help please,

---

### Post by admiralspark on 2010-03-09
Hello,
First, are you dual booting? Please give us system specifics if you can.
Second, please plop the install CD back in and boot from there. Once the menu comes up, select "Check Disk" or whatever it's labeled; that will make sure the CD was burned right. I suggest this because it sounds like either you have a corrupted install or Grub is messed up. 

If you can get into Ubuntu without any problems, it's probably a problem with Grub. In that case, you will have to replace Grub...which is a drawn out process. 
Please let us know more specifics about the problem and your laptop itself.

---

### Post by ububiginner on 2010-03-09
thank you very much for your time,
 
First, no, I do not have dual boot. I ditched windows since I didn't speak the language. I have Acer Aspier One. 
 
I opened ubuntu using bootable USB.  I checked disk utility and said disk is healthy.  Is that what you mean by "check disk"?

---

### Post by presence1960 on 2010-03-09
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by ububiginner on 2010-03-10
Hi there, thank you for helping me out.

o.k. so, here it is..... I guess I don't know how to attach document.

so, here is copy-n-paste:

     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f56e946

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   306,616,589   306,616,527  83 Linux
/dev/sda2         306,616,590   312,576,704     5,960,115   5 Extended
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4013 MB, 4013948928 bytes
5 heads, 32 sectors/track, 48998 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,839,743     7,831,680   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6a878380-c63d-0c4c-9ace-2e212cc2640b   ext2       casper-rw                     
/dev/sda1        25c61c23-14b2-407a-ad0a-c6c871b3acaa   ext4                                     
/dev/sdb1        7872-A6D7                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 25c61c23-14b2-407a-ad0a-c6c871b3acaa
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 25c61c23-14b2-407a-ad0a-c6c871b3acaa
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 25c61c23-14b2-407a-ad0a-c6c871b3acaa
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 25c61c23-14b2-407a-ad0a-c6c871b3acaa
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 25c61c23-14b2-407a-ad0a-c6c871b3acaa
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 25c61c23-14b2-407a-ad0a-c6c871b3acaa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 25c61c23-14b2-407a-ad0a-c6c871b3acaa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b343ea55-4785-4e80-a1ea-3e53165ea81d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.7GB: boot/grub/core.img
    .4GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .3GB: boot/initrd.img-2.6.31-19-generic
    .3GB: boot/initrd.img-2.6.31-20-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: boot/vmlinuz-2.6.31-19-generic
    .3GB: boot/vmlinuz-2.6.31-20-generic
    .3GB: initrd.img
    .3GB: initrd.img.old
    .3GB: vmlinuz
    .2GB: vmlinuz.old

Thanks again for taking time for me,

---

### Post by presence1960 on 2010-03-10
```
=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa / ext4 errors=remount-ro 0 1
[COLOR="Red"]# swap was on /dev/sda5 during installation
UUID=b343ea55-4785-4e80-a1ea-3e53165ea81d none swap sw 0 0[/COLOR]
```

According to fstab swap was on sda5 at installation time. But now you have no swap partition:

```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #1 for /boot/grub.
=> Syslinux is installed in the MBR of /dev/sdb

sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sdb1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f56e946

Partition Boot Start End Size Id System

/dev/sda1 63 306,616,589 306,616,527 83 Linux
/dev/sda2 306,616,590 312,576,704 5,960,115 5 Extended
Empty Partition


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 4013 MB, 4013948928 bytes
5 heads, 32 sectors/track, 48998 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition Boot Start End Size Id System

/dev/sdb1 * 8,064 7,839,743 7,831,680 b W95 FAT32
```

If you need a swap partition then you will have to create a swap partition within the sda2 extended partition and then change the UUID in etc/fstab to the newly created swap partition's UUID.

If you don't need a swap partition then you need to delete the swap partition reference from /etc/fstab

Let me know which route you want to go.

---

### Post by ububiginner on 2010-03-10
I can go either way, but I guess I would like to have a swap partition.  just in case.  
 
your help is appliciated very much

---

### Post by presence1960 on 2010-03-10
> **ububiginner said:**
> I can go either way, but I guess I would like to have a swap partition.  just in case.  
 
your help is appliciated very much

If you can boot into ubuntu open a terminal and run ```
gksu gparted
```

When gparted loads create a swap partition inside sda2 (extended partition). In use as choose linux-swap. Click the green check mark to apply. See my attached pic. Right click the newly created swap and make sure it is on. Do not choose swap off. If you must turn the swap on click the green check mark to apply.

Now run in terminal ```
sudo blkid -c /dev/null
```
Get the UUID of the swap partition.

Now run in terminal ```
gksu gedit /etc/fstab
```
Substitute the swap UUID in there for the old UUID. Click Save on top toolbar & close file. Reboot & see what happens.

You are having trouble booting because your swap partition can not be found. This should fix it.

Edit: oops the pic...

---

### Post by ububiginner on 2010-03-10
Code:
gksu gedit /etc/fstab
Substitute the swap UUID in there for the old UUID. Click Save on top toolbar & close file. Reboot & see what happens.
 
I'm having a problem with above operation. The fstab has only two lines "aufs / auf rw 0 0" and "tmpf /tmp tmpfs nosuid, nodev 0 0"
 
Where do I put the UUDI ?

---

### Post by ububiginner on 2010-03-10
o.k.  So what I did is that I deleted what was on fstab file and copy and pasted everything I got from the terminal.  I restarted. Started fine but bypassed GRUB menu.  Below is what is on fstab right now

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b343ea55-4785-4e80-a1ea-3e53165ea81d none            swap    sw              0       0

I'll start again tomorrow.

fingers crossed!!

thank you so much for your help!
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by presence1960 on 2010-03-10
> **ububiginner said:**
> Code:
gksu gedit /etc/fstab
Substitute the swap UUID in there for the old UUID. Click Save on top toolbar & close file. Reboot & see what happens.
 
I'm having a problem with above operation. The fstab has only two lines "aufs / auf rw 0 0" and "tmpf /tmp tmpfs nosuid, nodev 0 0"
 
Where do I put the UUDI ?

You must be doing it from the Live CD & you are opening the Cd's fstab file. If so do this:

Go Places > Computer. When the file browser opens highlight your Ubuntu partition (sda1) on the left pane. It won't be under File System as that is the CD's file System.

Now open a terminal and run ```
gksu nautilus
```

Now highlight the ubuntu partition (sda1) on the left (again not under Filesytem) then on the right navigate to /etc/fstab. Open the fstab file. it should contain this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=[COLOR="Red"]b343ea55-4785-4e80-a1ea-3e53165ea81d [/COLOR]none swap sw 0 0
```

replace the red with the new UUID

---

### Post by presence1960 on 2010-03-10
> **ububiginner said:**
> o.k.  So what I did is that I deleted what was on fstab file and copy and pasted everything I got from the terminal.  I restarted. Started fine but bypassed GRUB menu.  Below is what is on fstab right now

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=25c61c23-14b2-407a-ad0a-c6c871b3acaa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b343ea55-4785-4e80-a1ea-3e53165ea81d none            swap    sw              0       0

I'll start again tomorrow.

fingers crossed!!

thank you so much for your help!
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

Ok to get the GRUB menu hit Shift. But you really do not need it since you only have ubuntu and no other OS. If you ever need to boot into recovery mode then hold down the Shift key to bring up the GRUB menu. Since you can now boot into Ubuntu do so. Then open a terminal and run ```
gksu gedit /etc/fstab
```Then edit the UUID to your current swap UUID. Do not do it from the Live CD, but rather from ubuntu.

---

### Post by ububiginner on 2010-03-11
It didn't start....

---

### Post by ububiginner on 2010-03-12
It didn't start....
 
It didn't start with safe mode neither...
 
What else can I do?
 
help

---

### Post by ububiginner on 2010-03-12
[COLOR=black][FONT=Verdana]I don't know if it's help but below is what I got from trying start by deleting "quiet splash"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.084161] use 1-2: new high speed USE device using ehci_hcd and address 2[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.084526] scsi 0:0:0:0: Direct-Access ATA Hitach HTS54501 PBBO PQ: 0 ANSI: 5[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.084924] sd 0:0:0:0: Attached scsi generic sg0 type 0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.085124] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149GiB)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.085350] sd 0:0:0:0: [sda] Write Protect is off[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.085490] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn&#8217;t support DPO or FUA[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.085931] sda:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.395449] usb 1-2: configuration #1 chosen from 1 choice[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.404103] ata3: SATA link down (SStatus 0 Scntrol 300)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.430782]  sda1 sda2 <sda5>[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.461629] sd 0:0:0:0: [sda] Attached SCSI disk[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.461740] Freeing unused kernel memory: 540k freed[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.462317] Write protecting the kernel text: 4580k[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.462468] Write protecting the kernel read-only data: 1840k [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Loading, please wait&#8230;[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.766864] Linux agpgart interface v0.103[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.828160] agpgart-intel 0000:00:00.0: Intel 945GME Chipset[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.828562] agpgart-intel 0000:00:00.0: detected 7932k stolen memory[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.831469] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][2.962320] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/FONT][/COLOR]
 
 
Did it say something meaningful?

---

### Post by ububiginner on 2010-03-13
anyone?

---

### Post by presence1960 on 2010-03-13
Boot the ubuntu Live CD and follow the instructions in post #11 being careful to edit the fstab from your ubuntu partition not the Live CD fstab.

---

### Post by ububiginner on 2010-03-14
hi,  
 
I cannot quite figure out below:
 
[Go Places > Computer. When the file browser opens highlight your Ubuntu partition (sda1) on the left pane. It won't be under File System as that is the CD's file System.

Now open a terminal and run 
Code:
gksu nautilus
Now highlight the ubuntu partition (sda1) on the left (again not under Filesytem) then on the right navigate to /etc/fstab. Open the fstab file. it should contain this:
]
 
 The last time I replaced uuid, I managed to open ubuntu from hard drive...  
 
By the way,  I changed SATA mode: AHCL to IDE in BIOS. then I try to start.  I didn't and I get following message
 
[
[FONT=Calibri][SIZE=3]Boot args (cat /proc/cmdline)[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]                Check rootdelay= (did the sytem wait long enough?)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                Check root= (did the system wait for the right device?)[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Missing modules (cat/proc/modules; 1s/dev)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Alert! /dev/dis/by-uuid/25c61c23-14b2-407a-ad0a-c6c871b3acaa does not exist dropping to a shell[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Busy box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-n shell (ash)[/SIZE][/FONT]
]
 
......?

---

