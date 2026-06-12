---
title: "Multiple Distros Grub2"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by JASONFUSARO on 2011-07-12
Finally!!!


Now to not screw things up


After a couple of weeks of rebooting, changing, googling, more rebooting, more modifying,
more googling, hairpulling, swearing, punching the desk I think I finally have accomplished
a multiboot system.

Now to keep it in it's pristine state!!!

I started by completely reinstalling Windows Vista (Square One)

then I created my partitions although after searching Google to determine 
why there is a limit to only 16 I ran into a dead end so 16 it stands for now

I then began installing Distros and also put a few on USB.
USB Puppy, Toorox and ArchBang these seem to be the fastest booting under
a minute !!!

My partition scheme is as follows
```

[root@archbang ~]# blkid
[SIZE="1"][FONT="Arial"][SIZE="1"][FONT="Book Antiqua"][SIZE="1"][FONT="Courier New"][CENTER][LEFT][FONT="Fixedsys"][SIZE="1"][FONT="System"][SIZE="2"][SIZE="4"][SIZE="1"]/dev/sda1: LABEL="WindowsVista" UUID="C65A6C105A6C0013" TYPE="ntfs" 
/dev/sda2: LABEL="MY_BOOT_GRUB" UUID="935626ef-4817-48f4-b690-f6bbaeea7df6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="49b2f37d-e3af-4a16-b7d3-be022adf39b8" TYPE="swap" 
/dev/sda5: LABEL="Distro-1_To Be D" UUID="196a9858-cc5e-4e14-b9e9-5ca5e21df982" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Chakra" UUID="ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda7: LABEL="UbuntuStudio64" UUID="f3a87410-015f-4d94-844e-4ec276cfedbc" TYPE="ext4" 
/dev/sda9: LABEL="CtkArch64" UUID="0920168c-5419-4412-8134-713ed2c3814c" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda10: UUID="ee7be487-f281-4072-9af3-72612c9a684c" TYPE="ext3" LABEL="ArchBang" 
/dev/sda11: UUID="52777f50-fd1d-42d8-9a17-5ad1ddf0b794" TYPE="ext3" SEC_TYPE="ext2" LABEL="UltimateEdition" 
/dev/sda12: LABEL="Toorox Gnome 64" UUID="91033a5b-7407-4a80-b1aa-07ff96202ee3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="Puppy" UUID="856f3983-f4e9-45da-b500-e199fefbbad1" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda14: LABEL="Zorin" UUID="06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda15: LABEL="Linux From Scrat" UUID="20610f96-41af-401a-956e-d077128f64d3" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda16: LABEL="Shared" UUID="9fb6e192-7b65-4aed-9922-cbc1a94eed6e" TYPE="ext2" 
/dev/sda8: LABEL="Distro-4 To Be d" UUID="b35a2191-0991-4040-8023-1bef352cf212" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="ReadyBoost-SysUtilities" UUID="8A9C26F89C26DE87" TYPE="ntfs" [/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/FONT][/LEFT][/CENTER][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE]




[root@archbang /]# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029370

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   133226495    66612224    7  HPFS/NTFS
/dev/sda2       133226496   133636095      204800   83  Linux
/dev/sda3       133636096   143876095     5120000   82  Linux swap / Solaris
/dev/sda4       143878201   976773119   416447459+   f  W95 Ext'd (LBA)
/dev/sda5       143878203   164360191    10240994+  83  Linux
/dev/sda6       164361078   197124095    16381509   83  Linux
/dev/sda7       197126144   248326143    25600000   83  Linux
/dev/sda8       248328192   340488191    46080000   83  Linux
/dev/sda9       340490240   391690239    25600000   83  Linux
/dev/sda10      391692288   453132287    30720000   83  Linux
/dev/sda11      453134336   504334335    25600000   83  Linux
/dev/sda12      504336384   555536383    25600000   83  Linux
/dev/sda13      555538432   606738431    25600000   83  Linux
/dev/sda14      606740480   698900479    46080000   83  Linux
/dev/sda15      698902528   801302527    51200000   83  Linux
/dev/sda16      801304576   976773119    87734272   83  Linux

Disk /dev/sdb: 7969 MB, 7969177600 bytes
246 heads, 62 sectors/track, 1020 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15557039     7778489    7  HPFS/NTFS
[root@archbang /]# 


```


[COLOR="Red"]**QUESTION REQUIRING HELP**[/COLOR]

[B][SIZE="3"]What I would like help with is.

1.) The simplest, most efficient backup plan and software to be a safe as possible.
	a) It must be able to restore my system regardless of the fact of whether or not
	   I have any distros working or running.
	b) I won't need a password or be root to recover it.
	c) The first time I do a recover, as a practice run there is absolutely zero
	   posibillity that it will not screw things up.[/SIZE][/B]



Some of the following posts will be purely informational mainly to be of possible help to other users
who are experiencing difficulties of the likes which I have had.


I have been using ArchBang which I have installed on partition #10, which has been a super help mainly because it has under accessories Thunar File Manager (root) which is there from the install no need of downloading!

If you open 2 it allows you to easily make backup copies, edit, change permissions, all within a GUI. Your password is
required to start it but no more after that. 

#################
AND IT IS EXTREMELY IMPORTANT TO READ EVERYTHING BEFORE CLICKING THE MOUSE, MAKE SURE YOU KNOW EXACLTY WHAT IS BEING CHANGED BECAUSE THINGS CAN GET REALLY MESSED UP, CAN YOU GUESS HOW I KNOW THIS??
#################

It also has shortcut keys already set up by using the windows key on the keyboard it's refered to as super and another key, for instance super + t starts a terminal, super + f starts filemanager, not Thunar as root
the normal file manager.

I have been using it as my main distro to run update-grub which in version 2 is actually grub-mkconfig.

The first thing I did after installing was checked which version of grub was running and then upgraded to Grub2.

It uses the pacman file manager do get software from repositories.

for instance

