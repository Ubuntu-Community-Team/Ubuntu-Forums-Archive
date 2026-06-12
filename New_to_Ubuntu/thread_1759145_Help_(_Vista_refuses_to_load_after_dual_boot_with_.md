---
title: "Help :( Vista refuses to load after dual boot with Ubuntu - Grub error!"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by electromagnetic on 2011-05-15
HI everyone!

this is my 1st post here . 
Being a Microsoft user since birth but got inspired by the whole linux thing , so installed the latest version Ubuntu 11.04 in separate partition(made it my self for the 1st time(9GB)).The partition including Vista is apprx 126 GB.
Installation went smoothlty . and when i tried restarting my laptop, It gave Grub error and nothing else appears on screen.Vista or Ubuntu is not loaded.

---> I searched some forums for help and found this post:[http://ubuntuforums.org/showthread.php?t=1271409&page=2]("http://ubuntuforums.org/showthread.php?t=1271409&page=2")

when i try to type "sudo grub" in terminal it gives error "Command not found"
I even trued "sudo /sbin/grub" but no gain:(

I have loads of data in Vista Drive. Even though i have transferred some of it through booting Via Ubuntu cd, but I need it all normal.. PLEASE HELP! I have my study programs like matlab installed there.

I am WAITING for ur reply :)--pls keep it simple since i am new 
Regards, Electro

---

### Post by TeoBigusGeekus on 2011-05-15
Probably grub wasn't installed properly.
Look at [this]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2") - 3rd method, using chroot.

---

### Post by Hedgehog1 on 2011-05-15
We need to get a look at your install to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by electromagnetic on 2011-05-15
> **Hedgehog1 said:**
> We need to get a look at your install to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS
I tried to do as mentioned above, running the following command on terminal:
```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script055*.sh 

```The results were placed in a file Results.txt on desktop.I got the following results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Fat16
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'swsuspend'

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   246,482,943   246,482,881   7 HPFS/NTFS
/dev/sda2         289,163,264   312,571,903    23,408,640   7 HPFS/NTFS
/dev/sda3         246,484,990   289,163,263    42,678,274   5 Extended
/dev/sda5         276,592,640   282,871,807     6,279,168  82 Linux swap / Solaris
/dev/sda6         270,307,328   276,590,591     6,283,264  82 Linux swap / Solaris
/dev/sda7         246,484,992   264,019,967    17,534,976  83 Linux
/dev/sda8         264,022,016   270,292,991     6,270,976  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CC147F8B147F7774                       ntfs                                     
/dev/sda2        AAAE82AFAE82739B                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        53fe7366-3d5b-4212-ac50-c7c807bbc4e5   swsuspend                                
/dev/sda6        351d3103-86e5-4035-9235-9902dac75d12   swap                                     
/dev/sda7        3069d721-b5be-4ef3-9615-d3b030d858a6   ext4                                     
/dev/sda8        cef201c5-17db-4fff-bf25-382b76c85dc3   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 3069d721-b5be-4ef3-9615-d3b030d858a6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 3069d721-b5be-4ef3-9615-d3b030d858a6
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 3069d721-b5be-4ef3-9615-d3b030d858a6
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3069d721-b5be-4ef3-9615-d3b030d858a6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 3069d721-b5be-4ef3-9615-d3b030d858a6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3069d721-b5be-4ef3-9615-d3b030d858a6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 3069d721-b5be-4ef3-9615-d3b030d858a6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 3069d721-b5be-4ef3-9615-d3b030d858a6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CC147F8B147F7774
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AAAE82AFAE82739B
    drivemap -s (hd0) ${root}
    chainloader +1
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=cef201c5-17db-4fff-bf25-382b76c85dc3 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 134.9GB: boot/grub/core.img
 131.0GB: boot/grub/grub.cfg
 127.7GB: boot/initrd.img-2.6.38-8-generic
 133.1GB: boot/vmlinuz-2.6.38-8-generic
 127.7GB: initrd.img
 133.1GB: vmlinuz

```Thanks for the timely response...!What to do next now?

---

### Post by Hedgehog1 on 2011-05-15
Hello again Electro!

You will need to do these following steps booted from your Natty/11.04 LiveCD/LiveUSB to load the correct version of grub2 on your hard drive.

```
sudo mount /dev/sd**a7** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

Once these commands are done, you should be able to boot into either Vista or Ubuntu.

**As a separate matter**, you have 3 swap partitions, but you only need one. Once you are booting correctly, we can help you remove the two extra ones and reclaim that disk space for Vista or Ubuntu.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-15
Wait - just saw there is one more thing wrong.

Before you reboot, you will also need to fix your **/etc/fstab** (**F**ile **S**ystem **TAB**le) file.

```
sudo mount /dev/sd**a7** /mnt
```
ignore any error from running this command a second time.

```
gksudo gedit /mnt/etc/fstab
```

[COLOR="Red"]and change this line:[/COLOR]

/dev/sda8       /               ext4    errors=remount-ro 0       1

[COLOR="red"]to this line:[/COLOR]

UUID=3069d721-b5be-4ef3-9615-d3b030d858a6   / ext4   errors=remount-ro 0 1

[COLOR="red"]and then save the file and exit the editor.[/COLOR]

**Now** you can reboot.

***The Hedge***

:KS

---

### Post by electromagnetic on 2011-05-15
> **Hedgehog1 said:**
> Wait - just saw there is one more thing wrong.

Before you reboot, you will also need to fix your **/etc/fstab** (**F**ile **S**ystem **TAB**le) file.

```
sudo mount /dev/sd**a7** /mnt
```ignore any error from running this command a second time.

```
gksudo gedit /mnt/etc/fstab
```[COLOR=Red]and change this line:[/COLOR]

/dev/sda8       /               ext4    errors=remount-ro 0       1

[COLOR=red]to this line:[/COLOR]

UUID=3069d721-b5be-4ef3-9615-d3b030d858a6   / ext4   errors=remount-ro 0 1

[COLOR=red]and then save the file and exit the editor.[/COLOR]

**Now** you can reboot.

***The Hedge***

:KS

I have done everything as mentioned, but running the last command```
gksudo gedit /mnt/etc/fstab
``` gave me  almost 5-6 times the warning:
```
(gedit:9707): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.U53MVV': No such file or directory

```I checked out by loading the fstab file again . The line is edited to the mentioned one though. dont know why the warnings. 
I am restarting my laptop, lets see what happens-- Afterall , hopes keep us alive :)

---

### Post by electromagnetic on 2011-05-15
Hurrah! I have my Vista back and its working Normal!!\\:D/ Thanks man@Hedgehog1 

But there is a little problem with ooBuntoo. After i booted  in  it, some alterations have been done. For Instance I cannot figure out any top menu (System,Applications,Firefox launch icon-on top), The down task bar is also gone. the desktop appears to have an less opaque mirror image merged with it ,I mean the icons are 2 each, with 2nd just an image,(2nd ones not click-able).

Also , i cannot see any of the options(close, minimize , maximize)on the windows, if I open any icon. I wished to attach a print screen copy of it, but could not figure how to open paint there.

---

### Post by Hedgehog1 on 2011-05-15
To set up your Ubuntu installed properly, you will have to **reinstall** from the LiveCD/LiveUSB'.

Please choose the **very last option called 'Something Else'**;
[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

You then need to define /dev/sda7 as your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

PLEASE BE SURE TO INSTALL YOUR BOOTLOADER ON /dev/sda (not sda1 or 2 or 3, just /dev/sda)

This will overwrite /dev/sda7, and leave everything else alone on your PC.

***The Hedge***

:KS

p.s. If you have any data in /dev/sda7, please back it up before you do this.

---

### Post by electromagnetic on 2011-05-16
Viola ! I got everything back to Normal :) Thank you very Much Hedghog1 and all for the support.:)

Re installed Ubuntu 11.04 from CD, and did the above mentioned Disk setting and Its working pretty  good.
One more thing: 
Restarting Ubuntu after installation gave teh Error that Hardware does not have all the features for Unity, try Classic mode instead .

How do i switch to classic mode, i donot see any options while starting.
And Do i have to install all applications like Matlab and other programs with Linux Compatibility? coz the matlab installed in Windows Vista wont work.

---

### Post by Hedgehog1 on 2011-05-16
Here is a link to your UI options: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

You will need to reload matlab (I think it's a choice of things like 'FreeMat' and 'GNU Octave' in the Ubuntu Software Center).


***The Hedge***

:KS

p.s. Once you get the correct video drivers loaded, Unity should also work for you.

---

### Post by electromagnetic on 2011-05-16
just wanted to say thanks O:), and is there any option where u get to know wether u are running Unity or Classic?

---

### Post by astex on 2011-05-16
There is a program called wine which is capable of running windows programs, but by and large, windows programs will not run on linux and linux programs will not run on windows.  There are several free adaptations of matlab you might try like maple or octave.

Your computer doesn't seem to support hardware acceleration.  At the login screen, click other login, type in your name, and on the bottom bar click 'classic 2D.'

---

