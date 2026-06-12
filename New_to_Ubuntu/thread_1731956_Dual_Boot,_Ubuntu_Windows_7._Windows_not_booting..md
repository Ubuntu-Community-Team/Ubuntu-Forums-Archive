---
title: "Dual Boot, Ubuntu Windows 7. Windows not booting."
date: 2011-04-17
forum: New to Ubuntu
---

### Post by zainhuss on 2011-04-17
Hi, I installed Ubuntu 10.10 Netbook Remix, on my Samsung N110, which had Windows 7 pre-installed.

I want to run them both, side by side.
When installing Ubuntu, I had to adjust my partitions to Install Ubuntu.

However, now, whenever I start my computer, Ubuntu starts up, and i don't get an option to choose Win7.

I think this is because, when adjusting partitions, I may have deleted the "Windows 7 Loader" Partition, so it does not boot Win 7

On the positive, my partition for Windows 7 is still there, because, when I go to Disk Utility on Ubuntu, there is a partition which says, "Windows 7".

Also, I installed Ubuntu on a USB, as i own a netbook.


Any help??
Thanks

---

### Post by scott-ian on 2011-04-17
You should install "Startup-manager" and make sure the boot delay is not set to 0.

---

### Post by zainhuss on 2011-04-17
If any additional information needed, pls ask.
Thanks

---

### Post by zainhuss on 2011-04-17
@scott-ian,
i will try and let u know.
Thanks.

---

### Post by zainhuss on 2011-04-17
@scott-ian
I ran the Stratup Utility, but in the default OS, Windows 7 doesnt even show up.
Even though it shows uo in the partitions.
I think i may have damaged the partitions :/

---

### Post by scott-ian on 2011-04-17
If it is zero, you can change it.  That is the amount of time it gives you to choose to load another operating system.

---

### Post by scott-ian on 2011-04-17
Can you access the Windows 7 files?

---

### Post by zainhuss on 2011-04-17
Yeah, i can access the files, as the partition has been "mounted"

---

### Post by scott-ian on 2011-04-17
It seems you have deleted the Windows 7 boot loader, but everything else is intact.

---

### Post by zainhuss on 2011-04-17
yep :L...what do you suggest I do?
Thanks

---

### Post by Leppie on 2011-04-17
zainhuss, can download and run the boot info script and post the generated results.txt: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by zainhuss on 2011-04-17
*Are there any solutions?...

---

### Post by zainhuss on 2011-04-17
Sorry for the trouble, just another question.
What program should I use to open this program that u just suggested to me.
P.S.I am using Ubuntu 10.10 Netbook Remix

---

### Post by scott-ian on 2011-04-17
The files for booting windows are contained in a directory entitled "boot" on the windows partition.  Is that folder in existence?

---

### Post by scott-ian on 2011-04-17
Open the terminal, cd to the location the file is in, and type "sh boot_info_script055.sh"

---

### Post by zainhuss on 2011-04-17
@Scott-ian
Yes, in the partition, within a folder named "Windows", there is a folder named "Boot".

---

### Post by Leppie on 2011-04-17
never mind...

---

### Post by scott-ian on 2011-04-17
> **zainhuss said:**
> @Scott-ian
Yes, in the partition, within a folder named "Windows", there is a folder named "Boot".
There should be one at the root of the windows partition.
If that is the one you are talking about, you might want to back it up before attempting to fix the problem

---

### Post by zainhuss on 2011-04-17
I know to, "Ctrl+Alt+T".
But how do i "cd" to the location.
P.S., the location is, "Zain"-"Downloads"

---

### Post by Leppie on 2011-04-17
> **zainhuss said:**
> @Scott-ian
Yes, in the partition, within a folder named "Windows", there is a folder named "Boot".
did you run that script?

---

### Post by scott-ian on 2011-04-17
The cd command is simple.  Let's say you script is in the "Downloads" folder (where I suspect it is)
Simply type: cd Downloads

---

### Post by zainhuss on 2011-04-17
I cannot, because I do not know how to "cd" to the location.

---

