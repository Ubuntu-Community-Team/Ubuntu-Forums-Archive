---
title: "problem triple booting"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by nitstorm on 2010-02-11
hey guys, 

jus tried triple booting xp, ubuntu and opensuse. result: failure!
i had xp and ubuntu 9.10 dual booting previously, added opensuse 11.2  just now and the grub seems to have disappeared, wen i start my machine now i just get three options - opensuse 11.2, windows, failsafe opensuse

what do i do????

this is my output of fdisk -l if u need it. please help !!!
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe603e603

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5357    43030071    7  HPFS/NTFS
/dev/sda2   *        5358       18643   106719795    f  W95 Ext'd (LBA)
/dev/sda5            5358       12998    61376301    7  HPFS/NTFS
/dev/sda6           16155       18519    18996831   83  Linux
/dev/sda7           18520       18643      995998+  82  Linux swap / Solaris
/dev/sda8           12999       16154    25350538+  83  Linux

```

---

### Post by audiomick on 2010-02-11
Hi,
I have no personal experience of it, but I have read that SuSe installed after Ubuntu will mess up your grub. I dont know which boot loader SuSe is using these days, but there is a fair bet that it has overwritten your grub.

My guess is that your options would be to try and correct the configuration of whatever bootloader is now installed, or re-install grub.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Whilst I am not very good at reading it, I know that the results of the boot info script mentioned here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
should tell you pretty much all there is to know about your boot setup. Maybe if you post the results.txt here (use code tags around it, the # button) it will assist people to help you.

---

### Post by philinux on 2010-02-11
+1 info from audiomick.

As windows eats grub sounds like suse does too.

Time to put grub back on then.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by kansasnoob on 2010-02-11
Yep, you need to restore Ubuntu's grub. But we need to know more. Post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That way I can see what Ubuntu's grub looks like, which partition is Ubuntu and which is Suse, etc.

---

### Post by kansasnoob on 2010-02-11
If you manage to get Ubuntu's grub2 restored on your own the following worked for adding Suse to mine:

[http://digitizor.com/2009/12/28/how-to-add-opensuse-11-2-to-grub2/](http://digitizor.com/2009/12/28/how-to-add-opensuse-11-2-to-grub2/)

---

### Post by nitstorm on 2010-02-11
============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 214222469 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe603e603

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    86,060,204    86,060,142   7 HPFS/NTFS
/dev/sda2    *     86,060,205   299,499,794   213,439,590   f W95 Ext d (LBA)
/dev/sda5          86,060,268   208,812,869   122,752,602   7 HPFS/NTFS
/dev/sda6         259,514,073   297,507,734    37,993,662  83 Linux
/dev/sda7         297,507,798   299,499,794     1,991,997  82 Linux swap / Solaris
/dev/sda8         208,812,933   259,514,009    50,701,077  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4834DE1C34DE0D36                       ntfs                                     
/dev/sda5        01CA90EE7AD84350                       ntfs                                     
/dev/sda6        87c9b9fc-6ead-43d8-b69e-551409fc094e   ext4                                     
/dev/sda7        e1208fd7-10c9-436d-b013-667a0fa36f5b   swap                                     
/dev/sda8        e67ec47c-8b79-480f-81d6-534982028161   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,acl,user_xattr)
/dev/sda1        /windows/C               fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /windows/D               fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 87c9b9fc-6ead-43d8-b69e-551409fc094e
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 87c9b9fc-6ead-43d8-b69e-551409fc094e
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=87c9b9fc-6ead-43d8-b69e-551409fc094e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 87c9b9fc-6ead-43d8-b69e-551409fc094e
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=87c9b9fc-6ead-43d8-b69e-551409fc094e ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 87c9b9fc-6ead-43d8-b69e-551409fc094e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=87c9b9fc-6ead-43d8-b69e-551409fc094e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 87c9b9fc-6ead-43d8-b69e-551409fc094e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=87c9b9fc-6ead-43d8-b69e-551409fc094e ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 87c9b9fc-6ead-43d8-b69e-551409fc094e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=87c9b9fc-6ead-43d8-b69e-551409fc094e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 87c9b9fc-6ead-43d8-b69e-551409fc094e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=87c9b9fc-6ead-43d8-b69e-551409fc094e ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4834de1c34de0d36
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "openSUSE 11.2 (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 948a43ca-ed6f-46c7-aed9-3eaf288be409
    linux /boot/vmlinuz root=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part8 resume=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part7 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd
}
menuentry "Failsafe -- openSUSE 11.2 (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 948a43ca-ed6f-46c7-aed9-3eaf288be409
    linux /boot/vmlinuz root=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part8 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=87c9b9fc-6ead-43d8-b69e-551409fc094e / ext4 errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=e1208fd7-10c9-436d-b013-667a0fa36f5b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda8 /media/Disk1 ntfs-3g defaults,locale=en_IN 0 0
/dev/sda5 /media/Disk2 ntfs-3g defaults,locale=en_IN 0 0
/dev/sda1 /media/Disk3 ntfs-3g defaults,locale=en_IN 0 0

=================== sda6: Location of files loaded by Grub: ===================


 132.8GB: boot/grub/core.img
 132.8GB: boot/grub/grub.cfg
 132.8GB: boot/initrd.img-2.6.31-14-generic
 132.8GB: boot/initrd.img-2.6.31-17-generic
 132.8GB: boot/initrd.img-2.6.31-19-generic
 132.8GB: boot/vmlinuz-2.6.31-14-generic
 132.8GB: boot/vmlinuz-2.6.31-17-generic
 132.8GB: boot/vmlinuz-2.6.31-19-generic
 132.8GB: initrd.img
 132.8GB: initrd.img.old
 132.8GB: vmlinuz
 132.8GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Fri Feb 12 00:21:42 IST 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,7)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2 - 2.6.31.12-0.1
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.31.12-0.1-default root=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part8 resume=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part7 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.31.12-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.12-0.1
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.31.12-0.1-default root=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part8 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.31.12-0.1-default

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader +1

=============================== sda8/etc/fstab: ===============================

/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part7 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part8 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part5 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

---

### Post by nitstorm on 2010-02-11
> 
NOTE: Although the title says this is for adding OpenSUSE, it should work for adding other OS as well) OpenSUSE 11.2 uses the legacy Grub in contrast to Grub2 that is used by Ubuntu 9.10. So, when I installed OpenSUSE 11.2 in my laptop which has Ubuntu Karmic installed, the Grub that it installed did not recognize my Ubuntu installations. Now, getting back Grub2 is just a simple matter of booting using the Ubuntu Live CD and reinstalling it. However, that left out OpenSUSE 11.2 from the menu list.
 If you have been in similar circumstance and wishes to get OpenSUSE 11.2 back in your Grub2 menu list, here is what you need to do:
 
[LIST]
[*]Open Terminal.
[*]Enter the following commands one by one
[/LIST]
[INDENT]sudo apt-get install &#8211;reinstall libdebian-installer4
[/INDENT][INDENT]sudo os-prober
[/INDENT][INDENT]sudo  update-grub
[/INDENT]Now, reboot and you should see OpenSUSE listed in the Grub2 menu list along with everything else.



So i need to do a full reinstall of ubuntu karmic now!!!????

---

### Post by nitstorm on 2010-02-11
sitting in ubuntu live cd booted version and dont know what to do, please help!!!!

---

### Post by lunix- on 2010-02-11
I don't think you need to do a reinstall.. Luckily linux is pretty tweakable if you knwo what you are doing.. and if you dont as well :)

I guess that /boot/grub/grub.cfg file contains errors and needs to get fixed. I cloned my ubuntu harddrive with dd command once.. that messed up this file. I got it fixed by setting the correct boot order in the bios (to the preferred ubuntu 9.10 harddrive). After booting up I ran the command 'update-grub'.  That fixed it.   

I think I had to press 'e' in the grub menu to change the disk to boot from also..  Booting from ubuntu CD and editing the grub.cfg file could also work but is not advisable I think.

When you are able to boot to your ubuntu OS, then you should run 'update-grub', and hopefully your ok  :)

I'm a grub-noob, so Im sure there are a lot easier and more elegant ways of fixing grub problems, but this worked for me.

Not beeing able to boot is really frustrating, so good luck:)

---

### Post by Habboblob on 2010-02-11
> **nitstorm said:**
> sitting in ubuntu live cd booted version and dont know what to do, please help!!!!

Restore the Grub Menu: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

After you boot into Ubuntu.
Type this command into Terminal:
```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

