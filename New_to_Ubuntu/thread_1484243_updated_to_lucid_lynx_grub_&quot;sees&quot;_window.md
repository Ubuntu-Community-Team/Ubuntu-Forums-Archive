---
title: "updated to lucid lynx grub &quot;sees&quot; windows 7 but will not boot it"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-05-15
I updated to lucid lynx last night.  Lucid boots fine.  Grub notices all partitions but when i go to boot into windows 7 (all os are 64 bit) the screen goes black then it goes back to grub.  I believe i'm using grub 1.98.  I used the bash and sudo update-grub (screen shot included) and still no luck.  Can anyone help?

ps i got rid of backtrack 4 so please disregard signature noting backtrack 4 as an OS that i have installed.

---

### Post by bradmayne04 on 2010-05-15
I have now tried testdisk which did not work.  after using testdisk i rebooted and selected windows 7 and instead of going back to the GRUB operating system selection screen I got a black screen and something that looked like this
 
======S
 
As of right now I am on one of my desktops (linux is on one of my laptops) writing this because I am using this windows 7 recovery disk to try and fix this problem.  I should have foreseen this problem when I was installing lucid lynx last night because I was getting errors from grub during install (i installed by download while using linux and installed from there) however I saw that GRUB "saw" for lack of a better term the windows 7 partition and thought nothing more of it until today when I had to go into my windows OS and suprise! I couldn't boot into windows 7.  I will update this thread again shortly as I believe the windows 7 reinstall is almost done.
PS there is no fix disk or anything from the emachine windows 7 recovery disk(s).  All you can do is partition the whole drive over again and re install win 7 or just re install the win 7 OS again. Which kinda stinks cuz some of the threads i read stated that you could recover with testdisk or your windows recovery disk and fix disk or something to that effect.

---

### Post by samg34 on 2010-05-15
try this:
go to the linux recovery option
go to the update grub option.

try getting the latest version of linux grub and/or ubuntu

---

### Post by oldfred on 2010-05-15
Testdisk will recover from several of the windows problems from backup data that windows keeps. You can also install a windows bootloader from Ubuntu, but if you have NTFS partitions you need a windows disk to run chkdsk.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by bradmayne04 on 2010-05-15
well something is wrong with the BIOS now.  I can not boot at all.  This is a bios issue.  After install of lucid lynx i was unable to change the boot order.  now i'm getting bios errors.  OK so now i'm gonna say it.  I don't care if i get a profile infraction
**** CANONICAL **** UBUNTU THANKS FOR BRICKING MY LAPPY ASSHOLES.
maybe it's my fault you say? i don't think so i am A+ and network + cert so i don't think so.  WUBI ruined my toshiba about a year ago and now this.  I'm going back to SUSE.  **** YOU VERY MUCH!

---

### Post by oldfred on 2010-05-15
Grub nor windows messes with the BIOS. BIOS always boots first and passes boot to the MBR of the primary master drive. (Maybe you missed that class). The BIOS may prevent you from installing boot loaders, some have lockouts or security.

If you want tools to understand the boot process and what is installed where this is useful for all systems, if you boot from a linux liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by samg34 on 2010-05-16
Is the windows partition tagged as bootable?

---

### Post by bradmayne04 on 2010-05-17
> **oldfred said:**
> Grub nor windows messes with the BIOS. BIOS always boots first and passes boot to the MBR of the primary master drive. (Maybe you missed that class). The BIOS may prevent you from installing boot loaders, some have lockouts or security.
 
If you want tools to understand the boot process and what is installed where this is useful for all systems, if you boot from a linux liveCD.
 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.
 blah blah blah

---

### Post by bradmayne04 on 2010-05-20
> **samg34 said:**
> Is the windows partition tagged as bootable?
 
 
Well i don't know yet this is what I did.  I got the hard drive out of that computer and runnind on another.  This is the error message i get from GRUB while trying to boot windows 7 home premium 64 bit. 
 
example :    ===S
 