```

[root@archbang BOOT_INFO]# pacman -Ss grub

core/grub 0.97-17 [0.44 MB] (base)
    A GNU multiboot boot loader
extra/grub2-bios 1:1.99-3 [0.64 MB] [installed]
    The GNU GRand Unified Bootloader version 2 - Built for PC BIOS
extra/grub2-common 1:1.99-3 [1.22 MB] [installed]
    The GNU GRand Unified Bootloader version 2 - Files common for all platforms
extra/grub2-efi-i386 1:1.99-3 [0.62 MB]
    The GNU GRand Unified Bootloader version 2 - i386 UEFI version
extra/grub2-efi-x86_64 1:1.99-2 [0.62 MB] [installed]
    The GNU GRand Unified Bootloader version 2 - x86_64 UEFI version
community/python-markdown 2.0.3-5 [0.07 MB]
    Python implementation of John Gruber's Markdown.


gives a list of what is out there

-Ss   tells pacman to search for stuff with reference to grub


[root@archbang BOOT_INFO]# packer grub

using packer will give this

0 core/grub 0.97-17 [0.44 MB] (base)
    A GNU multiboot boot loader
1 extra/grub2-bios 1:1.99-3 [0.64 MB] [installed]
    The GNU GRand Unified Bootloader version 2 - Built for PC BIOS
2 extra/grub2-common 1:1.99-3 [1.22 MB] [installed]
    The GNU GRand Unified Bootloader version 2 - Files common for all platforms
3 extra/grub2-efi-i386 1:1.99-3 [0.62 MB]
    The GNU GRand Unified Bootloader version 2 - i386 UEFI version
4 extra/grub2-efi-x86_64 1:1.99-2 [0.62 MB] [installed]
    The GNU GRand Unified Bootloader version 2 - x86_64 UEFI version
5 community/python-markdown 2.0.3-5 [0.07 MB]
    Python implementation of John Gruber's Markdown.
6 aur/grub-gfx 0.97-11
    A GNU multiboot boot loader 
7 aur/kgrubeditor 0.8.5-2
    A KDE 4 GUI for GRUB 
8 aur/startupmanager 1.9.13-4
    GUI app for changing the settings of GRUB, GRUB2, Usplash and Splashy 
9 aur/grub-gfx-themes 0.1-1
    A collection of grub graphical boot themes. 
10 aur/grubng 1.0-1
    (Wikia's) Next Generation Web Crawling Bot 
11 aur/grub2-gfxmenu-overlay 20090719-1
    Overlay/graphical files for grub2-gfxmenu. 
12 aur/grub2-theme-aftermathblue 0.02.1-2
    Deep blue grub2-gfxmenu theme, Arch branded (1024x768) 
13 aur/grub2-theme-archsphere 0.1.1-2
    Sleek grub2-gfxmenu theme, Arch branded (1024x768) 
14 aur/grub2-theme-distroballs 0.1.1-2
    Distro balls grub2-gfxmenu theme, Arch branded (1024x768) 
15 aur/grub2-theme-elegantarch 0.1.1-2
    Elegant grub2-gfxmenu theme, Arch branded (1024x768) 
16 aur/grub2-theme-planeplant 0.1.1-2
    Artistic grub2-gfxmenu theme, Tux branded (1024x768) 
17 aur/grub2-theme-simplyblack 0.1.1-2
    Simple black grub2-gfxmenu theme, Arch branded (1024x768) 
18 aur/grub2-theme-ubuntuglow 0.1.1-2
    Simple grub2-gfxmenu theme, Ubuntu branded (1024x768) 
19 aur/grub4dos 0.4.5b_20110220-1
    A GRUB boot loader support menu on windows(fat,ntfs)/linux(ext2,3,4) 
20 aur/multimarkdown-git 20100216-1
    Expanded perl version of John Gruber's original Markdown 
21 aur/grub2-icons-circlestarts 0.9-1
    More complete extra icon set for grub2-gfxmenu. 
22 aur/burg-bzr 1844-2
    A brand-new boot loader based on GRUB. 
23 aur/ruby-rdiscount 1.6.8-1
    Fast Implementation of Gruber's Markdown in C. 
24 aur/grubinvaders 1.0.0-1
    multi boot compliant game for i386 and compatible x86_64. 
25 aur/grub2-efi-bzr 3381-1
    The GNU GRand Unified Bootloader version 2 for UEFI systems - BZR Development Version with grub-extras - Dummy pkgname - Edit PKGBUILD for actual pkgname 
26 aur/python3-markdown 2.0.3-2
    Python 3 implementation of John Gruber's Markdown. 
27 aur/grub2-bios-bzr 3381-1
    The GNU GRand Unified Bootloader 2 - Built for i386 BIOS - BZR Main Trunk with grub-extras 
28 aur/burg-emu 1844-2
    A brand-new boot loader based on GRUB.(emu) 
29 aur/grub-customizer 70-1
    GUI for customizing GRUB2 or BURG 
30 aur/kcm-grub2 1.3-1
    Manages the most common settings of GRUB2 
31 aur/grub4dos-svn 149-1
    A GRUB boot loader support menu on windows(fat,ntfs)/linux(ext2,3,4) 
32 aur/grub2-editor 0.5.0-1
    A KDE4 control module for configuring the GRUB2 bootloader. 
33 aur/grub-legacy-fedora-git 20110710-2
    Fedora's grub-legacy fork - compiled for BIOS systems 
34 aur/grub-legacy-efi-fedora 20110710-1
    Fedora's grub-legacy fork - compiled for UEFI systems 
35 aur/grub2-chainload 0.1-1
    Automatly generate chainload entries for Grub2 



after seeing what you want to download just enter the number and
it will do the rest

Type numbers to install. Separate each number with a space.
Numbers: 


```
 


after upgrading to grub2 I made backups of all my directories

/boot/grub   etc/grub.d    etc/default


then I wracked my brains trying to get things going


what I discovered

this is etc/default the original

```


GRUB_DEFAULT=0
GRUB_TIMEOUT=45
GRUB_DISTRIBUTOR="Arch Linux"
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable Hidden Menu, and optionally hide the timeout count
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you want GRUB to pass to the Linux kernel the old parameter 
# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx" 
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

# Uncomment and set to the desired menu colors.  Used by normal and wallpaper 
# modes only.  Entries specified as foreground/background.
GRUB_COLOR_NORMAL="light-blue/black"
GRUB_COLOR_HIGHLIGHT="light-cyan/blue"

# Uncomment one of them for the gfx desired, a image background or a gfxtheme
#GRUB_BACKGROUND="/path/to/wallpaper"
#GRUB_THEME="/path/to/gfxtheme"

# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"


```



**this is etc/default NOW**

```

GRUB_DEFAULT=0
GRUB_TIMEOUT=55
GRUB_DISTRIBUTOR="Arch Linux"
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER="xfalse"

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable Hidden Menu, and optionally hide the timeout count
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#####################    ORIGINAL    GRUB_GFXMODE=auto
GRUB_GFXMODE="640x480"

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX="keep"

# Uncomment if you want GRUB to pass to the Linux kernel the old parameter 
# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx" 
GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY="true"

# Uncomment and set to the desired menu colors.  Used by normal and wallpaper 
# modes only.  Entries specified as foreground/background.
GRUB_COLOR_NORMAL="black/black"
GRUB_COLOR_HIGHLIGHT="white/red"

# Uncomment one of them for the gfx desired, a image background or a gfxtheme
GRUB_BACKGROUND="/etc/grub.d/58844.jpg"
#GRUB_THEME="/path/to/gfxtheme"

# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"


```