### Post by scott-ian on 2011-04-17
I was mistaken.  After using the cd command, type "sudo bash boot_info_script055.sh"
If your worried the script is a virus, I have tested it, and it works fine.

---

### Post by scott-ian on 2011-04-17
It should be as simple as typing "cd Downloads"

---

### Post by zainhuss on 2011-04-17
Here are the results:
/home/zain/Downloads/RESULTS.txt
If u cannot open then here:
                Boot Info Script 0.55    dated February 15th, 2010                    
```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     6,306,311     6,304,264  12 Compaq diagnostics
/dev/sda2    *     20,973,568    21,178,367       204,800  82 Linux swap / Solaris
/dev/sda3          21,178,368   253,962,239   232,783,872   7 HPFS/NTFS
/dev/sda4         253,962,240   293,024,739    39,062,500  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c94ed50d-7529-43b6-9aec-572f32b6c444   ext4                                     
/dev/sda2        f8d060a5-167d-4d64-b305-0aadde9aba8d   swap                                     
/dev/sda3        1E4A51CE4A51A2F7                       ntfs       Windows                       
/dev/sda4        ee3654ed-61e4-4bbc-8ba2-13e24ef870b7   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /boot                    ext4       (rw,commit=0)
/dev/sda3        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set ee3654ed-61e4-4bbc-8ba2-13e24ef870b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux    /vmlinuz-2.6.35-22-generic root=UUID=ee3654ed-61e4-4bbc-8ba2-13e24ef870b7 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=ee3654ed-61e4-4bbc-8ba2-13e24ef870b7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: grub/core.img
    .1GB: grub/grub.cfg
    .2GB: initrd.img-2.6.35-22-generic
    .1GB: vmlinuz-2.6.35-22-generic

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=ee3654ed-61e4-4bbc-8ba2-13e24ef870b7 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
/dev/sda2       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 130.2GB: initrd.img
 130.2GB: vmlinuz
```

---

### Post by scott-ian on 2011-04-17
The script didn't find any problems...

---

### Post by scott-ian on 2011-04-17
It must be an error in the Grub configuration.

---

### Post by zainhuss on 2011-04-17
Oh. . . 
But, why is it that when i get a choice of 2 OS in the boot loader, I get,
Ubuntu, Ubuntu recovery,
and "mem. . ." something :LL

---

### Post by zainhuss on 2011-04-17
And when I click on "mem...", i am given a long script, and that's all, no Win7.

---

### Post by zainhuss on 2011-04-17
Also, the script does not mention a "Windows Loader", so I must have deleted it.
Any help?

---