that's it that's all I get/  now i uses GRUB ver 1.98
did grub maybe change something?  It did something to the bios of the old computer too lots of people sayin it's not true but it was.  Anyways does anyone have any idea's now on how to boot into windows when i need to?

---

### Post by wilee-nilee on 2010-05-20
> **bradmayne04 said:**
> Well i don't know yet this is what I did.  I got the hard drive out of that computer and runnind on another.  This is the error message i get from GRUB while trying to boot windows 7 home premium 64 bit. 
 
example :    ===S
 
that's it that's all I get/  now i uses GRUB ver 1.98
did grub maybe change something?  It did something to the bios of the old computer too lots of people sayin it's not true but it was.  Anyways does anyone have any idea's now on how to boot into windows when i need to?

It is hilarious that you would disregard oldfreds post what he says is correct, if you spent anytime on this forum you would realize the validity.

By the way if you really want this fixed post the bootscript.

---

### Post by bradmayne04 on 2010-05-20
here is /etc/default/grub and /boot/grub/grub.cfg i downloaded and burned the .iso image for windows 7 64 bit.  For some reason I was unable to select the "startup repair" option for some reason which was kinda strange.  I could select other options.  How could I run check disk from the command prompt?  does someone know the options to mount the drive?  I tried cd c: but I could not switch drives! Any idea's?    /etc/default/grub is first:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 acpi_osi=Linux"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true" 