or try this:

> [SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

Since Ubuntu 9.10 uses Grub 2, the above method will not work. However, it can still be done and this is how:
 First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
``` You will get something like this:


[IMG]http://talsemgeest.doesntexist.com/blog/wp-content/uploads/2009/09/SVR8XIL.JPG[/IMG]

From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE]

First of all, all credit for this part of the tutorial goes to [catlet]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1"). I am simply rewriting his tutorial to have all three bootloaders in this tutorial.

So, lets begin. To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.

Once there, open a terminal (Applications>Accessories>Terminal) and type this:

```
sudo grub
```Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:

```
find /boot/grub/stage1
```Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:

```
root (hd<a>,<b>)
```Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:

```
setup (hd0)
```Now to quit and check if it has worked:

```
quit
``````
sudo reboot
```Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.


---

### Post by lunix- on 2010-02-11
thats a beautiful response.  If it works,  I'll copy it, print it out, and peg it on the wall for future reference

---

### Post by philinux on 2010-02-11
Habboblob,

He's using grub2. See link post #3 also see my sig for grub2 info.

---

### Post by audiomick on 2010-02-11
sda6 has got what is left of the 9.10 grub 2 ( the config files) on it, and it looks like SuSe added a legacy grub on sda2.

I would be attempting to re-install grub 2, but maybe philinux has some advice.
I have to bail out now. I will look back tomorrow.

---

### Post by nitstorm on 2010-02-11
i keep getting some error!!! annoying!!!

this is what i have done - used gparted deleted the opensuse partition, changed the label of my ubuntu drive to** / **but in the live disc it shows up as /media/_  that's annoying!!! and wen i restart the comp  i just get a cli saying grub>   i dunno what to do there either!!! and sudo update-grub gives the following error:
grub-probe: error: cannot find a device for /.

and sudo grub-install gives: install device not specified

---

### Post by philinux on 2010-02-11
> **nitstorm said:**
> i keep getting some error!!! annoying!!!

this is what i have done - used gparted deleted the opensuse partition, changed the label of my ubuntu drive to** / **but in the live disc it shows up as /media/_  that's annoying!!! and wen i restart the comp  i just get a cli saying grub>   i dunno what to do there either!!! and sudo update-grub gives the following error:
grub-probe: error: cannot find a device for /.

and sudo grub-install gives: install device not specified

You need to follow the link I gave you in post #3.

You need to use a chroot jail from the livecd to reinstall grub2.
Just follow the instructions in the link to reinstall grub2 to /dev/sda

---

### Post by nitstorm on 2010-02-11
i finally got my head outta my a** and followed the instructions on post#3 . now i am back on ubuntu and loving it, not gonna go anywhere away from it. Thanks a trillion to philinux and others. Philinux u rock bro ! Cheers!!! Thread solved :D

---

### Post by philinux on 2010-02-11
> **nitstorm said:**
> i finally got my head outta my a** and followed the instructions on post#3 . now i am back on ubuntu and loving it, not gonna go anywhere away from it. Thanks a trillion to philinux and others. Philinux u rock bro ! Cheers!!! Thread solved :D

Good news indeed. I would bookmark that link if you're going tinkering. 

;)

---

### Post by nitstorm on 2010-02-11
Already bookmarked, and copied to a notepad file just in case :D

---

### Post by kansasnoob on 2010-02-11
Why did you do this:

> changed the label of my ubuntu drive to / but in the live disc it shows up as /media/_

I'm not even sure I understand what you mean. You're being impatient and doing all kinds of things wrong!

You didn't need to remove Suse! And now I'd like to see a screenshot of Gparted so I can try to understand what you did.

Patience is a virtue :)

---