grub.cfg  BEFORE   ie. when nothing was working

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod part_msdos
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

set menu_color_normal=light-blue/black
set menu_color_highlight=light-cyan/blue

insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_input console
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Arch Linux, with Linux vmlinuz26' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/ee7be487-f281-4072-9af3-72612c9a684c ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26.img
}
menuentry 'Arch Linux, with Linux vmlinuz26 Fallback' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/ee7be487-f281-4072-9af3-72612c9a684c ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" --class memtest86 --class gnu --class tool {
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
  linux16 ($root)/boot/memtest86+/memtest.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

### BEGIN /etc/grub.d/41_NEW_Chakra_Distro ###
menuentry 'TinyCore' {
	
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set root=88627fac-5ffd-44a4-90cc-cd92f680d547
	linux	/boot/bzImage root=/dev/disk/by-uuid/88627fac-5ffd-44a4-90cc-cd92f680d547 ro  quiet
	initrd	/boot/init.gz quiet  tce=sda5 swapfile=sda3 home=sda3 opt=sda3 safebackup showapps vga=792 superuser waitusb=5:UUID="88627fac-5ffd-44a4-90cc-cd92f680d547" tce=UUID="88627fac-5ffd-44a4-90cc-cd92f680d547"
}
menuentry 'Chakra Linux' {
	set root='(hd0,msdos1,bsd6)'
	#search --no-floppy --fs-uuid --set root=ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro  quiet
	initrd	/boot/kernel26.img
}
menuentry 'Zorin' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)/dev/sda14'
	#search --no-floppy --fs-uuid --set root=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux	/boot/vmlinuz-2.6.35-25-generic root=/dev/sda14 #root=/dev/disk/by-uuid/06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro  quiet
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'CtkArch64' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)/dev/sda9'
	#search --no-floppy --fs-uuid --set root=0920168c-5419-4412-8134-713ed2c3814c
	linux	/boot/vmlinuz26 ##root=/dev/sda9 #isk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro  quiet
	initrd	/boot/kernel26.img
}
menuentry 'Ultimate' {
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set root=52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux	/boot/vmlinuz-2.6.35-25-generic root=/dev/disk/by-uuid/52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro  quiet
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Puppy' {
	set root='(hd0,msdos13)'
	##search --no-floppy --fs-uuid --set root=856f3983-f4e9-45da-b500-e199fefbbad1
	linux	/boot/vmlinuz pfix=ram   ### root=/dev/disk/by-uuid/856f3983-f4e9-45da-b500-e199fefbbad1 ro  quiet
	initrd	/boot/initrd.gz
}
menuentry 'Toorox64KDE' {
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set root=9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux	/boot/vmlinuz root=/dev/disk/by-uuid/9c13257a-18a7-4cf6-98be-41387ac8dfca ro  quiet
	initrd	/boot/initrd.gz
}
menuentry "ubuntu" { insmod ext3 set root=(hd0,7) chainloader +1 }

#menuentry 'UbuntuStudio64' {
#	set root='(hd0,msdos7)'
#	search --no-floppy --fs-uuid --set root=f3a87410-015f-4d94-844e-4ec276cfedbc
#	linux	/boot/vmlinuz-2.6.38-8-generic root=/dev/disk/by-uuid/f3a87410-015f-4d94-844e-4ec276cfedbc ro  quiet
#	initrd	/boot/initrd-2.6.38-8-generic.img
#
#}
### END /etc/grub.d/41_NEW_Chakra_Distro ###


```


grub.cfg  NOW

```

# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod part_msdos
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

set menu_color_normal=black/black
set menu_color_highlight=white/red

insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_input console
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
insmod jpeg
background_image -m stretch /etc/grub.d/58844.jpg
set timeout=55
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Arch Linux, with Linux vmlinuz26' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 root=/dev/sda10 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26.img
}
menuentry 'Arch Linux, with Linux vmlinuz26 Fallback' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 root=/dev/sda10 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/42_NEW_Chakra_Distros ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root C65A6C105A6C0013
	chainloader +1
}

menuentry "Should Be TinyMicro, with Linux vmlinuz26 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}

menuentry "UbuntuStudio64, with Linux 2.6.38-8-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=/dev/disk/by-uuid/f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}

menuentry "TooroxKDE64 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda5 vga=791 nomce noapic lang=us
}

menuentry "CtkArch Linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
	initrd /boot/kernel26.img
}

menuentry "Ultimate, with Linux 2.6.35-25-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	#search --no-floppy --fs-uuid --set=root 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	#linux /boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro quiet splash
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda11 ro quiet splash	
	initrd /boot/initrd.img-2.6.35-25-generic
}

menuentry "TooroxGnome64 (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	#search --no-floppy --fs-uuid --set=root 91033a5b-7407-4a80-b1aa-07ff96202ee3
	linux /boot/vmlinuz root=/dev/sda12 nomce noapic lang=us
}
menuentry "Puppy, with Linux  (on /dev/sda13)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	#search --no-floppy --fs-uuid --set=root 856f3983-f4e9-45da-b500-e199fefbbad1
	linux /boot/vmlinuz root=/dev/sda13 pmedia=atahd
	
}
menuentry "Zorin, with Linux (on /dev/sda14)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	#search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux	/boot/vmlinuz-2.6.38-8-generic root=/dev/sda14 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}

### END /etc/grub.d/42_NEW_Chakra_Distros ###


```


COMAPRISON EXAMPLE

NOT WORKING

```

menuentry 'Zorin' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)/dev/sda14'
	#search --no-floppy --fs-uuid --set root=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux	/boot/vmlinuz-2.6.35-25-generic root=/dev/disk/by-uuid/06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro  quiet
	initrd	/boot/initrd.img-2.6.35-25-generic
}


WORKING

menuentry "Zorin, with Linux (on /dev/sda14)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	#search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux	/boot/vmlinuz-2.6.38-8-generic root=/dev/sda14 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}




```





BOOT INFO SCRIPT

```



                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /menu.lst /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda2 and looks at sector 266447120 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #8 
                       for /boot/grub/menu.lst.
    Operating System:  
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Chakra Linux (2011.04 - 
                       Aida) () ()
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda13 and looks at sector 586193008 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #13 for /boot/grub/menu.lst.
    Operating System:  Lucid Puppy Linux Linux 
                       2.6.33.2 [i686 arch]
    Boot files:        /etc/fstab