```
and here is /boot/grub/grub.cfg:
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
insmod tga
if background_image /usr/share/images/grub/Glasses_800_edit.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  4f176399-7430-4298-ad78-0df1ec04b3d6
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro   ipv6.disable=1  acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  4f176399-7430-4298-ad78-0df1ec04b3d6
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  4f176399-7430-4298-ad78-0df1ec04b3d6
    linux    /boot/vmlinuz-2.6.31-21-generic  root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro   ipv6.disable=1  acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  4f176399-7430-4298-ad78-0df1ec04b3d6
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic  root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  4f176399-7430-4298-ad78-0df1ec04b3d6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  4f176399-7430-4298-ad78-0df1ec04b3d6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5814d12b14d10d3e
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7c70d18570d14694
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by wilee-nilee on 2010-05-20
Post this in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
to have the code tags either at the tops of the script[] with code in between and [] /code at the bottom, or just highlight the script when you reply and click in the # in the reply window.
Without the information that is provided in the boot script we are all just flailing in the dark, and not protecting your actual installs.

---

### Post by bradmayne04 on 2010-05-20
I'm wondering if I should just reformat the entire drive and start over.  I don't think I will use ubuntu anymore that's crazy that happened.  All I get when I try to boot to windows 7 home premium 64 bit is this:  ====S
What the heck is that?  I've never seen anything like that.  I posted startup scripts, etc., I tried to use the startup disk and run check disk but for some reason I can't change drives with the recovery disk I have am I stupid this is how i'm tryin to change drives from the command prompt in the start up disk: cd c:
 
however when I do that nothing happens.  I don't get this!!  If anyone thinks they have the workaround or whatever let me know!!!

---

### Post by wilee-nilee on 2010-05-20
What I see is your not doing what is easiest; which is posting the script, it is a script which reads the hard drive and gives the lowdown on what is where and pretty much everything needed. 

If you had just followed oldfred's advice to begin with you would probably be set. Also you have to remember that this is a forum for people having problems with their computer setups so there is NO cause and effect in regards to the operating system overall.

You can do what you want but you have blahh blahh solid advice and disregarded any other help, this makes no sense.

---

### Post by oldfred on 2010-05-21
If you want win7 info:
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

Info & adding XP after 7  for windows setup, USB flash drive for repair, shows windows 7 repair menu screen
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

---

### Post by bradmayne04 on 2010-05-21
> **wilee-nilee said:**
> What I see is your not doing what is easiest; which is posting the script, it is a script which reads the hard drive and gives the lowdown on what is where and pretty much everything needed. 
 
If you had just followed oldfred's advice to begin with you would probably be set. Also you have to remember that this is a forum for people having problems with their computer setups so there is NO cause and effect in regards to the operating system overall.
 
You can do what you want but you have blahh blahh solid advice and disregarded any other help, this makes no sense.
 
 
Okay well I will try your advice and apologize to those who have been trying to help.  I reviewed this myself after i ran the script.  Only a couple things that i want to comment on. 1)Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279563752 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block. 
2) I don't have XP.  It was never on this hard drive.  What was on here was vista which is just the loader I'm thinking that the factory kept it there for some reason after upgrading to windows 7.  Upgrade from vista to win 7 was done at factory not by me. (just so ya know)  so I guess the loader is still there and the script mistook vista for xp (which is strange cuz they boot differently!)  The vista loader shows up at boot on GRUB  when I click on that selection (the vista loader) i just did it to see what would happen after all this.  It just brought me back to the GRUB selection screen immediately.  No error codes or anything.  But like I said when I try to boot to windows 7 is when I get the strange error that looks like this: ====S 
and that's all i get.  The system refuses to boot after that error.
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279563752 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 279563752 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   279,290,024   253,907,325   7 HPFS/NTFS
/dev/sda4         279,290,025   488,392,064   209,102,040   5 Extended
/dev/sda5         279,290,088   479,797,289   200,507,202  83 Linux
/dev/sda6         479,797,353   488,392,064     8,594,712  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5814D12B14D10D3E                       ntfs       PQSERVICE                     
/dev/sda2        7C70D18570D14694                       ntfs       SYSTEM RESERVED               
/dev/sda3        66B0D255B0D22B77                       ntfs       eMachines                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4f176399-7430-4298-ad78-0df1ec04b3d6   ext4                                     
/dev/sda6        6e4bf4f8-751c-429c-84e9-637402fa36ac   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
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
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
insmod tga
if background_image /usr/share/images/grub/Glasses_800_edit.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro   ipv6.disable=1 acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro   ipv6.disable=1 acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5814d12b14d10d3e
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7c70d18570d14694
    chainloader +1
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
# / was on /dev/sda5 during installation
UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6e4bf4f8-751c-429c-84e9-637402fa36ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 143.1GB: boot/grub/core.img
 145.4GB: boot/grub/grub.cfg
 143.8GB: boot/initrd.img-2.6.31-21-generic
 144.0GB: boot/initrd.img-2.6.32-22-generic
 143.5GB: boot/vmlinuz-2.6.31-21-generic
 152.4GB: boot/vmlinuz-2.6.32-22-generic
 144.0GB: initrd.img
 143.8GB: initrd.img.old
 152.4GB: vmlinuz
 143.5GB: vmlinuz.old
```

---

### Post by oldfred on 2010-05-21
Because you have windows7 you have two main windows partitions. A 100MB boot partition - sda2 and the main install - sda3

The sda1 partition (seen as Vista) still has grub installed to it. It is probably a recovery partition and may not work, nor be repairable as it may not have the backup boot sector. Not sure if windows tools will fix it. But I do not believe in recovery partitions after a month or two, as you do not want to go back to as installed and delete everything you have done since.

did you try running the teskdisk on both sda2 & sda3, It normally defaults to only one partition.

Your system looks ok with the separate boot partition & main install. If the windows tools run on both sda2 & sda3 should fix it. Have you run a full set of window repairs? 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd


I also have seen users not be able to repair the boot partition even with windows tools, but by moving the boot flag to the main partition run repairs on that partition and it then boots directly. (Boot partition then is not used). You can move the boot flag with gparted, right click on each partition and manage flags. Then use the windows repairs to fix sda3. It should move/create new   /bootmgr /Boot/BCD files. If not move them from sda2 to sda3 then run repairs, so it corrects the changes.

You will still then have to run sudo update-grub as it is trying to boot windows thru the sda2 boot partition.

