---
title: "Boot menu problem"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by jamere on 2010-03-05
Hi all,
I have a dual boot set up on my Acer Aspire One laptop (Win XP and Karmic 9.10), and I've received several new kernel images via Update Manager that don't show on the boot menu list. I'm pretty sure I have Grub2 as the menu displays 1.97 Beta 4. I did a "sudo update-grub" from Terminal and it appeared to run OK as XP and 2.6.31-17,19, and 20 were listed. The menu still shows 2.6.31-16 which I've been booting for some time.

Here's what is displayed after doing "ls /boot/ command in terminal:

> jim@jim-laptop:~$ ls /boot/
abi-2.6.31-16-generic         memtest86+.bin
abi-2.6.31-17-generic         System.map-2.6.31-16-generic
abi-2.6.31-19-generic         System.map-2.6.31-17-generic
abi-2.6.31-20-generic         System.map-2.6.31-19-generic
config-2.6.31-16-generic      System.map-2.6.31-20-generic
config-2.6.31-17-generic      vmcoreinfo-2.6.31-16-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-17-generic
config-2.6.31-20-generic      vmcoreinfo-2.6.31-19-generic
grub                          vmcoreinfo-2.6.31-20-generic
initrd.img-2.6.31-16-generic  vmlinuz-2.6.31-16-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-17-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-20-generic

anyone have an idea why the new kernels aren't showing up in boot menu?

Thanks much for any help or info.

---

### Post by swoll1980 on 2010-03-05
> **jamere said:**
> Hi all,
I have a dual boot set up on my Acer Aspire One laptop (Win XP and Karmic 9.10), and I've received several new kernel images via Update Manager that don't show on the boot menu list. I'm pretty sure I have Grub2 as the menu displays 1.97 Beta 4. I did a "sudo update-grub" from Terminal and it appeared to run OK as XP and 2.6.31-17,19, and 20 were listed. The menu still shows 2.6.31-16 which I've been booting for some time.

Here's what is displayed after doing "ls /boot/ command in terminal:



anyone have an idea why the new kernels aren't showing up in boot menu?

Thanks much for any help or info.

What kernel is it that you want to run? You would have only gotten one Linux kernel image, and some headers in the update.

---

### Post by jamere on 2010-03-05
Thanks for the reply. I want to run the newest kernel (2.6.31-20) that came through in updates today. I seem to get only old items in the menu list. The boot menu list never seems get updated with newer kernels to choose. Kernels 16, 17, 19, and 20 are out there. I've been running 16 and have never used the others because they don't show up on the menu.

Hope I'm making myself clear.;)  Have never had to deal with Grub before.

Thanks again.

---

### Post by jamere on 2010-03-05
Here's the output from "sudo update-grub" command:

```
jim@jim-laptop:~$ sudo update-grub
[sudo] password for jim: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
Found Ubuntu 9.10 (9.10) on /dev/sda7
done
```

---

### Post by presence1960 on 2010-03-05
If you have GRUB 2 there is no menu.lst used. Your sudo update-grub detected the kernels- they should appear on your GRUB menu at boot. If they do not I need more info about your setup & boot process.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by jamere on 2010-03-06
Presence1960, thanks much for your reply!

This is a guess on my part, but I think that Grub is probably filled with old entries of different versions of Xubuntu, Ubuntu 9.04, and 9.10. Here is a quick background FYI:

As I said before, I have an Acer Aspire One Netbook with a built-in Qualcomm USB modem for handling broadband wireless. To make a long story short, my netbook won't connect in Ubuntu without first booting in XP (to load the Qualcomm modem firmware) and then re-booting in 9.10 without "powering off". This is the ONLY way I can connect using any *buntu flavor. This is apparently a known problem with the Qualcomm modem and I guess any laptop using it. I tried all the different *buntu flavors hoping to find one that would work with my Netbook without having to first boot in XP.