### Post by scott-ian on 2011-04-17
This might help: [http://www.fedoraforum.org/forum/showthread.php?t=996](http://www.fedoraforum.org/forum/showthread.php?t=996)

---

### Post by scott-ian on 2011-04-17
> **zainhuss said:**
> 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr


That shows you probably did not delete anything.

---

### Post by scott-ian on 2011-04-17
Did you do a normal install or a WUBI install?

---

### Post by zainhuss on 2011-04-17
thanks, but how do i access my BIOS setup?

---

### Post by zainhuss on 2011-04-17
I did a normal install with a USB.

---

### Post by zainhuss on 2011-04-17
Also, do you think that if I installed GRUB (whatever it is) again, or deleted Ubuntu from my netbook (don't know how to though), the problem would be solved?

---

### Post by scott-ian on 2011-04-17
The fault seems to be with the grub boot loader.  Edit /etc/default/grub and run the grub-mkconfig command to change Grub settings.  Could you post the contents of /etc/default/grub?

---

### Post by scott-ian on 2011-04-17
Forget the last thing I said.  This command might fix the problem:
sudo update-grub

---

### Post by oldfred on 2011-04-17
Boot flag is on sda2 and it is a 100MB partition. That would indicate that it was the windows system partition (hidden in windows).

The windows system partition has two windows boot files.
/bootmgr /Boot/BCD 

The main windows install has this:
/Windows/System32/winload.exe

You can move boot flag to sda3 and run windows repairs and it will reinstall /bootmgr & create a new /Boot/BCD.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

### Post by uRock on 2011-04-17
Try, ```
sudo update-grub
```

---

### Post by scott-ian on 2011-04-17
> **oldfred said:**
> Boot flag is on sda2 and it is a 100MB partition. That would indicate that it was the windows system partition (hidden in windows).

The windows system partition has two windows boot files.
/bootmgr /Boot/BCD 

The main windows install has this:
/Windows/System32/winload.exe

You can move boot flag to sda3 and run windows repairs and it will reinstall /bootmgr & create a new /Boot/BCD.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
I don't think this will help.  The problem is the grub configuration.
See this: [http://ubuntuforums.org/showthread.php?t=144718](http://ubuntuforums.org/showthread.php?t=144718)

---

### Post by Leppie on 2011-04-17
> **scott-ian said:**
> The script didn't find any problems...
grub is looking in msdos1/grub for its files, but they are installed in /boot/grub
> 
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in     partition #1 for (,[COLOR=Red]msdos1[/COLOR])/grub.
to repair grub using a livecd, issue the following commands:
```
sudo -i
mkdir /mnt/temp
mount /dev/sda1 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit
```then reboot and see if it's working normally

---

### Post by scott-ian on 2011-04-17
Before doing anything else, try the command:
sudo update-grub

---

### Post by Leppie on 2011-04-17
> **scott-ian said:**
> Before doing anything else, try the command:
sudo update-grub

that should not change the link in the master boot record pointing to (,msdos1)/grub

---

### Post by scott-ian on 2011-04-17
The problem is that grub is not detecting windows.  If sudo update-grub doesn't work, then the solution would be to edit /boot/grub/menu.lst

---

### Post by zainhuss on 2011-04-17
i tried sudo update-grub, but still made no difference.

@Old fred, what u r saying seems quite complicated for me :(...i am using a netbook, so cannot insert a "recovery disc".
Any other suggestions ppl?
Thanks

---

### Post by zainhuss on 2011-04-17
some help on how to edit boot/grub/lst ??
Thanks

---

### Post by Leppie on 2011-04-17
> **zainhuss said:**
> i tried sudo update-grub, but still made no difference.

@Old fred, what u r saying seems quite complicated for me :(...i am using a netbook, so cannot insert a "recovery disc".
Any other suggestions ppl?
Thanks
are you currently in ubuntu?

---

### Post by scott-ian on 2011-04-17
The recovery disk would not be an option.  I believe the problem is related Grub, but I may be wrong.

---

### Post by zainhuss on 2011-04-17
> **Leppie said:**
> are you currently in ubuntu?
Yep

---

### Post by scott-ian on 2011-04-17
> **zainhuss said:**
> some help on how to edit boot/grub/lst ??
Thanks
My mistake.  That file doesn't seem to exist... my source is a little out of date.
As for a boot disk, you probably should be able to fix it from within Ubuntu.

---

### Post by zainhuss on 2011-04-17
> **scott-ian said:**
> My mistake.  That file doesn't seem to exist... my source is a little out of date.
As for a boot disk, you probably should be able to fix it from within Ubuntu.
lol....no problem.
awlryt, that good news, any ideas how?

---

### Post by Leppie on 2011-04-17
issue these commands in a terminal:
```
sudo grub-install --recheck /dev/sda
sudo update-grub

```

then run the boot info script and post the results again

---

### Post by scott-ian on 2011-04-17
This seems to be the solution:
[http://www.brighthub.com/computing/linux/articles/36648.aspx](http://www.brighthub.com/computing/linux/articles/36648.aspx)
But neither of the configuration files mentioned exist on my computer.

---

### Post by Leppie on 2011-04-17
> **scott-ian said:**
> This seems to be the solution:
[http://www.brighthub.com/computing/linux/articles/36648.aspx](http://www.brighthub.com/computing/linux/articles/36648.aspx)
But neither of the configuration files mentioned exist on my computer.
these are instructions for grub legacy... not grub2 which has been the default boot loader since karmic...

---

### Post by scott-ian on 2011-04-17
> **Leppie said:**
> these are instructions for grub legacy... not grub2 which has been the default boot loader since karmic...
Oops.  Then this should help: [http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/](http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/)

---

### Post by Leppie on 2011-04-17
i put the instructions in post #53

---

### Post by zainhuss on 2011-04-17
> **Leppie said:**
> issue these commands in a terminal:
```
sudo grub-install --recheck /dev/sda
sudo update-grub

```then run the boot info script and post the results again
sudo grub-install --recheck /dev/sda sudo update-grubthe top line doesn't seem to be working :L, it says that it isn't a command

---

### Post by Leppie on 2011-04-17
> **scott-ian said:**
> Oops.  Then this should help: [http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/](http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/)
this is for customising grub, not reparing

---

### Post by scott-ian on 2011-04-17
> **zainhuss said:**
> sudo grub-install --recheck /dev/sda sudo update-grubthe top line doesn't seem to be working :L, it says that it isn't a command
It works on my computer.

---

### Post by zainhuss on 2011-04-17
> **scott-ian said:**
> It works on my computer.
so....no more suggestions anyone??

---

### Post by oldfred on 2011-04-17
The OP has a separate /boot partition and when ever installing grub you have to also mount that. (part of why separate /boot is not recommended for standard desktops unless really required).

If separate /boot
$ sudo mount /dev/sda4 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

If doing the full chroot and install grub's boot loader to the MBR, you had to also mount /boot. Many instructions leave that off or have a small footnote somewhere.

Windows will not boot until the windows repairs are made.

---

### Post by Leppie on 2011-04-17
> **zainhuss said:**
> sudo grub-install --recheck /dev/sda sudo update-grubthe top line doesn't seem to be working :L, it says that it isn't a command
so you're missing parts of grub.
issue the following commands:
```
sudo apt-get purge grub-common grub-pc
sudo apt-get install grub-common grub-pc
sudo grub-install --recheck /dev/sda
sudo update-grub

```the last 2 commands probably are not necessary as they should be executed when installing grub2, but it should not harm your system running those commands.

---

### Post by zainhuss on 2011-04-17
> **Leppie said:**
> so you're missing parts of grub.
issue the following commands:
```
sudo apt-get purge grub-common grub-pc
sudo apt-get install grub-common grub-pc
sudo grub-install --recheck /dev/sda
sudo update-grub

```the last 2 commands probably are not necessary as they should be executed when installing grub2, but it should not harm your system running those commands.
done it :)....but i still cany load Win7 :(.

@old fred,I dont have an external CD/DVD drive, as i own a "netbook", so cannot do "recovery".

---

### Post by scott-ian on 2011-04-17
As mentioned in post #53, "then run the boot info script and post the results again"

---

### Post by zainhuss on 2011-04-17
> **scott-ian said:**
> As mentioned in post #53, "then run the boot info script and post the results again"
Here are the results:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 354640 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 354640 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     6,306,311     6,304,264  12 Compaq diagnostics
/dev/sda2    *     20,973,568    21,178,367       204,800  82 Linux swap / Solaris
/dev/sda3          21,178,368   253,962,239   232,783,872   7 HPFS/NTFS
/dev/sda4         253,962,240   293,024,739    39,062,500  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c94ed50d-7529-43b6-9aec-572f32b6c444   ext4                                     
/dev/sda2        f8d060a5-167d-4d64-b305-0aadde9aba8d   swap                                     
/dev/sda3        1E4A51CE4A51A2F7                       ntfs       Windows                       
/dev/sda4        ee3654ed-61e4-4bbc-8ba2-13e24ef870b7   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda1        /boot                    ext4       (rw,commit=600)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set ee3654ed-61e4-4bbc-8ba2-13e24ef870b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux    /vmlinuz-2.6.35-22-generic root=UUID=ee3654ed-61e4-4bbc-8ba2-13e24ef870b7 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=ee3654ed-61e4-4bbc-8ba2-13e24ef870b7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_linux_xen ###
### END /etc/grub.d/11_linux_xen ###

### BEGIN /etc/grub.d/12_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/12_memtest86+_proxy ###

### BEGIN /etc/grub.d/13_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
### END /etc/grub.d/13_os-prober ###

### BEGIN /etc/grub.d/14_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/14_custom ###

### BEGIN /etc/grub.d/15_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/15_custom ###

### BEGIN /etc/grub.d/16_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c94ed50d-7529-43b6-9aec-572f32b6c444
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/16_memtest86+_proxy ###

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .2GB: initrd.img-2.6.35-22-generic
    .1GB: vmlinuz-2.6.35-22-generic

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=ee3654ed-61e4-4bbc-8ba2-13e24ef870b7 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
/dev/sda2       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 130.2GB: initrd.img
 130.2GB: vmlinuz

---

### Post by scott-ian on 2011-04-17
Could you post the output of the command "sudo fdisk -l"

---

### Post by scott-ian on 2011-04-17
What is the output of "sudo fdisk -l"?

---

### Post by Leppie on 2011-04-17
> **oldfred said:**
> The OP has a separate /boot partition and when ever installing grub you have to also mount that. (part of why separate /boot is not recommended for standard desktops unless really required).

If separate /boot
$ sudo mount /dev/sda4 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

If doing the full chroot and install grub's boot loader to the MBR, you had to also mount /boot. Many instructions leave that off or have a small footnote somewhere.

Windows will not boot until the windows repairs are made.
you are right about the seperate boot partition, missed that in the results.
however, he's already in his ubuntu system with a broken grub.

zainhuss, sorry for overlooking that part
issue the following commands in a terminal:
```
sudo mount /dev/sda4 /boot
sudo apt-get purge grub-common grub-pc
sudo apt-get install grub-common grub-pc
sudo grub-install --recheck /dev/sda
sudo update-grub
```

---

### Post by uRock on 2011-04-17
> **scott-ian said:**
> Could you post the output of the command "sudo fdisk -l"

> **scott-ian said:**
> What is the output of "sudo fdisk -l"?

That info is listed here. [http://ubuntuforums.org/showpost.php?p=10688579&postcount=25](http://ubuntuforums.org/showpost.php?p=10688579&postcount=25)

---

### Post by oldfred on 2011-04-17
To get windows to work you have to do repairs. I have a win7 repairCd that I copied to USB. I could not do it from Ubuntu, so I burned a CD and then used the CD to copy itself to the USB. That created a bootable windows repair CD. 

Do you have another computer with a CD/DVD or can you use a friend's?

---

### Post by scott-ian on 2011-04-17
I don't believe that is the problem.  The problem is related to Grub, not the Windows boot loader.

---

### Post by uRock on 2011-04-17
If the OP has already run the **sudo update-grub** command, which he/she claims to ha done, then I agree that the Windows repair disk may be the only way to fix this.

---

### Post by scott-ian on 2011-04-17
> **uRock said:**
> If the OP has already run the **sudo update-grub** command, which he/she claims to ha done, then I agree that the Windows repair disk may be the only way to fix this.
Yes, but that does not seem to be an option.

---

### Post by uRock on 2011-04-17
> **scott-ian said:**
> Yes, but that does not seem to be an option.

It is an option. The OP only has to find a friend willing to help by sharing the proper repair disk, which every Windows user should have a copy of. I am not sure how to place the image on a thumb drive, but I am sure someone can help the OP with that.

---

### Post by oldfred on 2011-04-18
I tried creating a bootable FAT or NTFS partition and extracting files from ISO to flash, but however I did it did not work.

If you want to experiment:
But the ISO has your two key files. The issue will be that the BCD will be wrong, but maybe adding bootmgr will let you boot enough to self repair the BCD.

In the window repair ISO from the neosmart site.
Windows 7 64-bit Repair Disc.iso

I open it with Archive Mounter and find in /boot/ the BCD. That file needs to be copied to /Boot in your win7 partition.
At root of the ISO is bootmgr which is what starts windows booting.
Copy bootmgr to the root of your win7 partition.

Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by zainhuss on 2011-04-18
> **oldfred said:**
> To get windows to work you have to do repairs. I have a win7 repairCd that I copied to USB. I could not do it from Ubuntu, so I burned a CD and then used the CD to copy itself to the USB. That created a bootable windows repair CD. 

Do you have another computer with a CD/DVD or can you use a friend's?

Yes, I have a PC wih a CD/DVD Drive, but it is also running Ubuntu, so will it be possible to copy a Win7 repair disk to USB?

---

### Post by cdeem on 2011-04-18
I am by no means an expert, but I had a similar problem a while back. After a lot of research I found that there is a hidden partition with windows 7 that must be there in order for it to boot. When you install grub2 to the MBR it will point to the hidden partition instead of the partition with the OS on it and boot from there.

From the info you have given it looks to me like you have deleted that partition. You have 2 ext4 partitions and only 1 ntfs(and of course the swap). If this is the case you will need to reinstall Win7. Use the instructions [here]("http://www.ehow.com/how_5231455_avoid-reserved-hidden-partition-windows.html"). That will install win7 with only 1 partition and you can then install you other OS's normally.

---

### Post by ububeginner on 2011-04-18
> **zainhuss said:**
> Yes, I have a PC wih a CD/DVD Drive, but it is also running Ubuntu, so will it be possible to copy a Win7 repair disk to USB?
Is it possible for you to gain access to a computer running Windows 7 or Vista? 
Friend, family, work?
If so, then this should get your Windows repair disk to a bootable USB

[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

I have never tried it with a repair disk but I suspect it should work just as well as with the installation disk.

---

### Post by zainhuss on 2011-04-18
> **ububeginner said:**
> Is it possible for you to gain access to a computer running Windows 7 or Vista? 
Friend, family, work?
If so, then this should get your Windows repair disk to a bootable USB

[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

I have never tried it with a repair disk but I suspect it should work just as well as with the installation disk.
No, my netbook doesn't have a CD/DVD drive.
And yes, one of my friends is using Win7.
Just to let you know, I can still access my Windows folder, from Ubuntu, and i can see the bot folder etc.
Also, there is a folder named "Recovery", so i suspect that my "Recovery Disk" is saved there, as i have a netbook?

Thanks for ur suggestions

---

### Post by ububeginner on 2011-04-18
The recovery folder you see on on your Windows partition is a hidden folder on your windows system. It contains a winre.wim image wich, from what I understand, can be used to create a system restore point in windows, which then would be accessable from the Windows bootloader by pressing F8 before Windows starts.
However, there seems to be a problem with your bootloader. In order to fix that you need to download the Windows recovery CD ISO image from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

The link provided in the my previous post has instructions on how to get that ISO image to a bootable USB, but you need a working Windows 7 or Vista system to do that.

EDIT:
this thread provides instructions on how to make a bootable windows usb using a linux system. (post by piratesnack 04-24-2010)

[http://www.linuxquestions.org/questions/linux-software-2/creating-windows-7-bootable-usb-from-linux-762229/](http://www.linuxquestions.org/questions/linux-software-2/creating-windows-7-bootable-usb-from-linux-762229/)

the instructions are for the installation DVDs but I think they should work for the recovery disks as well.

---

### Post by zainhuss on 2011-04-20
Thnkz for the help.
Will try nd let u know wot happens

---

### Post by oldfred on 2011-04-20
I do not have win7 but wanted a repair USB. I used Ubuntu to create the windows repair CD from neosmart and used that CD to create the USB.

Used win7 repair ISO to create USB. Except I used used xcopy *.* /s/e/f/h/r/x J: where J: was the USB drive.
[http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)

---

### Post by daniix on 2011-11-04
Hi,

have you ever solved this? It happened the same to me.

any help would be appreciated

---

### Post by omid429 on 2012-02-17
I have a similar problem and i am hoping someone can help me. A few weeks ago, I installed 11.10 on my Win7 laptop. Dual boot was working fine. Today however, when I came home and started my laptop, Win7 no longer boots. It freezes on the splash screen. Ubuntu runs fine, but not Win7. I installed the cd and tried to boot from cd to run startup repair, but the disc also freezes at the splash screen. I have read through this post and have tried everything and everything seems to be in working order but Win7 just refuses to start. I can access the partition using Ubuntu as well. One thing I should not is that I I updated Ubuntu today. I logged in, it said there were updates, so I updated. Then restarted my system and now Win7 is stuck. Little help?

---

