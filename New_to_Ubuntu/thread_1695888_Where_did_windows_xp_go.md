---
title: "Where did windows xp go?"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by Nod3225 on 2011-02-26
I downloaded a ubunto live cd to install on an old gateway laptop.  when I installed it I was asked if I wanted to install alongside my windows xp.  I selected yes but when I got to the partitions screen I didn't know what to do so I just went on.  Now it boots into Ubunto ok but I can't find windows xp.  Have I deleted it?

---

### Post by Quackers on 2011-02-26
Go to Applications menu > Accessories > Terminal and when it opens type in
```
sudo update-grub
``` then press enter. Watch the terminal screen as grub.cfg is configured. If it picks up a Windows Loader you should reboot and you should see a grub menu, asking which OS to boot.
If no Windows loader is found go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Nod3225 on 2011-02-26
Thanks,  I didn't find it so I will try the download you suggested.

---

### Post by Quackers on 2011-02-26
Hmm, ok, that will tell is what is on there. By the way, which version of Ubuntu did you install? 10-04, 10-10 etc.

---

### Post by Nod3225 on 2011-02-26
10.10

---

### Post by Quackers on 2011-02-26
I had a nasty suspicion of that. We'll see what the boot script says, but be prepared for bad news.

---

### Post by Nod3225 on 2011-02-26
```
#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   124,098,542   124,096,495  83 Linux
/dev/sda2         124,098,558   488,396,799   364,298,242   5 Extended
/dev/sda5         485,328,896   488,396,799     3,067,904  82 Linux swap / Solaris
/dev/sda6         245,415,936   365,513,759   120,097,824  83 Linux
/dev/sda7         482,258,944   485,322,751     3,063,808  82 Linux swap / Solaris
/dev/sda8         124,098,560   242,343,935   118,245,376  83 Linux
/dev/sda9         242,345,984   245,409,791     3,063,808  82 Linux swap / Solaris
/dev/sda10        365,514,752   479,182,847   113,668,096  83 Linux
/dev/sda11        479,184,896   482,254,847     3,069,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        04495303-3e07-4d4f-a143-186b06fdc82a   ext4                                     
/dev/sda10       5f3f7d58-7950-4a65-b2b3-c1a46c5d27f3   ext4                                     
/dev/sda11       fdee6231-a6bb-4186-a268-e932b8204bc8   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9cba6f85-fb02-41cd-ad75-0f055beb3a60   swap                                     
/dev/sda6        bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2   ext4                                     
/dev/sda7        19febc8b-35b5-4085-9593-7deb09e170f5   swap                                     
/dev/sda8        de6853e1-454b-402f-b675-14bf1dba8fc0   ext4                                     
/dev/sda9        9a69d683-aef7-4da9-a40a-3201f93ed4ca   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9cba6f85-fb02-41cd-ad75-0f055beb3a60 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .4GB: boot/vmlinuz-2.6.35-22-generic
    .4GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04495303-3e07-4d4f-a143-186b06fdc82a
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 5f3f7d58-7950-4a65-b2b3-c1a46c5d27f3
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda10
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de6853e1-454b-402f-b675-14bf1dba8fc0
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda8
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=bbd5e6eb-a4f8-43ac-bd55-cb1258f533a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=19febc8b-35b5-4085-9593-7deb09e170f5 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 130.0GB: boot/grub/core.img
 128.3GB: boot/grub/grub.cfg
 127.0GB: boot/initrd.img-2.6.35-22-generic
 125.9GB: boot/vmlinuz-2.6.35-22-generic
 127.0GB: initrd.img
 125.9GB: vmlinuz

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=de6853e1-454b-402f-b675-14bf1dba8fc0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=9a69d683-aef7-4da9-a40a-3201f93ed4ca none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


  63.8GB: boot/vmlinuz-2.6.35-22-generic
  63.8GB: vmlinuz

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=5f3f7d58-7950-4a65-b2b3-c1a46c5d27f3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=fdee6231-a6bb-4186-a268-e932b8204bc8 none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 187.7GB: boot/vmlinuz-2.6.35-22-generic
 187.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 
```

I hope this works.

---