sda14: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda15: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda16: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub.cfg /grub/grub.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   133,226,495   133,224,448   7 NTFS / exFAT / HPFS
/dev/sda2         133,226,496   133,636,095       409,600  83 Linux
/dev/sda3         133,636,096   143,876,095    10,240,000  82 Linux swap / Solaris
/dev/sda4         143,878,201   976,773,119   832,894,919   f W95 Extended (LBA)
/dev/sda5         143,878,203   164,360,191    20,481,989  83 Linux
/dev/sda6         164,361,078   197,124,095    32,763,018  83 Linux
/dev/sda7         197,126,144   248,326,143    51,200,000  83 Linux
/dev/sda8         248,328,192   340,488,191    92,160,000  83 Linux
/dev/sda9         340,490,240   391,690,239    51,200,000  83 Linux
/dev/sda10        391,692,288   453,132,287    61,440,000  83 Linux
/dev/sda11        453,134,336   504,334,335    51,200,000  83 Linux
/dev/sda12        504,336,384   555,536,383    51,200,000  83 Linux
/dev/sda13        555,538,432   606,738,431    51,200,000  83 Linux
/dev/sda14        606,740,480   698,900,479    92,160,000  83 Linux
/dev/sda15        698,902,528   801,302,527   102,400,000  83 Linux
/dev/sda16        801,304,576   976,773,119   175,468,544  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7969 MB, 7969177600 bytes
246 heads, 62 sectors/track, 1020 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,557,039    15,556,978   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C65A6C105A6C0013                       ntfs       WindowsVista
/dev/sda10       ee7be487-f281-4072-9af3-72612c9a684c   ext3       ArchBang
/dev/sda11       52777f50-fd1d-42d8-9a17-5ad1ddf0b794   ext3       UltimateEdition
/dev/sda12       91033a5b-7407-4a80-b1aa-07ff96202ee3   ext3       Toorox Gnome 64
/dev/sda13       856f3983-f4e9-45da-b500-e199fefbbad1   ext3       Puppy
/dev/sda14       06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb   ext3       Zorin
/dev/sda15       20610f96-41af-401a-956e-d077128f64d3   ext3       Linux From Scrat
/dev/sda16       9fb6e192-7b65-4aed-9922-cbc1a94eed6e   ext2       Shared
/dev/sda2        935626ef-4817-48f4-b690-f6bbaeea7df6   ext3       MY_BOOT_GRUB
/dev/sda3        49b2f37d-e3af-4a16-b7d3-be022adf39b8   swap       
/dev/sda5        196a9858-cc5e-4e14-b9e9-5ca5e21df982   ext3       Distro-1_To Be D
/dev/sda6        ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6   ext3       Chakra
/dev/sda7        f3a87410-015f-4d94-844e-4ec276cfedbc   ext4       UbuntuStudio64
/dev/sda8        b35a2191-0991-4040-8023-1bef352cf212   ext3       Distro-4 To Be d
/dev/sda9        0920168c-5419-4412-8134-713ed2c3814c   ext3       CtkArch64
/dev/sdb1        8A9C26F89C26DE87                       ntfs       ReadyBoost-SysUtilities

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext3       (rw,relatime,errors=continue,barrier=0,data=ordered)
/dev/sda16       /media                   ext2       (rw)
/dev/sda16       /media                   ext2       (rw)
/dev/sdb1        /media                   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/menu.lst: ================================

--------------------------------------------------------------------------------
color cyan/blue white/cyan white/black white/black
timeout 10
default 0

title Tiny Core Linux 
find --set-root --ignore-floppies /tce/boot/bzImage
kernel /tce/boot/bzImage quiet tce=sda1 
initrd /tce/boot/init.gz /tce/boot/ntfs-3g.gz


title Windows
find --set-root /bootmgr && chainloader /bootmgr
find --set-root /ntldr && chainloader /ntldr
--------------------------------------------------------------------------------

========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1

title find /menu.lst, /boot/grub/menu.lst, /grub/menu.lst
	errorcheck off
	configfile /menu.lst || configfile /MENU.LST
	configfile /boot/grub/menu.lst || configfile /BOOT/GRUB/MENU.LST
	configfile /grub/menu.lst || configfile /GRUB/MENU.LST
	find --set-root --ignore-floppies --ignore-cd /menu.lst && configfile /menu.lst
	find --set-root --ignore-floppies --ignore-cd /boot/grub/menu.lst && configfile /boot/grub/menu.lst
	find --set-root --ignore-floppies --ignore-cd /grub/menu.lst && configfile /grub/menu.lst
	errorcheck on
	commandline

title commandline
	commandline

title reboot
	reboot

title halt
	halt


--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       0

=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f3a87410-015f-4d94-844e-4ec276cfedbc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Chainload into GRUB 2
root		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/grub/core.img