If you run fixboot it will put the windows boot loader in the MBR. You will have to reinstall grub2 from the liveCD. Be sure to use the grub2 instructions.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by bradmayne04 on 2010-05-21
well I just moved the boot flag like you said and I'm booting up the win 7 repair disk now. okay update this is what happened now i set the boot flag like you said. this time when i start up the recovery disk for win 7 i get a message stating "
 
> **oldfred said:**
> Because you have windows7 you have two main windows partitions. A 100MB boot partition - sda2 and the main install - sda3
 
The sda1 partition (seen as Vista) still has grub installed to it. It is probably a recovery partition and may not work, nor be repairable as it may not have the backup boot sector. Not sure if windows tools will fix it. But I do not believe in recovery partitions after a month or two, as you do not want to go back to as installed and delete everything you have done since.
 
did you try running the teskdisk on both sda2 & sda3, It normally defaults to only one partition.
 
Your system looks ok with the separate boot partition & main install. If the windows tools run on both sda2 & sda3 should fix it. Have you run a full set of window repairs? 
BootRec.exe /fixmbr #updates MBR master boot record do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd
 
 
I also have seen users not be able to repair the boot partition even with windows tools, but by moving the boot flag to the main partition run repairs on that partition and it then boots directly. (Boot partition then is not used). You can move the boot flag with gparted, right click on each partition and manage flags. Then use the windows repairs to fix sda3. It should move/create new /bootmgr /Boot/BCD files. If not move them from sda2 to sda3 then run repairs, so it corrects the changes.
 
You will still then have to run sudo update-grub as it is trying to boot windows thru the sda2 boot partition.
 
If you run fixboot it will put the windows boot loader in the MBR. You will have to reinstall grub2 from the liveCD. Be sure to use the grub2 instructions.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by bradmayne04 on 2010-05-21
okay so i set the flag like you said.  I restarted the windows 7 recovery disk afterwards.  I was not able to make any repairs.  I went to the prompt which was d and is now c after i changed the flags.  Windows is recongnized as windows 7 home premium. (good so far) now startup repair could not detect a problem. (bad)  because of that i tried again after doing the fixmbr option.  (no good no boot for win 7 nor anything else!!)  I an now getting a "disk failure diagnosis" from the recovery disk after startup repairs are run. (really bad) any ideas

---

### Post by oldfred on 2010-05-21
Because you ran the fixMBR that puts the windows boot loader in the MBR which is ok until you can get windows to boot on its own, grub would not boot it anyway. After you get windows working, then you can reinstall grub2. Grub2 is better at finding working windows installs, with old grub we often had to add manual entries.

Are you running the repair or the command line repairs using bootrec.exe?

Windows boot loader in the MBR only looks for the partition with the boot flag (active partition) and jumps to the partition boot sector (PBR) to continue booting. Grub boots to a menu and if you choose windows jumps to that same partition boot sector for windows to boot. How windows works:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

What errors are you getting? Sometimes windows chkdsk repairs those and sometimes testdisk finds partition errors and can fix those.

---

### Post by bradmayne04 on 2010-05-21
I'm not getting ANY errors LOL because nothing is loading I guess.  Not even GRUB i get a blank screen with a cursor blinking.

---

### Post by oldfred on 2010-05-21
This will get you to reinstall grub and boot Ubuntu, but it will not boot windows unless windows will boot on its own.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

once booted
sudo update-grub

Does windows repair disk not give any error messages?

---

### Post by bradmayne04 on 2010-05-21
I can't boot even from a live ubuntu disk. I can boot from a gentoo disk though. Both are for 64 bit systems i'm really confused now! I even burned three copies of an iso to do this too! For some reason 10.04 will not boot now. I wish i had an older copy to work with. This is really weird!  Also, just tried backtrack 4 live disk which worked also!  This is really strange!

---

### Post by bradmayne04 on 2010-05-22
> **oldfred said:**
> This will get you to reinstall grub and boot Ubuntu, but it will not boot windows unless windows will boot on its own.
 
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
Install from LiveCD:
Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda
 
once booted
sudo update-grub
 