### Post by Quackers on 2011-02-26
Wow, you have 11 partitions, but sadly, no Windows partitions. It looks like Windows is gone. I'm afraid when using the 10.10 installer, the "install alongside" option is a bad choice. It often over-writes existing operating systems.
How many times did you try to install Ubuntu?
It may be worth trying to recover your NTFS partition with testdisk, from the Ubuntu live cd desktop. If you intend on doing that you should stop using the Ubuntu system now! Boot from the live cd and select "try ubuntu" and use that desktop instead, so that no further writing to disc takes place.
Here are guides to getting and running testdisk.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by Nod3225 on 2011-02-26
Thanks,  It sounds like 11 partitions are bad?  I am totally new to this.  It is not a big thing if I lost the windows xp.  What would happen if I reformatted the hard drive and started from scratch?

---

### Post by Quackers on 2011-02-26
Then everything would be wiped - but XP already has been.
You should install XP first, either in a ready made partition (using the live cd desktop and gparted) or using the whole hard drive, then resizing it after installation to allow space for the Ubuntu partitions. The first may be best.

---

### Post by Nod3225 on 2011-02-26
thanks,  I guess I will reformat the hard drive reinstall windows xp and then ubunto.

---

### Post by rewyllys on 2011-02-26
Good luck with re-installing XP and then installing Ubuntu.  

With respect to the latter task, I'd like to strongly recommend that you use separate partitions for your root directory, "/",  and your home directory, "/home".  (You'll also need a separate partition for your swap directory.)

The home directory contains your personal data and the configuration files for the programs you use.  Having your home directory on a separate partition will let you avoid a lot of possible troubles with future upgrades and/or re-installations, because you can wipe out your root directory, and even re-format the root directory's partition, without losing your personal data and configurations.

---

### Post by Nod3225 on 2011-02-27
I almost have it.  I reinstalled windows xp and am ready to install the ubunto.  I have selected the option to install alongside windows.  When I get to the option to move the slider to alocate space for windows I have chosen 30 gig for windows and 40 for ubunto.  Is that enough for ubunto?  finally there are 2 buttons below and I assume I should check the one that says use entire partition?

---

### Post by jerenept on 2011-02-27
> **Nod3225 said:**
> I almost have it.  I reinstalled windows xp and am ready to install the ubunto.  I have selected the option to install alongside windows.  When I get to the option to move the slider to alocate space for windows I have chosen 30 gig for windows and 40 for ubunto.  Is that enough for ubunto?  finally there are 2 buttons below and I assume I should check the one that says use entire partition?

What do the 2 buttons say?

---

### Post by Nod3225 on 2011-02-27
one says use the entire partition and the other says use entire disk

---

### Post by jerenept on 2011-02-27
you don't need to click one of those. just click "next" or "install"

---

### Post by Nod3225 on 2011-02-27
Thanks It is installing now

---

### Post by Hakunka-Matata on 2011-02-27
> **Nod3225 said:**
> I downloaded a ubunto live cd to install on an old gateway laptop.  when I installed it I was asked if I wanted to [COLOR="Red"][SIZE="3"]install alongside my windows xp[/SIZE][/COLOR].  I selected yes but when I got to the partitions screen I didn't know what to do so I just went on.  Now it boots into Ubunto ok but I can't find windows xp.  Have I deleted it?

@Nod3225, I hope your install works, but it appears you are attempting to install it in the same fashion you did before: i.e. your post #1, quoted above.  If you find that you are left with a good Ubuntu System but no XP system as happened the first time around, please read Post #6.  I'll be very curious to see how your install turns out.. Good Luck

---

### Post by Hakunka-Matata on 2011-02-27
I realise this is unsolicited, so excuse me if I offend.  But many people have been bitten by this issue.  It's a shame because it reflects badly on an Excellent OS, the installer will get fixed some day, sooner hopefully rather than later.

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install")

> Boot, installation, upgrade and post-install

    *

      In dual boot installs, side-by-side partitioning can be overridden by the user, resulting in data loss. After selecting the "Install alongside other operating systems" option, clicking on either the "Use entire partition" of "Use entire disc" buttons will override the side-by-side partitioning and [COLOR="Magenta"][COLOR="Magenta"]result in a loss of data[/COLOR][/COLOR]. (655950) 

---