title		Ubuntu 11.04, memtest86+
uuid		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
set locale_dir=($root)/boot/grub/locale
set lang=
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro single vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root C65A6C105A6C0013
	chainloader +1
}
menuentry "Arch (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	linux /boot/vmlinuz26 root=/dev/sda10
	initrd /boot/kernel26.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Toorox (on sda12) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 91033a5b-7407-4a80-b1aa-07ff96202ee3
	linux /boot/vmlinuz root=/dev/sda12 nomce noapic lang=us
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda14)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda14)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Chakra Linux, with Linux vmlinuz26 (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single
	initrd /boot/kernel26-fallback.img
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Arch Linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
	initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro
	initrd /boot/kernel26-fallback.img
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
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  63.579459190 = 68.267924480   boot/grub/core.img                             2
  63.580416679 = 68.268952576   boot/grub/grub.cfg                             1
  63.581790924 = 68.270428160   boot/grub/menu.lst                             1
  63.576772690 = 68.265039872   boot/grub/stage2                               3

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
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
set menu_color_normal=light-blue/black
set menu_color_highlight=light-cyan/blue

insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Chakra Linux, with Linux vmlinuz26" --class chakralinux --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	echo	Loading Linux vmlinuz26 ...
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro  quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback" --class chakralinux --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	echo	Loading Linux vmlinuz26 ...Loading Linux Fallback ...
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro  quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (recovery mode)" --class chakralinux --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	echo	Loading Linux vmlinuz26 ...Loading Linux Fallback ...
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26-fallback.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c65a6c105a6c0013
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=========================== sda6/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=burg
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
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
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -neda { command="set theme_name=neda" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Chakra GNU/Linux, with Linux vmlinuz26' --class chakra --class gnu-linux --class gnu --class os --group group_main {
	savedefault
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 resume=/dev/disk/by-uuid/8001914c-bc7c-483d-ba56-400bc4454bc8 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26.img
}
menuentry 'Chakra GNU/Linux, with Linux vmlinuz26 Fallback' --class chakra --class gnu-linux --class gnu --class os --group group_main {
	savedefault
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	echo	'Loading Linux vmlinuz26 ...Loading Linux Fallback ...'
	linux	/boot/vmlinuz26 resume=/dev/disk/by-uuid/8001914c-bc7c-483d-ba56-400bc4454bc8 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
menuentry 'Chakra GNU/Linux, with Linux vmlinuz26 Fallback (recovery mode)' --class chakra --class gnu-linux --class gnu --class os --group group_main {
	savedefault
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	echo	'Loading Linux vmlinuz26 ...Loading Linux Fallback ...'
	linux	/boot/vmlinuz26 resume=/dev/disk/by-uuid/8001914c-bc7c-483d-ba56-400bc4454bc8 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/20_memtest86+ ###
### END /etc/burg.d/20_memtest86+ ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	savedefault
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c65a6c105a6c0013
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class ubuntu --class os --group group_/dev/sda5 {
	savedefault
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 364c8100-5e21-46c0-bb74-77573a700075
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=364c8100-5e21-46c0-bb74-77573a700075 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class ubuntu --class os --group group_/dev/sda5 {
	savedefault
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 364c8100-5e21-46c0-bb74-77573a700075
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=364c8100-5e21-46c0-bb74-77573a700075 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0
UUID=ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 / ext3 defaults 0 0
UUID=8001914c-bc7c-483d-ba56-400bc4454bc8 swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  78.392344475 = 84.173138944   boot/burg/burg.cfg                             1
  78.391577721 = 84.172315648   boot/burg/core.img                             1
  78.392027855 = 84.172798976   boot/grub/core.img                             1
  78.413592339 = 84.195953664   boot/grub/grub.cfg                             1
  78.391379356 = 84.172102656   boot/kernel26-fallback.img                     4
  78.382544518 = 84.162616320   boot/kernel26.img                              2
  78.413352013 = 84.195695616   boot/vmlinuz26                                 2

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f3a87410-015f-4d94-844e-4ec276cfedbc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Chainload into GRUB 2
root		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/grub/core.img

title		Ubuntu 11.04, memtest86+
uuid		f3a87410-015f-4d94-844e-4ec276cfedbc
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
set locale_dir=($root)/boot/grub/locale
set lang=
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro single vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root C65A6C105A6C0013
	chainloader +1
}
menuentry "Arch (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	linux /boot/vmlinuz26 root=/dev/sda10
	initrd /boot/kernel26.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Toorox (on sda12) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 91033a5b-7407-4a80-b1aa-07ff96202ee3
	linux /boot/vmlinuz root=/dev/sda12 nomce noapic lang=us
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda14)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda14)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Chakra Linux, with Linux vmlinuz26 (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single
	initrd /boot/kernel26-fallback.img
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Arch Linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
	initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro
	initrd /boot/kernel26-fallback.img
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda7	/	ext4	errors=remount-ro	0	1
/dev/sda3	none	swap	sw	0	0


--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  95.968204498 = 103.045074944  boot/grub/core.img                             1
  95.961925507 = 103.038332928  boot/grub/grub.cfg                             1
  95.758148193 = 102.819528704  boot/grub/menu.lst                             1
 101.590976715 = 109.082480640  boot/initrd.img-2.6.38-8-generic               2
  94.857501984 = 101.852467200  boot/vmlinuz-2.6.38-8-generic                  1
 101.590976715 = 109.082480640  initrd.img                                     2
  94.857501984 = 101.852467200  vmlinuz                                        1

=========================== sda9/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#  Linux           Grub
# -------------------------
#  /dev/sda        (hd0)
#  /dev/sda3       (hd0,2)
#  /dev/sdb2       (hd1,1)

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# Boot entries follow.
# Each is implicitly numbered from 0 in the order of appearance below.

# You can use the commented entry to boot another system; copy and adjust
# it as many times as you want for all of your other installed systems.
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,8)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02   
initrd /boot/kernel26.img

# (1) Arch Linux fallback (useful if you change your hard disk/mainboard)
title  Arch Linux Fallback
root   (hd0,8)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro
initrd /boot/kernel26-fallback.img

# (2) Optional entry for the system on sda1
title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

title My_GRUB_BOOT
rootnoverify (hdo,1)
makeactive
chainloader +1

title Chakra
root (hd0,5)
kernel /vmlinuz26 root=/dev/sda6
#disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro
initrd /kernel26.img

title UbuntuStudio 64 bit
rootnoverify (hd0,6)
makeactive
chainloader +1

title Toorox 64 bit
rootnoverify (hd0,7)
makeactive
chainloader +1

--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0
UUID=0920168c-5419-4412-8134-713ed2c3814c / ext3 defaults 0 1
UUID=759ac79d-c3af-49f4-ae9a-19a2e3464a02 swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 165.616214752 = 177.829056512  boot/grub/menu.lst                             1
 165.686748505 = 177.904791552  boot/grub/stage2                               2
 165.721801758 = 177.942429696  boot/kernel26-fallback.img                     4
 165.664985657 = 177.881423872  boot/kernel26.img                              2
 165.712062836 = 177.931972608  boot/vmlinuz26                                 2

========================== sda10/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod part_msdos
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

set menu_color_normal=black/black
set menu_color_highlight=white/red

insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_input console
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
insmod jpeg
background_image -m stretch /etc/grub.d/58844.jpg
set timeout=55
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Arch Linux, with Linux vmlinuz26' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 root=/dev/sda10 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26.img
}
menuentry 'Arch Linux, with Linux vmlinuz26 Fallback' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 root=/dev/sda10 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/42_NEW_Chakra_Distros ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root C65A6C105A6C0013
	chainloader +1
}

menuentry "Should Be TinyMicro, with Linux vmlinuz26 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}

menuentry "UbuntuStudio64, with Linux 2.6.38-8-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=/dev/disk/by-uuid/f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}

menuentry "TooroxKDE64 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda5 vga=791 nomce noapic lang=us
}

menuentry "CtkArch Linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
	initrd /boot/kernel26.img
}

menuentry "Ultimate, with Linux 2.6.35-25-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	#search --no-floppy --fs-uuid --set=root 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	#linux /boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro quiet splash
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda11 ro quiet splash	
	initrd /boot/initrd.img-2.6.35-25-generic
}

