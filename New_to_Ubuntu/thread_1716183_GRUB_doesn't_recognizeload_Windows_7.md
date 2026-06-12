---
title: "GRUB doesn't recognize/load Windows 7"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by dspetrov on 2011-03-28
Hi, I'm new to Ubuntu and I installed Ubuntu 10.04 Desktop 64-bit on a system that already has Windows 7 32-bit installed and working. On boot it doesn't display a menu for dual boot and Ubuntu starts. I have one 320 GB HDD with the following partitions:
70 GB Windows 7
200 GB Data (NTFS)
30 GB (it was unpartitioned and the Ubuntu installed created the SWAP drive and the drive where Ubuntu is installed)

After reading around the forums I have this:
the result from the command "sudo fdisk -lu":

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73636731

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   146802687    73297920    7  HPFS/NTFS
/dev/sda2       146802688   566234328   209715820+   7  HPFS/NTFS
/dev/sda3       566235134   625141759    29453313    5  Extended
/dev/sda5       566235136   622618623    28191744   83  Linux
/dev/sda6       622620672   625141759     1260544   82  Linux swap / Solaris

After reading I created the file menu.lst in /boot/grub folder with this contents:
title Windows 7
root (hd0,0)
savedefault
makeactive
chainloader +1

This led to no change. I also tried the command "sudo update-grub". The result is this:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done

Again nothing changed. All this looks to me as GRUB doesn't recognize/load the Windows 7 partition (or the OS itself). Please help! Thank you in advance! :)

---

### Post by robsoles on 2011-03-28
Welcome to UF.

Your description of your problem makes me think you are pretty advanced for an absolute beginner. I've got a frank admission, I switched from Windows to Ubuntu without ever doing the dualboot thing (I'd been stuck in Windows and working with Server Eds (text only) of Linux for a while!)  and the information from which I am working to respond is rather incomplete but....

Have you seen/(worked through) [http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html) ?

Maybe it will be quicker to search on [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) for 'windows' (without apostrophe/quotes, just using [CTRL]+[F] when page has loaded) and see if you can follow any steps that allow you to get Windows 7 listed in your boot menu. Pretty sure that was grub2 booting my Ubuntu 10.04 installs last time I had to tackle it.

It sounds like you manually partitioned (or chose a specific location to install to at least) and you didn't choose the option similar to "install them side by side, choosing between them at start up" and now grub is doing an excellent job of it's task, as configured overall by the installer, and only offering you the Ubuntu install. Please tell me if I am wrong and you chose the one that made it sound like you really should be offered dual boot on start up?

Sorry I can't tell you the minimum sequence of steps to fix it straight up but my post brings your thread back to the top of the list and it might even so much as provoke better responses from others who have actually played with dualboot :)

---

### Post by coffeecat on 2011-03-28
Hi, and welcome to the forum.

First:

> **dspetrov said:**
> After reading I created the file menu.lst in /boot/grub folder with this contents:
title Windows 7
root (hd0,0)
savedefault
makeactive
chainloader +1

This led to no change.

The file menu.lst is a configuration file for the older legacy grub. You have grub2 which has a different configuration so you can happily forget about menu.lst

> **dspetrov said:**
>  I also tried the command "sudo update-grub". The result is this:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done

Thanks for posting that output. That's useful. There are several possible reasons why update-grub is not detecting Windows. These include:

* - The Windows C: partition filesystem is in an inconsistent state.

* - Some grub files have been written to the boot sector of the Windows boot partition.

* - The application os-prober has gone missing from Ubuntu. This should not happen as os-prober is part of a default installation, but I've been involved in threads where it was so - inexplicably.

As a start, boot up Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file in code tags as described there. Then we can take it from there.

---

### Post by dspetrov on 2011-03-28
Hi robsoles and thank you for the quick answer! I checked the URL that you posted and it is helpful. I haven't still used the Windows auto repair that's mentioned there because I prefer to see the result from Boot Info Script mentioned in the reply after your's. :)

As for your question about the manual partitions - yes, I've manually partitioned, because the option "install them side by side, choosing between them at start up" wanted to resize my 200 GB data partition and leave the 30 GB unpartitioned space instead of installing on that 30 GB (that were for that purpose).... which was quite strange for me!