Does windows repair disk not give any error messages?
 
I can't mount the /dev/sda5 /mnt and i get the error: mount: unkown filesystem type 'ext4'
i am now able to boot from an old 8.04 disk for some reason.
any idea about the error?

---

### Post by wilee-nilee on 2010-05-22
You need a cd of the distro your using to do this basically 8.04 is legacy grub and ext3. I find that loading the ISO onto a thumb with unetbootin or the startup disc creator works best. 

Also when you want to boot a cd it is best to use the key option to choose the boot device on my computer it is f12 and f2 to get to the bios. 

I have never changed the boot order on my computers for installs or automatic boot from. This works okay with a Linux system that can be hard shutdown with virtually no problems, but windows is different about this.

---

### Post by bipul on 2010-05-22
> **bradmayne04 said:**
> Well i don't know yet this is what I did.  I got the hard drive out of that computer and runnind on another.  This is the error message i get from GRUB while trying to boot windows 7 home premium 64 bit. 
 
example :    ===S
 
that's it that's all I get/  now i uses GRUB ver 1.98
did grub maybe change something?  It did something to the bios of the old computer too lots of people sayin it's not true but it was.  Anyways does anyone have any idea's now on how to boot into windows when i need to?

I would like to pont at the line where he said.. where he's taking the hdd out and running it on another system ... i think the stage 1 stage 2.. things got tampered there... if he is atall trying to do that... 
normally installtions done on one system and ... if we try to do the boot on another... it generaslly doesnot happen... atleast when i had tried that with a neighbours hdd.. it did not work...

{ if i did not understand ... as to that's what he did... ignore my post please... i just wanted to help in the bitter-sweet interaction; if i am wrong just inform me...  }

---

### Post by oldfred on 2010-05-22
Old grub 0.97 may or may not be compatible with ext4. Ubuntu modified the grub 0.97 with 9.04 to work with ext4. Any old grubs before that will not know what ext4 is. Other distributions may not either.

---

### Post by bradmayne04 on 2010-05-22
okay I ran a win 7 complete restore because I couldn't boot anything right?  Then, the next thing I know when I boot I go to grub like it was before all this happened! ummm, still can't boot win 7 though! kinda funny use a win 7 recover disk for recovering ubu... anyways idea?

---

### Post by Elfy on 2010-05-22
> File system: ntfs
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 and
looks at sector 279563752 of the same hard drive for
**core.img, but core.img can not be found at this**
location. No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /BOOTMGR /BOOT/BCD

This might help you 

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by bradmayne04 on 2010-05-22
> **bradmayne04 said:**
> I can't mount the /dev/sda5 /mnt and i get the error: mount: unkown filesystem type 'ext4'
i am now able to boot from an old 8.04 disk for some reason.
any idea about the error?
 
 
I read that you should not have the windows selection highlighted?  Is this true? Should I make sure that the selection is NOT highlighted?

---

### Post by wilee-nilee on 2010-05-22
> **bradmayne04 said:**
> okay I ran a win 7 complete restore because I couldn't boot anything right?  Then, the next thing I know when I boot I go to grub like it was before all this happened! ummm, still can't boot win 7 though! kinda funny use a win 7 recover disk for recovering ubu... anyways idea?

Since there have been repair attempts, you should probably post the script again. If you can use the code tags, the easiest way is [] with the word code in between at the top of the text and [] with  /code in between the brackets at the bottom of the text. Your doing good, this has been a trying job to get it working but your sticking with it. ;)

Hopefully forestpiskie will get back to you with the info you need I am just not familiar with testdisk.

---

### Post by Elfy on 2010-05-22
> Since there have been repair attempts, you should probably post the script again.I'd agree with that 

Just to reiterate - please use code tags