menuentry "TooroxGnome64 (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	#search --no-floppy --fs-uuid --set=root 91033a5b-7407-4a80-b1aa-07ff96202ee3
	linux /boot/vmlinuz root=/dev/sda12 nomce noapic lang=us
}
menuentry "Puppy, with Linux  (on /dev/sda13)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	#search --no-floppy --fs-uuid --set=root 856f3983-f4e9-45da-b500-e199fefbbad1
	linux /boot/vmlinuz root=/dev/sda13 pmedia=atahd
	
}
menuentry "Zorin, with Linux (on /dev/sda14)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	#search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux	/boot/vmlinuz-2.6.38-8-generic root=/dev/sda14 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}

### END /etc/grub.d/42_NEW_Chakra_Distros ###
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0
UUID=49b2f37d-e3af-4a16-b7d3-be022adf39b8 swap swap defaults 0 0
UUID=ee7be487-f281-4072-9af3-72612c9a684c / ext3 defaults 0 1
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 206.574058533 = 221.807206400  boot/grub/core.img                             2
 206.546886444 = 221.778030592  boot/grub/grub.cfg                             1
 206.555034637 = 221.786779648  boot/grub/stage2                               5
 206.573997498 = 221.807140864  boot/kernel26-fallback.img                     4
 206.642192841 = 221.880365056  boot/kernel26.img                              2
 206.564598083 = 221.797048320  boot/vmlinuz26                                 2

========================== sda11/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
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
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c65a6c105a6c0013
	chainloader +1
}
menuentry "ArchBang Linux (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set f3c20ff5-45cd-4bdf-b517-9018983c8d4d
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/f3c20ff5-45cd-4bdf-b517-9018983c8d4d ro quiet resume=/dev/sda3
	initrd /boot/kernel26.img
}
menuentry "ArchBang Linux Fallback (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set f3c20ff5-45cd-4bdf-b517-9018983c8d4d
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/f3c20ff5-45cd-4bdf-b517-9018983c8d4d ro
	initrd /boot/kernel26-fallback.img
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Chakra Linux, with Linux vmlinuz26 (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single
	initrd /boot/kernel26-fallback.img
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro single vga=786
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "TinyMicro (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda5 vga=791 nomce noapic lang=us
}
menuentry "Chakra (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda6
}
menuentry "TooroxKDE64 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "CtkArchLinux (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda9
}
menuentry "Arch Linux (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
	initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro
	initrd /boot/kernel26-fallback.img
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
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=89e5a88c-252e-4a65-b91e-06d8e9097f35 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 219.641689301 = 235.838468096  boot/grub/core.img                             1
 219.573360443 = 235.765100544  boot/grub/grub.cfg                             1
 219.611007690 = 235.805523968  boot/initrd.img-2.6.35-25-generic              6
 219.721340179 = 235.923992576  boot/vmlinuz-2.6.35-25-generic                 3
 219.611007690 = 235.805523968  initrd.img                                     6
 219.721340179 = 235.923992576  vmlinuz                                        3

========================== sda12/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
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
set timeout=5
insmod vbe
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c65a6c105a6c0013
	chainloader +1
}
menuentry "Chakra Linux, with Linux vmlinuz26 (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single
	initrd /boot/kernel26-fallback.img
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro single vga=786
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "TinyMicro (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda5 vga=791 nomce noapic lang=us
}
menuentry "Chakra (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda6
}
menuentry "TooroxKDE64 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "CtkArchLinux (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda9
}
menuentry "Toorox (on sda12)"{
	insmod ext3
	search --no-floppy --fs-uuid --set 91033a5b-7407-4a80-b1aa-07ff96202ee3
	linux /boot/vmlinuz root=/dev/sda12  nomce noapic lang=us
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

========================== sda12/boot/grub/grub.conf: ==========================

--------------------------------------------------------------------------------
default 0

timeout 5

title Toorox
kernel /boot/vmlinuz root=/dev/sda12 vga=791 nomce noapic lang=us
#initrd /boot/initrd.gz

title Windows
root (hd0,0)
chainloader +1
makeactive
boot
--------------------------------------------------------------------------------

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
/proc      /proc       proc   defaults             0 0
/sys       /sys        sysfs  noauto               0 0
/dev/fd0   /media/floppy auto   users,noauto,exec    0 0
/dev/dvd /media/dvd  auto   users,noauto,exec,ro 0 0
none       /dev/shm    tmpfs  nodev,nosuid,noexec  0 0
# Added by KNOPPIX
/dev/sda1 /media/sda1 ntfs-3g noauto,users,exec,rw,umask=000 0 0
# Added by KNOPPIX
/dev/sda2 /media/sda2 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda3 none swap sw 0 0
# Added by KNOPPIX
/dev/sda5 /media/sda5 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda6 /media/sda6 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda7 /media/sda7 auto noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda8 /media/sda8 auto noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda9 /media/sda9 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda10 /media/sda10 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda11 /media/sda11 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda12 /media/sda12 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda13 /media/sda13 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda14 /media/sda14 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda15 /media/sda15 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sda16 /media/sda16 ext2 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/sdb1 /media/sdb1 fuseblk noauto,users,exec 0 0
/dev/sda12 / ext3 defaults 0 1
--------------------------------------------------------------------------------

=================== sda12: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 242.487411499 = 260.368875520  boot/grub/core.img                             1
 242.550388336 = 260.436496384  boot/grub/grub.cfg                             1
 242.509769440 = 260.392882176  boot/grub/grub.conf                            1
 242.509769440 = 260.392882176  boot/grub/menu.lst                             1
 242.550579071 = 260.436701184  boot/grub/stage2                               2
 242.553928375 = 260.440297472  boot/vmlinuz                                   2

=============================== sda13/etc/fstab: ===============================

--------------------------------------------------------------------------------
/dev/sda13     /            ext3     defaults               0 1
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0
--------------------------------------------------------------------------------

=================== sda13: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 286.780406952 = 307.928117248  boot/vmlinuz                                   2

========================== sda14/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos14)'
search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos14)'
search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
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
if background_color 8,50,90; then
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
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root C65A6C105A6C0013
	chainloader +1
}
menuentry "ArchBang Linux (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos10)'
	search --no-floppy --fs-uuid --set=root f3c20ff5-45cd-4bdf-b517-9018983c8d4d
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/f3c20ff5-45cd-4bdf-b517-9018983c8d4d ro quiet resume=/dev/sda3
	initrd /boot/kernel26.img
}
menuentry "ArchBang Linux Fallback (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos10)'
	search --no-floppy --fs-uuid --set=root f3c20ff5-45cd-4bdf-b517-9018983c8d4d
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/f3c20ff5-45cd-4bdf-b517-9018983c8d4d ro
	initrd /boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single
	initrd /boot/kernel26-fallback.img
}
menuentry "UbuntuStudio64, with Linux 2.6.38-8-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro single vga=786
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Arch Linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
	initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro
	initrd /boot/kernel26-fallback.img
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
--------------------------------------------------------------------------------