---

### Post by Razorback on 2011-03-28
> **coffeecat said:**
> hi, and welcome to the forum.

As a start, boot up ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

download and run the boot info script and post the results.txt file in code tags as described there. Then we can take it from there.

+1

---

### Post by M4rotku on 2011-03-28
10.04 uses grub2, not the original grub, and thus your way of going about editing the grub config files is outdated.  Editing the menu.lst won't do anything anymore.  Firstly, because it would no longer exist and thus if you created the file, it would not be used by grub.  Secondly, the file which has replaced it '/boot/grub/grub.cfg' should not be edited by hand.  With grub2, you edit the files in the /etc/grub.d directory and then run then grub itself will create the grub.cfg based on those files.

I hope this helps,
M4rotku

EDIT:  I had not seen Coffeecat's answer before writing my own.  Use his.

---

### Post by dspetrov on 2011-03-28
Hi cofeecat and thanks for the reply! Here's the result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        206,848   146,802,687   146,595,840   7 HPFS/NTFS
/dev/sda2         146,802,688   566,234,328   419,431,641   7 HPFS/NTFS
/dev/sda3         566,235,134   625,141,759    58,906,626   5 Extended
/dev/sda5         566,235,136   622,618,623    56,383,488  83 Linux
/dev/sda6         622,620,672   625,141,759     2,521,088  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5260358C603577B5                       ntfs       Windows                       
/dev/sda2        4C5ADA6D5ADA5376                       ntfs       Data                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4   ext4                                     
/dev/sda6        bf3f4dfc-20fb-484a-aa51-3375ec7076f1   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

title Windows 7
root (hd0,0)
savedefault
makeactive
chainloader +1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0a977e3c-8c33-4ef3-83ae-7c6c6eb8a9f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bf3f4dfc-20fb-484a-aa51-3375ec7076f1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 294.4GB: boot/grub/core.img
 300.8GB: boot/grub/grub.cfg
 294.3GB: boot/grub/menu.lst
 294.4GB: boot/initrd.img-2.6.32-28-generic
 294.4GB: boot/vmlinuz-2.6.32-28-generic
 294.4GB: initrd.img
 294.4GB: vmlinuz
```

---

### Post by drs305 on 2011-03-28
The section of the grub.cfg which is supposed to be created by os-prober looks like the output when os-prober is not run.

If you have Lubuntu, os-prober is not installed by default. In other releases, perhaps it is missing or defective.

You can see if it is working on your machine by running the following command:
```
sudo os-prober
```

Does running the command produce output or an error message? If it runs, does it see Windows?

If it doesn't run or isn't installed, try installing it and rerunning update-grub:
```
sudo apt-get install os-prober
sudo update-grub
```

As the second command runs watch the terminal output to see if your system now finds Windows.

There are other ways os-prober can be disabled but for now I'm assuming you haven't done so by changing the grub files or their properties.

---

### Post by oldfred on 2011-03-28
Windows 7 typically installs a small 100MB (hidden in windows) boot/recovery partition that has these two files. It is so you could encrypt the main install and future use with gpt where a separate boot partition will be required (more training users that a new boot partition will be required).
/bootmgr /Boot/BCD 

Then the main install partition has this (which yours does).
/Windows/System32/winload.exe

Did you delete a small partition somewhere?

But you can repair your main install and add the missing boot files. Win7 will install just fine to one partition and work from that with MBR partitioning.

I have copied instructions from windows sites:

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.( you have boot flag on sda1)

---

### Post by dspetrov on 2011-03-28
I tried "sudo os-prober" and there was no result. Then I tried "sudo apt-get install os-prober" and this is it:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version.
os-prober set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.

The command "sudo update-grub" after that doesn't find Windows again:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by drs305 on 2011-03-28
os-prober is installed and working, so it's time to concentrate on the missing Windows folders *oldfred* has identified. I'll leave it to him or others as Windows repair/restoration is not my strong point.

---

### Post by dspetrov on 2011-03-28
It turned out that the Windows 7 partition boot was corrupted. I used the Windows 7 disc to repair it and it was fixed. Then the command "sudo update-grub" found all the partitions and after a restart of the system there was the menu with the dual boot. :D

Thank you all for the help!

---