[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end

---

### Post by bradmayne04 on 2010-05-22
tried to move boot flag to sda3 and rebooted. then received bootmgr is missing press ctrl alt del. ArRRGGHH! LOL so for some reason the boot flag can't be moved. I don't know what to say about that but now i gotta play w/ it again so I'll probably post again in the morning cuz this will run while i'm sleeping. there's not much i can do except to get it back to where i just was and be able to boot grub and only into linux lucid 64 bit. can't boot into win 7. anyways, let me know what you think now cuz like i said i can't change boot flag.
 
okay back to grub booting fine and lucid booting fine.  now still can't boot win 7.  if i try to select win 7 i go back to grub selection screen to pick an OS.  sda2 is win 7.

---

### Post by bradmayne04 on 2010-05-22
Ok so I'm up drinking coffee at 11:30 in the am and will post the script again shortly.

---

### Post by bradmayne04 on 2010-05-22
here is the output of the script now the GRUB OS selection screen is telling me that sda2 is for win 7.  the script is sayin that it's sda3!
here take a look at the output of update-grub:
brad@brad-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found Debian background: Glasses_800_edit.tga
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
&#8220;Adding Windows&#8221;
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2



 here: take a look, also how can I reformat the entire drive and start again?  
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279561864 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 279561864 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 279561864 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   279,290,024   253,907,325   7 HPFS/NTFS
/dev/sda4         279,290,025   488,392,064   209,102,040   5 Extended
/dev/sda5         279,290,088   479,797,289   200,507,202  83 Linux
/dev/sda6         479,797,353   488,392,064     8,594,712  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5814D12B14D10D3E                       ntfs       PQSERVICE                     
/dev/sda2        7C70D18570D14694                       ntfs       SYSTEM RESERVED               
/dev/sda3        520438C50438ADBB                       ntfs       eMachines                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4f176399-7430-4298-ad78-0df1ec04b3d6   ext4                                     
/dev/sda6        6e4bf4f8-751c-429c-84e9-637402fa36ac   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
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
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
insmod tga
if background_image /usr/share/images/grub/Glasses_800_edit.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro   ipv6.disable=1 acpi_osi=Linux
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(sda0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f176399-7430-4298-ad78-0df1ec04b3d6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5814d12b14d10d3e
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7c70d18570d14694
    chainloader +1
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
# / was on /dev/sda5 during installation
UUID=4f176399-7430-4298-ad78-0df1ec04b3d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6e4bf4f8-751c-429c-84e9-637402fa36ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 143.1GB: boot/grub/core.img
 160.3GB: boot/grub/grub.cfg
 144.0GB: boot/initrd.img-2.6.32-22-generic
 152.4GB: boot/vmlinuz-2.6.32-22-generic
 144.0GB: initrd.img
 152.4GB: vmlinuz

---

### Post by oldfred on 2010-05-22
You still have grub installed to the windows boot sectors of both sda1 and sda2 (are we back to where we were, or did you post the old boot script?):

Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279561864 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.

When you run this it may default to just one of your windows partitions, but you also need to select the other and repair it.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters: sda1 & sda2

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by bradmayne04 on 2010-05-22
no it's a fresh result that i put up from a few minutes ago.  Also, I've been tryin to say that I can't change the boot flag in gparted because that will cause an error on boot stating that the bootmgr is missing press ctrl alt del.  Fred, I know your tryin to help but I think the problem is w/ grub.  I've re-installed win 7 several times now.   even going back to "from factory state" this is obviously not working.  I believe that the issue is w/ GRUB.  i think that w/ all the changes made something bad happened.  if i used an older version of grub(i can't though because old grub doesn't understand ext 4) i don't think the problem would have been there.  What I want to do is to wipe the entire drive, install win7, then partition myself, and either install something old like 8.04 or suse or even gentoo (funny people say gentoo is a pain but nothing is as bad as this!) so let me know how to wipe an entire drive and all partitions from a win 7 recovery disk from c: prompt or linux live disk.  thanks i hate to do it now but i don't have all the time in the world.  I've been dealing w/ this for 2 days.

> **oldfred said:**
> You still have grub installed to the windows boot sectors of both sda1 and sda2 (are we back to where we were, or did you post the old boot script?):

Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279561864 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.

When you run this it may default to just one of your windows partitions, but you also need to select the other and repair it.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters: sda1 & sda2

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by bradmayne04 on 2010-05-22
this is the same message i received last time.  here is the output after running testdisk:
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS           1567   0  1  1579 254 63     208845 [SYSTEM RESERVED]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.






> **bradmayne04 said:**
> no it's a fresh result that i put up from a few minutes ago.  Also, I've been tryin to say that I can't change the boot flag in gparted because that will cause an error on boot stating that the bootmgr is missing press ctrl alt del.  Fred, I know your tryin to help but I think the problem is w/ grub.  I've re-installed win 7 several times now.   even going back to "from factory state" this is obviously not working.  I believe that the issue is w/ GRUB.  i think that w/ all the changes made something bad happened.  if i used an older version of grub(i can't though because old grub doesn't understand ext 4) i don't think the problem would have been there.  What I want to do is to wipe the entire drive, install win7, then partition myself, and either install something old like 8.04 or suse or even gentoo (funny people say gentoo is a pain but nothing is as bad as this!) so let me know how to wipe an entire drive and all partitions from a win 7 recovery disk from c: prompt or linux live disk.  thanks i hate to do it now but i don't have all the time in the world.  I've been dealing w/ this for 2 days.

---

### Post by oldfred on 2010-05-22
I typically do not recommend it but a few have gone back to grub legacy. You just have to download and run the latest copy of grub legacy from Ubuntu. Older versions of grub legacy (before Ubuntu 9.04) or versions from other distributions will not recognize ext4.

HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by bradmayne04 on 2010-05-22
Ok I downloaded Gparted live disk, ran it, removed ALL partitions and am starting from scratch.  (i should have done this 2 days ago but whatever it was a learning experience) i guess this thread will never really be "solved" but I will tell you what I learned:
1) GRUB2 is very different then the old GRUB.  I like old GRUB more myself.  
2) old GRUB will not reconongnize ext 4 GRUB2 will.
3) win 7 and vista boot very differently then XP
4) XP doesn't have as many problems at boot.
5) If i could I would install XP
6) I'm thinking about partitioning win 7 and installing ubuntu 8.04.
7) I have only 2 real complaints about ubuntu. actually 3 counting their using GRUB2 (actually 1.98) those are:
A) i can't use my fifth generation and I say FIFTH generation because their is software out there for the older generation IPOD nano.  I can't get my fifth generation to work in ubuntu.  I have to use Itunes.  If you know of anything that you personally have used for a FIFTH Generation NANO let me know ASAP, 
B) Samba and winbind.  I struggled for days to get the printer on my home network which is attached to a vista machine to work.  I needed winbind to make it work.  However, winbind made my internet browsing so slow it was unbearable (and i do have patience and put up w/ a lot in order to learn the mysterious ways of ubuntu LOL)  before going to prison I had 7.04 feisty fawn i believe and I never had that problem with samba and winbind.
C) of course if you have been reading this thread so far then you know the struggles I had w/ GRUB2.  I don't think something should be released until enough bug testing etc. has gone into it so the average home user will not be pulling his/her hair out when their is a problem.  
afterthoughts: a lot of well meaning people tried to help me on this thread and for that I am grateful however I don't think everyone understood the problem outside of old fred.  He and I have been sending many many private message's to each other about this for the past few days.  So, thanks fred for trying to help but at this point I had to wipe that drive.  Almost done as of now with what I hope will be the last re-install.  So thanks again all.

---

### Post by oldfred on 2010-05-22
IF you create the NTFS partition for win7 before installing it will not create the separate boot partition which I think has contributed to some of the problems.

Win7 system partition info
[http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/](http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/)


I had great luck with Karmic but it also uses grub2 as a default. Some software in windows writes to the MBR and corrupts grub2 but old grub and the windows boot loader tolerate the extra data in the MBR (which should not be used for other software except booting anyway).

More info on how windows works _show Vista but 7 is the same except for the new boot partition.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

