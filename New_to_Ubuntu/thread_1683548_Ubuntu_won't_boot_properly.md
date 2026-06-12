---
title: "Ubuntu won't boot properly"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by floyd741 on 2011-02-07
So I just started using Linux about a month ago and so far learning to work with it hasn't really been a problem. Well today I got the popup window telling me that there were updates ready to install, so I just went ahead and let it do what it had to do since I'm not of sufficient knowledge to do otherwise. After it restarted it didn't go to the login screen like I would have expected it to do. Instead I got a prompt titled "Ubuntu 10.10 (computer name) ttyl" or something like that. I was prompted to enter my login then password, then I was just left there in what I can only describe as a commend prompt (like working in Terminal). From there I'm lost, I'm not sure what exactly I did wrong as far as the updates go, I do remember it saying that a few couldn't be installed and they were named something like "Ubuntu kernel" or something I'm not really sure and I can't really check anymore. Luckily I have a second hard drive with Windows 7 installed so if I have any problems I already know how to fix them but I'm really just lost with the Linux hard drive.

Any help on how to fix this would be excellent as my Linux HD is my main drive, the Win7 HD is completely useless for normal stuff since I use it only for music production. Again, I would really appreciate any help on how to fix this.

---

### Post by JLangford on 2011-02-07
At the login screen, on the bar along the bottom of the screen, at some point during the login process (can't remember whether its when you choose a user or enter your password) there is a little box asking you what you wan't to boot into, it should list the terminal, failsafe ubuntu and ubuntu.

At least thats what happens with mine. I hope I helped.

---

### Post by drs305 on 2011-02-07
Try booting one of the older kernels and see if it works. If you don't get the Grub2 menu screen, hold down the SHIFT key during the early stage of the boot and the menu should appear.

---

### Post by Dutch70 on 2011-02-07
If you do get back to the dos like place(tty1) , try hitting cntrl>alt>F7 together.

---

### Post by floyd741 on 2011-02-07
@JLangFord That would be useful but the thing is I never get to the login screen. As soon as it boots it goes straight to the prompt.

@drs305 Booting older kernels does nothing, unfortunately. They all take me to the same screen.

@Dutch70 Alright well that did something (ctrl + alt + F7) but not anything that really helped me get to the login screen. The first time I did it I got big wall of text that ended up saying something like "No such file or directory found" then I tried again and got less text, one line saying something ArmorAPP (I think, I'm trying to remember all this from just seeing it for a short time) then the other line said something similar without the ArmorAPP and both said [OK] at the end. Unfortunately, neither of these have gotten me any closer to booting to the login screen.

Thanks a lot for the help but this issue still remains unsolved :( If nothing works would I be able to reinstall Ubuntu while leaving all of my files in place?  I know Windows does this but I'm not sure about Linux.

EDIT:

I tried running the latest kernel (and an older one) in recovery mode, then I tried running in failsafe graphics mode since earlier, that had gotten me to the login screen amd everything was fine save for the fact that I had no internet (no connection shown). I tried doing that again but now when I try failsafe graphics mode I get  quick flash of text at the bottom of the screen saying that it won't run because it was just attempted 30 seconds ago. So I can't even do that now :( I figured if I at least got there I could try JLangFords suggestion but I guess not.

---

### Post by floyd741 on 2011-02-07
Anyone else? I really need help, nothing I've tried is working and I have a lot of work to finish but it's impossible to do anything without access to any of it. I'm sure this must have happened to somebody at some point I mean it seems like it should be an easy issue but of course with my limited knowledge I really don't know. I've tried installing recover in the prompt but that does nothing, failsafe mode doesn't boot, ctrl+alt+F7 has been useless thus far, reinstalling Ubuntu doesn't seem to be an option since I can't find a way to reinstall while leaving the old files intact. I understand I'm not the only person here who needs help but I have nowhere else to get it and I just really need this fixed asap.

---

### Post by presence1960 on 2011-02-07
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by floyd741 on 2011-02-07
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,935,429,631 1,935,427,584  83 Linux
/dev/sda2       1,935,431,678 1,953,523,711    18,092,034   5 Extended
/dev/sda5       1,935,431,680 1,953,523,711    18,092,032  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,279,609   488,279,547   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        81e3bf82-5f91-4cdd-8bf0-12c347a95b92   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        81fe92e7-2dfb-44ce-a346-6275ae24b597   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2A1EFE241EFDE8A9                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 81e3bf82-5f91-4cdd-8bf0-12c347a95b92
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2a1efe241efde8a9
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=81fe92e7-2dfb-44ce-a346-6275ae24b597 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 214.8GB: boot/grub/core.img
 214.9GB: boot/grub/grub.cfg
 102.2GB: boot/initrd.img-2.6.35-22-generic
 125.0GB: boot/initrd.img-2.6.35-24-generic
 125.0GB: boot/initrd.img-2.6.35-25-generic
 215.0GB: boot/vmlinuz-2.6.35-22-generic
 215.0GB: boot/vmlinuz-2.6.35-24-generic
 215.0GB: boot/vmlinuz-2.6.35-25-generic
 125.0GB: initrd.img
 125.0GB: initrd.img.old
 215.0GB: vmlinuz
 215.0GB: vmlinuz.old

```

That's what I got from results.txt

---

### Post by presence1960 on 2011-02-07
Everything looks OK except I noticed this:

```
=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# [COLOR="Red"]/ was on /dev/sdb1 during installation
UUID=81e3bf82-5f91-4cdd-8bf0-12c347a95b92 /[/COLOR]               ext4    errors=remount-ro 0       1
# [COLOR="Red"]swap was on /dev/sdb5 during installation
UUID=81fe92e7-2dfb-44ce-a346-6275ae24b597 none            swap    sw              0       0[/COLOR]


```

It seems your ubuntu disk was second in the boot order when you installed it and then you switched the order. technically it should not matter because the devices are named by UUID #. But since I could find nothing else you could try resetting GRUB 2 on the MBR.

Boot the Ubuntu Live CD/USB. Choose try ubuntu. When the desktop loads open a terminal and run ```
sudo mount /dev/sda1 /mnt
```This will mount the ubuntu / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```When complete reboot without Live CD/USB and see what happens. hopefully you will get the GRUB menu.

---

### Post by floyd741 on 2011-02-07
Unfortunately, that didn't actually do anything as far as I can tell. Getting the GRUB menu has never been the problem, I get it every time I turn on my computer. The problem is that no matter which kernel I load I'm taken straight to a prompt.

When I tried the above directions all I got in Terminal was "Installation finished. No error reported." It didn't really make an effect on boot though, still get the prompt.

---

### Post by presence1960 on 2011-02-08
> **floyd741 said:**
> Unfortunately, that didn't actually do anything as far as I can tell. Getting the GRUB menu has never been the problem, I get it every time I turn on my computer. The problem is that no matter which kernel I load I'm taken straight to a prompt.

When I tried the above directions all I got in Terminal was "Installation finished. No error reported." It didn't really make an effect on boot though, still get the prompt.

Sorry for the delay, I retired for the night. I did say that everything looks OK, other than the disk designation in /etc/fstab. I also said that should not matter because the devices are named by UUID #. Since everything else looked OK I suggested that to give it a shot because it would not harm your set up. At the very worst nothing would happen, which is exactly what transpired. I have no ideas about your problem maybe someone else will see something I did not.

---