The only things that need to be preserved are:
Windows XP Home Edition
Windows Vista  (Loader)
Ubuntu 9.10 and newest Kernel (2.6.31-20)
I've been using Kernel (2.6.31-16)

Hope this makes sense! :D

With the above in mind, here are the Script results:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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
Disk identifier: 0x342a7ce8

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,779,263    16,777,216  12 Compaq diagnostics
/dev/sda2    *     16,779,264   139,614,962   122,835,699   7 HPFS/NTFS
/dev/sda3         139,620,915   312,576,704   172,955,790   5 Extended
/dev/sda5         139,621,041   222,243,209    82,622,169  83 Linux
/dev/sda6         301,411,593   307,355,579     5,943,987  82 Linux swap / Solaris
/dev/sda7         222,243,273   298,070,009    75,826,737  83 Linux
/dev/sda8         298,070,073   301,411,529     3,341,457  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4C921EDC921ECA7A                       ntfs       PQSERVICE                     
/dev/sda2        E62688E52688B7D7                       ntfs       ACER                          
/dev/sda5        1777a28b-cc04-44fd-9b79-a9aafabcbf9e   ext4                                     
/dev/sda6        78249822-f25f-40ca-a971-ef2ac2df4fa2   swap                                     
/dev/sda7        b69c99b5-e4c6-4279-879d-c51ea138f629   ext4                                     
/dev/sda8        41ff6063-641b-49c2-aec6-a7657a6fae02   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
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
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4c921edc921eca7a
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e62688e52688b7d7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=78249822-f25f-40ca-a971-ef2ac2df4fa2 none            swap    sw              0       0

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,9)
search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set b69c99b5-e4c6-4279-879d-c51ea138f629
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4c921edc921eca7a
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e62688e52688b7d7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set e5842692-bcbf-4987-84eb-38d8381ca029
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=e5842692-bcbf-4987-84eb-38d8381ca029 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set e5842692-bcbf-4987-84eb-38d8381ca029
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=e5842692-bcbf-4987-84eb-38d8381ca029 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set e5842692-bcbf-4987-84eb-38d8381ca029
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 1777a28b-cc04-44fd-9b79-a9aafabcbf9e
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1777a28b-cc04-44fd-9b79-a9aafabcbf9e ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b69c99b5-e4c6-4279-879d-c51ea138f629 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=41ff6063-641b-49c2-aec6-a7657a6fae02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 113.7GB: boot/grub/core.img
 113.7GB: boot/grub/grub.cfg
 113.7GB: boot/initrd.img-2.6.31-14-generic
 113.7GB: boot/initrd.img-2.6.31-16-generic
 113.7GB: boot/vmlinuz-2.6.31-14-generic
 113.7GB: boot/vmlinuz-2.6.31-16-generic
 113.7GB: initrd.img
 113.7GB: initrd.img.old
 113.7GB: vmlinuz
 113.7GB: vmlinuz.old 
```

---

### Post by presence1960 on 2010-03-06
You have 2 ubuntu installs, sda5 & sda7. Your GRUB is pointing to sda7, but sda5 has the newer kernels. I would boot from the Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo mount /dev/sda5 /mnt
```

Then in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Reboot without the Live CD and you should be good to go. If it works fine I would delete that sda7 partition with the other Ubuntu install through gparted.

---

### Post by gdea73 on 2010-03-06
Did you install from the CD or with "wubi"? I had issues using wubi, because it won't format the disk and it will be unsu pported filesystem

---

### Post by jamere on 2010-03-06
gdea73: I didn't install with "wubi"

presence1960: Thanks for your replies and insight on this matter! After giving it some thought, I think I'll wait and hope for the Qualcomm modem issue to be resolved in the new Ubuntu release (10.4), when hopefully I can boot independently of Windoze! Until I can see that the modem issue is fixed, I have to maintain connectivity with Windows and have to make sure I don't screw up Windows messing around with this boot issue. Hopefully soon, I can just blow away Windoze and devote the entire HD to Ubuntu!

Thanks again for your help.:)

---