=============================== sda14/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda14 during installation
UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=759ac79d-c3af-49f4-ae9a-19a2e3464a02 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda14: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 300.093788147 = 322.223251456  boot/grub/core.img                             1
 300.183769226 = 322.319867904  boot/grub/grub.cfg                             1
 300.093109131 = 322.222522368  boot/initrd.img-2.6.38-8-generic               6
 300.208705902 = 322.346643456  boot/vmlinuz-2.6.38-8-generic                  3
 300.093109131 = 322.222522368  initrd.img                                     6
 300.208705902 = 322.346643456  vmlinuz                                        3

================================ sdb1/grub.cfg: ================================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod part_msdos
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root fb70f55b-e58a-4ac6-af45-19d19cc24d60
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root fb70f55b-e58a-4ac6-af45-19d19cc24d60
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_input console
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Arch Linux, with Linux vmlinuz26-lts' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root fb70f55b-e58a-4ac6-af45-19d19cc24d60
	echo	'Loading Linux vmlinuz26-lts ...'
	linux	/boot/vmlinuz26-lts root=/dev/disk/by-uuid/fb70f55b-e58a-4ac6-af45-19d19cc24d60 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-lts.img
}
menuentry 'Arch Linux, with Linux vmlinuz26-lts Fallback' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root fb70f55b-e58a-4ac6-af45-19d19cc24d60
	echo	'Loading Linux vmlinuz26-lts ...Loading Linux Fallback ...'
	linux	/boot/vmlinuz26-lts root=/dev/disk/by-uuid/fb70f55b-e58a-4ac6-af45-19d19cc24d60 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-lts-fallback.img
}
menuentry 'Arch Linux, with Linux vmlinuz26' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root fb70f55b-e58a-4ac6-af45-19d19cc24d60
	echo	'Loading Linux vmlinuz26 ...'
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/fb70f55b-e58a-4ac6-af45-19d19cc24d60 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26.img
}
menuentry 'Arch Linux, with Linux vmlinuz26 Fallback' --class archlinux --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root fb70f55b-e58a-4ac6-af45-19d19cc24d60
	echo	'Loading Linux vmlinuz26 ...Loading Linux Fallback ...'
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/fb70f55b-e58a-4ac6-af45-19d19cc24d60 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
	initrd /boot/kernel26-fallback.img
}
menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro single
	initrd /boot/kernel26-fallback.img
}
menuentry "UbuntuStudio64, with Linux 2.6.38-8-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro vga=786 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f3a87410-015f-4d94-844e-4ec276cfedbc ro single vga=786
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Gentoo Base System release 2.0.2 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux /boot/vmlinuz root=/dev/sda8
}
menuentry "ArchBang Linux (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos10)'
	search --no-floppy --fs-uuid --set=root f3c20ff5-45cd-4bdf-b517-9018983c8d4d
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/f3c20ff5-45cd-4bdf-b517-9018983c8d4d ro quiet resume=/dev/sda3
	initrd /boot/kernel26.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" --class memtest86 --class gnu --class tool {
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root fb70f55b-e58a-4ac6-af45-19d19cc24d60
  linux16 ($root)/boot/memtest86+/memtest.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod part_msdos
if [ -s $prefix/grubenv ]; then
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

function load_video {
true
}

set menu_color_normal=black
set menu_color_highlight=red

insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_input console
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
insmod jpeg
background_image -m stretch /etc/grub.d/58844.jpg
set timeout=35
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_NEW_Chakra_Distro ###
menuentry 'TinyCore' {
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 88627fac-5ffd-44a4-90cc-cd92f680d547
	linux	/boot/bzImage root=/dev/disk/by-uuid/88627fac-5ffd-44a4-90cc-cd92f680d547 ro  quiet
	initrd	/boot/init.gz quiet  tce=sda5 swapfile=sda3 home=sda3 opt=sda3 safebackup showapps vga=792 superuser waitusb=5:UUID="88627fac-5ffd-44a4-90cc-cd92f680d547" tce=UUID="88627fac-5ffd-44a4-90cc-cd92f680d547"
}
menuentry 'Chakra Linux' {
	set root='(hd0,msdos1,bsd6)'
	#search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro  quiet
	initrd	/boot/kernel26.img
}
menuentry 'Zorin' {
	set root='(hd0,msdos1,bsd14)'
	#search --no-floppy --fs-uuid --set=root 06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
	linux	/boot/vmlinuz-2.6.35-25-generic root=/dev/sda14 #root=/dev/disk/by-uuid/06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb ro  quiet
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'CtkArch64' {
	set root='(hd0,msdos9)'
	#search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
	linux	/boot/vmlinuz26 ##root=/dev/sda9 #isk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro  quiet
	initrd	/boot/kernel26.img
}
menuentry 'Ultimate' {
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 52777f50-fd1d-42d8-9a17-5ad1ddf0b794
	linux	/boot/vmlinuz-2.6.35-25-generic root=/dev/disk/by-uuid/52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro  quiet
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Puppy' {
	set root='(hd0,msdos13)'
	##search --no-floppy --fs-uuid --set=root 856f3983-f4e9-45da-b500-e199fefbbad1
	linux	/boot/vmlinuz pfix=ram   ### root=/dev/disk/by-uuid/856f3983-f4e9-45da-b500-e199fefbbad1 ro  quiet
	initrd	/boot/initrd.gz
}

menuentry 'Toorox64KDE' {
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 9c13257a-18a7-4cf6-98be-41387ac8dfca
	linux	/boot/vmlinuz root=/dev/disk/by-uuid/9c13257a-18a7-4cf6-98be-41387ac8dfca ro  quiet
	initrd	/boot/initrd.gz
}

menuentry "ubuntu" { insmod ext3 set root=(hd0,7) chainloader +1 }
#menuentry 'UbuntuStudio64' {
#	set root='(hd0,msdos7)'
#	search --no-floppy --fs-uuid --set=root f3a87410-015f-4d94-844e-4ec276cfedbc
#	linux	/boot/vmlinuz-2.6.38-8-generic root=/dev/disk/by-uuid/f3a87410-015f-4d94-844e-4ec276cfedbc ro  quiet
#	initrd	/boot/initrd-2.6.38-8-generic.img
#
#}
### END /etc/grub.d/41_NEW_Chakra_Distro ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  64.187537193 = 68.920843264   grub.cfg                                       1
  33.187537193 = 35.634846720   grub/grub.cfg                                  1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  94 c1 89 46 18 8b c1 5e  c3 b8 c0 b3 00 10 e8 1d  |...F...^........|
00000010  5e 00 00 51 56 8b f1 e8  68 ff ff ff 85 c0 74 0b  |^..QV...h.....t.|this is etc/default NOW
00000020  8b 4d 08 50 e8 a1 38 00  00 eb 21 8d 4d f0 e8 2f  |.M.P..8...!.M../|
00000030  36 00 00 8b 4d 08 83 65  fc 00 50 e8 3b 38 00 00  |6...M..e..P.;8..|
00000040  83 4d fc ff 8d 4d f0 e8  43 37 00 00 8b 4d f4 8b  |.M...M..C7...M..|
00000050  c6 64 89 0d 00 00 00 00  5e c9 c2 04 00 55 8b ec  |.d......^....U..|
00000060  51 53 56 57 89 4d fc e8  18 ff ff ff 8b 7d 08 8b  |QSVW.M.......}..|
00000070  f0 6a 01 83 27 00 5b 85  f6 74 3f 8a 06 3c 2b 75  |.j..'.[..t?..<+u|
00000080  03 46 eb 08 3c 2d 75 04  46 83 cb ff 8a 06 84 c0  |.F..<-u.F.......|
00000090  74 21 3c 30 7c 04 3c 39  7e 08 8b 4d fc e8 f8 01  |t!<0|.<9~..M....|
000000a0  00 00 8b 07 0f be 0e 8d  04 80 46 8d 44 41 d0 89  |..........F.DA..|
000000b0  07 eb d9 8b 07 0f af c3  89 07 8b 45 fc 5f 5e 5b  |...........E._^[|
000000c0  c9 c2 04 00 53 56 57 8b  d9 e8 b6 fe ff ff 8b 7c  |....SVW........||
000000d0  24 10 8b f0 83 27 00 85  f6 74 26 8a 06 84 c0 74  |$....'...t&....t|
000000e0  20 3c 30 7c 04 3c 39 7e  07 8b cb e8 aa 01 00 00  | <0|.<9~........|
000000f0  8b 07 0f be 0e 8d 04 80  46 8d 44 41 d0 89 07 eb  |........F.DA....|
00000100  da 5f 8b c3 5e 5b c2 04  00 8b 44 24 04 56 8b f1  |._..^[....D$.V..|
00000110  83 66 08 00 83 f8 0d 74  13 83 f8 0a 74 0e 83 f8  |.f.....t....t...|
00000120  09 74 09 50 8d 4e 04 e8  2f f9 ff ff 8b 0e 8b 01  |.t.P.N../.......|
00000130  ff 10 83 f8 ff 74 0a 83  f8 3c 74 05 83 f8 3d 75  |.....t...<t...=u|
00000140  d3 83 f8 ff 89 46 14 75  07 c7 46 1c 01 00 00 00  |.....F.u..F.....|
00000150  6a 00 8d 4e 04 e8 01 f9  ff ff 5e c2 04 00 8b 44  |j..N......^....D|
00000160  24 04 53 56 8b f1 57 83  66 08 00 83 f8 0d 0f 84  |$.SV..W.f.......|
00000170  e9 00 00 00 83 f8 0a 0f  84 e0 00 00 00 83 f8 09  |................|
00000180  0f 84 d7 00 00 00 83 f8  5c 75 74 8b 0e 8b 01 ff  |........\ut.....|
00000190  10 8b f8 83 ff 22 7f 14  74 0e 83 ff ff 75 5d 8b  |....."..t....u].|
000001a0  ce e8 f4 00 00 00 eb 54  6a 22 eb 4f 83 ff 5b 7f  |.......Tj".O..[.|
000001b0  0e 74 08 83 ff 3d 75 44  57 eb 40 6a 7b eb 00 fe  |.t...=uDW.@j{...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 c5 87 38 01 00 fe  |............8...|
000001d0  ff ff 05 fe ff ff fe 8a  38 01 c9 ec f3 01 00 00  |........8.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt
/media/SCRIPTS/BOOT_INFO/boot_info_script.sh: line 2457: cd: /media
/media/: No such file or directory
  No volume groups found
mdadm: No arrays found in config file or automatically




```


[COLOR="Red"]**QUESTION REQUIRING HELP**[/COLOR]

I am still not able to boot into UbuntuStudio64 though I think I muffed things up by running commands from help texts. It was the first Distro I installed after starting from scratch, I might have to trash it and do a fresh re-install, I had it upgraded to grub2 and downloaded bookoo packages so I would really like to keep it, is there a way to do a reinstall on another partition and just transfer my home and user stuff???




***NOTE***

When I re-installed Windows Vista it took about 7 hours to get it back to how it was with all my software reinstalled, ie. Visual Basic and my software projects, my camera software, printer, scanner as compared to a couple of weeks to get Linux going again major learning curve involved here. I have been reading alot of Grub docs while things are installing and really trying to learn my way around in terminal and I believe I am only scratching the lowest level of awareness of the abilities and power of linux, at first I was going to just give up on it and stick with Windows or just run one distro. But the fact that there are so many other versions out there sparks my inner curiosity to try and figure out the strengths and weeknesses of each one, which are usefull which are not.

It seems the problem lies with the diffence in what each distro has as its background Grub and these differences cause alot of conflict especially if your searching for help and you don't realize at first which version the commands are for. So entering a command it doesn't work and your left scratching your head until you figure out that the commands are not for your particular version of grub or distro or something which causes major confusion.

So I guess it's probably best to pick one distro in particular upgrade it to which version of grub you want and use that as your base for updating your grub multiple menu system.

I also had to download os-prober located in etc/grub.d did not function until I found out about os-prober while Googling. So only when I did that did I start making a little bit of progress.

I even attempted to revert back to legacy based on comments I found regarding the difficulty it causes running Grub2, and if you don't have alot of free time to try and retry and investigate then Grub2 can be a real pain, but if you have alot of free time it can be accomplished.

---

### Post by JASONFUSARO on 2011-07-12
These are some screenshots

---

### Post by JASONFUSARO on 2011-07-12
a couple more screenshots of Zorin the second one is a wobbly window it doesn't look like that in reality you grab it and shake it around and it looks like jelly in realtime pretty cool effect

---

### Post by JASONFUSARO on 2011-07-12
Grub boot menu and my cooling system!!

Fan practically never goes on unless it's 90 degrees in my room like today, usally keeps the CPU at 25c to 30c around 70F


PROBLEMS WITH PIC UPLOAD

---

