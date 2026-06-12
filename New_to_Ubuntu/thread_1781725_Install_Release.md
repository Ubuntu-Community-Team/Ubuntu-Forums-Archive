---
title: "Install Release?"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by smcrossman on 2011-06-13
A couple of days ago I did what in Windows would be called a "repair" install...or so I thought.  My monster machine had inconsistent issues that were preogressively increasing and spreading. I fiugred from previous experience with this machine and with the fact that I've been doing a lot of tweaking of the programming that I might just as well do a fresh install of Natty, keeping my dual boot and see if that resolved some of the issues.

Well first install failed because the installer crashed. Second try went fine and I've been slowly getting the appearance & environment where I think I want it as well as installing the packages that I had tried out in the past month and want to keep using.  I've also been working out the issues with my wireless networking (with a lot of help from these forums).

Now I've found an icon on my Unity launcher that is labeld Install Release.  If I click on it it takes me to a window to install Ubuntu.  I'm really confused.  I am not running a LIve CD or Boot stick.  My hard drive is split up all over the place in partitions, but so far I've only found the 2 reserve areas and the large Windows partition and the Ubuntu partition that have things in them.  I've found and moved my previous home folder into my current home directory and it looks like everything is there (amazingly lucky!) 

So what is the install release and what is it going to do to my computer and my set-up?

---

### Post by cariboo on 2011-06-13
It looks like your install didn't go correctly, I'd just remove the icon and forget about it.

---

### Post by smcrossman on 2011-06-14
Under other circumstances I might be willing to do that. But I really need to be sure my foundation here is solid. This particular pc will be hosting my Samba network for a good wihile, and also be the location of virtual machines.  Actually I'm hoping to remove windows from it completely if I can master the VM set up and usage and get the network functioning up to where I want it to be.

I think maybe I should look at backing up what I have now and doing a completely fresh install...?  I know right now my Linux portion of the HD is in 5 partitions which seems really unnecessary....one for the file system one for extended logical partitions and 2 for SWAP.  Maybe I really am making more work for myself, but I spent the first 18 months with this particular pc having to reformat and reinstall back to factory specs every 10-21 days.  It was awful, but I couldn't do anything else with the issues that kept re-occurring.  Upgrading to Win7 solved most of those, and then switching to 64bit solved even more.  I'm hoping (and really expecting) that if I get it stable with Ubuntu and remove Windows it will actually live up to some of its original potential.

So I guess my question right now is do I backup on external and totally reformat/partition/install the Ubuntu section or do I somehow use this Install Release?  What is it for? How does it work? What does it do?

---

### Post by smcrossman on 2011-06-14
Okay, this is really nagging at me. I'm trying to figure out if I'm totally reformatiing the current linux partitions and reinstalling or if I can just clean things up somehow and keep moving forward in this transition process.  I've searced the forums, I've searched documentation I can't find anything about install RELEASE.  It is an app (listed in my installed applications).  

I've taken some screenshots. First the properties information received by right clicking on the icon in usr/share/applications.  Then the first 3 screens that come up if you launch it.  I'm really confused by the terminology....permanent?  is my current Ubuntu install set to self destruct?  Do I really have 2 installs of the same OS playing in the same partition?  I haven't seen any sign of that but then again how would I know? 

Please, has anyone actually seen this or even heard of this before?

---

### Post by el_koraco on 2011-06-14
It's a weird one. I'm guessing that it's a bizzarro scenario in which the install process just didn't remove the installer after finishing with the install.

---

### Post by VanR on 2011-06-14
May not be so uncommon as my Zorin OS 5 install has "Install Zorin OS" in the System> Administration menu. Guess what happens if you click on it? It tries to reinstall. I have just ignored it for now. Don't have a clue as to how to get rid of it.

---

### Post by el_koraco on 2011-06-14
I'd say sudo apt-get remove ubiquity?

---

### Post by Paddy Landau on 2011-06-14
If your PC will be around for a while, and you want a rock-solid foundation, then (a) you want a Long Term Support (LTS) version, and (b) you want to get everything right.

(a) The current LTS is 10.04, supported until 13.04 (April 2013). 11.04 is supported only until 12.10 (October 2012).

(b) Make a **full** backup; consolidate your partitions (one for swap, one for Ubuntu, one for /home, and the remainder for Windows); install from scratch; restore if necessary.

---

### Post by JohnBonne on 2011-06-14
> **smcrossman said:**
> Okay, this is really nagging at me. I'm trying to figure out if I'm totally reformatiing the current linux partitions and reinstalling or if I can just clean things up somehow and keep moving forward in this transition process.  I've searced the forums, I've searched documentation I can't find anything about install RELEASE.  It is an app (listed in my installed applications).  

I've taken some screenshots. First the properties information received by right clicking on the icon in usr/share/applications.  Then the first 3 screens that come up if you launch it.  I'm really confused by the terminology....permanent?  is my current Ubuntu install set to self destruct?  Do I really have 2 installs of the same OS playing in the same partition?  I haven't seen any sign of that but then again how would I know? 

Please, has anyone actually seen this or even heard of this before?

yes a milestone in Linux. Installs have to be recognised throughout so one drive wont recognise the others. And tis include Windows/Linux installs. I can't help but this is very interesting. Seems things are coming to a head as this is the third subscription of this type this last hour.

I can produce the others if you want.

---

### Post by smcrossman on 2011-06-14
Okay, I am feeling a bit better.  It isn't just my monster coming back out to torture me.  I did 2 installs Saturday...the first the installer crashed, I tried to report the but but it locked up on me and I couldn't get the information to send.  So then I rolled the dice again and did another install again replacing linux 11.04 with 11.04.  That one finished fine but I didn't have time to work through all the packages with synaptic so I quit and came back later to find I had a lot of things to reinstall.  So somewhere in there the installer got a bit confused about things.

I'm guessing that since I'm not sure what all is on there that I need to at least redo my Linux portion of the drive.  The windows is huge, and I haven't even started thinking about transferring documents and things over yet.  Unfortunately my PC will NOT back up windows in any way shape or form, and if you do partial backups it will not be able to read them to restore.  The OS isn't such an issue since I purchased it online so I can go back and redownload it to reinstall, but I just don't want to it's an ugly dirty process and why waste the time if I am going to wipe it away in the next 3 months or so?

I guess I could (if I can get this monster in windows to comply) use networking and move the files to my netbook and just wipe windows off this now.  But I have about 3 seriously needed programs that I just can't do in linux, and they tend to bog down on the netbook.

I'm exploring VM to see if I can make that work for those few programs, and have yet to look at Wine.  Any suggestions out there?  I do appreciate the feedback about LTS vs. Natty. And if I actually can get VM working (user issues no experience) then LTS would be safer and I could a VM to explore the new things and such.  But at the same time, the more I learn and find out I'm enjoying learning and working out MY issues with tweaking things so frequent upgrades might be something to keep me on my toes long term.

Anyway...any thoughts suggestions from newbies or experienced a like welcome.  I won't mark this as solved since we still don't know what the deal is, but I'm guessing its just one of those things that you need to keep an eye out  for (like when one of the idiot lights on the car stays on a little too long and pops on sporadically but never stays lit) not a fire in the kitchen but something to watch.

---

### Post by JohnBonne on 2011-06-15
> **smcrossman said:**
> Okay, this is really nagging at me. I'm trying to figure out if I'm totally reformatiing the current linux partitions and reinstalling or if I can just clean things up somehow and keep moving forward in this transition process.  I've searced the forums, I've searched documentation I can't find anything about install RELEASE.  It is an app (listed in my installed applications).  

I've taken some screenshots. First the properties information received by right clicking on the icon in usr/share/applications.  Then the first 3 screens that come up if you launch it.  I'm really confused by the terminology....permanent?  is my current Ubuntu install set to self destruct?  Do I really have 2 installs of the same OS playing in the same partition?  I haven't seen any sign of that but then again how would I know? 

Please, has anyone actually seen this or even heard of this before?

Very windows. It is empirical. It works or it doesn´t.. What I mean is the problem is reparable or it isn´t It is trying to remind you about a previous setup or program that doesn´t exist? There may be trace hidden files you haven´ cleaned up or traces left behind that resemble another O/s. The clean-up tool you heard mentioned may be around. Really this is the kind of refreshing post I enjoy, a technical problem with the answer located at the root of code.

I would like to hear if you find the answer to this bug and any others that resemble it. An installer like Norton-Anti-virus has for it's program may be what the doctor ordered.

Here is my story. I have attended several others. [http://ubuntuforums.org/showthread.php?t=1781051](http://ubuntuforums.org/showthread.php?t=1781051)

---

### Post by smcrossman on 2011-06-15
Thanks for the information & the boot script link looks promising.  I had actually been to your link because I'm currently looking at using an external HD (or usb stick) for filesystem on one computer and setting my Samba shares up on an actual external HD to hopefully eventually transfer to a network position when I get a gateway/router that will allow that.

Anyway, before I make any decisions I think I'll run computer janitor (not familar with it but figure I would try it) and then use the boot script program and see what I'm actually looking at there.

---

### Post by smcrossman on 2011-06-15
Okay....here is the result of my boot info script.  It is seriously long. I forgot to take the external HD where I've partitioned for networking  AND been playing with creating VMs off the PC before I ran it. I'm hoping that is where the length and obvious messages that might need addressed are originating.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdg1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdg1 starts at sector 62.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   435,712,469   435,505,622   7 NTFS / exFAT / HPFS
/dev/sda3         435,714,046   625,141,759   189,427,714   5 Extended
/dev/sda5         617,021,440   625,141,759     8,120,320  82 Linux swap / Solaris
/dev/sda6         435,714,048   608,897,023   173,182,976  83 Linux
/dev/sda7         608,899,072   617,017,343     8,118,272  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34   389,749,303   389,749,270 Data partition (Windows/Linux)
/dev/sdb2     389,749,304   625,142,414   235,393,111 Swap partition (Linux)

Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             62    15,650,907    15,650,846   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/ramzswap0                                          swap       
/dev/sda1        122808D92808BE2B                       ntfs       System Reserved
/dev/sda2        E0EC0AE8EC0AB934                       ntfs       
/dev/sda5        97e0c3d2-c0d6-499a-94bd-7f841bb73571   swap       
/dev/sda6        3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac   ext4       
/dev/sda7        472ad73f-3029-487e-8bc5-d32d140df238   swap       
/dev/sdb1        1dde0a65-14ad-4ea8-a3ee-337f0b988a9b   ext3       Home Network
/dev/sdb2        4ffd2469-553e-421c-8163-8bdf47241780   swap       network swap
/dev/sdg1        5ECE-CBE6                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Home Network      ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg1        /media/5ECE-CBE6         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda6/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac

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

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Chainload into GRUB 2
root        3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024x24,1280x800x24,1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
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
set menu_color_normal=yellow/black
set menu_color_highlight=light-green/light-gray
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    echo    'Loading Linux 2.6.38-9-generic ...'
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 122808D92808BE2B
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=3f2f3012-a1ab-4d87-8e6c-e6ccfa2846ac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=97e0c3d2-c0d6-499a-94bd-7f841bb73571 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=472ad73f-3029-487e-8bc5-d32d140df238 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 259.903713226 = 279.069487104  boot/grub/core.img                             1
 235.961631775 = 253.361872896  boot/grub/grub.cfg                             1
 252.125579834 = 270.717779968  boot/grub/menu.lst                             1
 223.600585938 = 240.089300992  boot/initrd.img-2.6.38-10-generic              2
 261.275321960 = 280.542240768  boot/initrd.img-2.6.38-8-generic               1
 231.273288727 = 248.327802880  boot/initrd.img-2.6.38-9-generic               2
 256.116523743 = 275.003023360  boot/vmlinuz-2.6.38-10-generic                 1
 260.044681549 = 279.220850688  boot/vmlinuz-2.6.38-8-generic                  1
 231.151679993 = 248.197226496  boot/vmlinuz-2.6.38-9-generic                  1
 223.600585938 = 240.089300992  initrd.img                                     2
 261.275321960 = 280.542240768  initrd.img.old                                 1
 256.116523743 = 275.003023360  vmlinuz                                        1
 260.044681549 = 279.220850688  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  4e 00 4c 00 53 00 20 00  69 00 6e 00 69 00 74 00  |N.L.S. .i.n.i.t.|
00000010  69 00 61 00 6c 00 69 00  7a 00 61 00 74 00 69 00  |i.a.l.i.z.a.t.i.|
00000020  6f 00 6e 00 0d 00 0a 00  00 00 00 00 3c 00 01 00  |o.n.........<...|
00000030  4e 00 4c 00 53 00 20 00  63 00 6f 00 6e 00 66 00  |N.L.S. .c.o.n.f.|
00000040  69 00 67 00 75 00 72 00  61 00 74 00 69 00 6f 00  |i.g.u.r.a.t.i.o.|
00000050  6e 00 20 00 63 00 68 00  61 00 6e 00 67 00 65 00  |n. .c.h.a.n.g.e.|
00000060  73 00 0d 00 0a 00 00 00  28 00 01 00 4e 00 4c 00  |s.......(...N.L.|
00000070  53 00 20 00 6f 00 70 00  65 00 72 00 61 00 74 00  |S. .o.p.e.r.a.t.|
00000080  69 00 6f 00 6e 00 73 00  0d 00 0a 00 00 00 00 00  |i.o.n.s.........|
00000090  38 00 01 00 4e 00 4c 00  53 00 20 00 63 00 6c 00  |8...N.L.S. .c.l.|
000000a0  65 00 61 00 6e 00 2d 00  75 00 70 00 20 00 6f 00  |e.a.n.-.u.p. .o.|
000000b0  70 00 65 00 72 00 61 00  74 00 69 00 6f 00 6e 00  |p.e.r.a.t.i.o.n.|
000000c0  73 00 0d 00 0a 00 00 00  3c 00 01 00 4d 00 55 00  |s.......<...M.U.|
000000d0  49 00 20 00 6e 00 6f 00  74 00 69 00 66 00 79 00  |I. .n.o.t.i.f.y.|
000000e0  20 00 69 00 6e 00 69 00  74 00 69 00 61 00 6c 00  | .i.n.i.t.i.a.l.|
000000f0  69 00 7a 00 61 00 74 00  69 00 6f 00 6e 00 0d 00  |i.z.a.t.i.o.n...|
00000100  0a 00 00 00 34 00 01 00  4d 00 55 00 49 00 20 00  |....4...M.U.I. .|
00000110  6e 00 6f 00 74 00 69 00  66 00 79 00 20 00 6f 00  |n.o.t.i.f.y. .o.|
00000120  70 00 65 00 72 00 61 00  74 00 69 00 6f 00 6e 00  |p.e.r.a.t.i.o.n.|
00000130  0d 00 0a 00 00 00 00 00  38 00 01 00 53 00 45 00  |........8...S.E.|
00000140  4d 00 20 00 53 00 63 00  65 00 6e 00 61 00 72 00  |M. .S.c.e.n.a.r.|
00000150  69 00 6f 00 20 00 4c 00  69 00 66 00 65 00 63 00  |i.o. .L.i.f.e.c.|
00000160  79 00 63 00 6c 00 65 00  0d 00 0a 00 00 00 00 00  |y.c.l.e.........|
00000170  30 00 01 00 53 00 45 00  4d 00 20 00 49 00 6e 00  |0...S.E.M. .I.n.|
00000180  69 00 74 00 69 00 61 00  6c 00 69 00 7a 00 61 00  |i.t.i.a.l.i.z.a.|
00000190  74 00 69 00 6f 00 6e 00  0d 00 0a 00 00 00 00 00  |t.i.o.n.........|
000001a0  38 00 01 00 4e 00 4c 00  53 00 20 00 63 00 6f 00  |8...N.L.S. .c.o.|
000001b0  64 00 65 00 20 00 70 00  61 00 67 00 65 00 00 ef  |d.e. .p.a.g.e...|
000001c0  ff ff 82 ef ff ff 02 88  ce 0a 00 e8 7b 00 00 ef  |............{...|
000001d0  ff ff 05 ef ff ff 01 00  00 00 01 90 52 0a 00 00  |............R...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

So does the tell any of you what I should do next?  LOL

---

### Post by Paddy Landau on 2011-06-16
Wine: If you want to experiment with Wine, I strongly suggest you install [PlayOnLinux]("http://www.playonlinux.com/"). Wine is a bit complicated. PlayOnLinux is a front-end to Wine that hides much of the complexity, and lets you install different Windows programs in different "prefixes", so they don't accidentally interfere with each other (as happens on Windows machines). Uninstalling via PlayOnLinux is lightning fast.

Be aware that Wine is a work-in-progress, and very few Windows programs work without flaws; not that many work at all.

Windows in VirtualBox works very well indeed provided you have sufficient RAM. Don't download from the default repository, but instead follow the instructions on the [VirtualBox Linux download page]("http://www.virtualbox.org/wiki/Linux_Downloads") (scroll down to "Debian based Linux distributions"). You will find it much more pleasant if you also download and install the Extension Pack; again, not from the default repository, but follow the instructions on the main [VirtualBox download page]("http://www.virtualbox.org/wiki/Downloads").

If you have the RAM to run a VM, I suggest using it instead of Wine (& PlayOnLinux).

---

### Post by 3rdalbum on 2011-06-16
> **Paddy Landau said:**
> Wine: If you want to experiment with Wine, I strongly suggest you install [PlayOnLinux]("http://www.playonlinux.com/"). Wine is a bit complicated. PlayOnLinux is a front-end to Wine that hides much of the complexity

PlayOnLinux only works when you are installing one of the programs that it has a definition for. Unless something has changed since my last PoL experience.

---

### Post by Paddy Landau on 2011-06-16
> **3rdalbum said:**
> PlayOnLinux only works when you are installing one of the programs that it has a definition for. Unless something has changed since my last PoL experience.
No, PlayOnLinux can install any Windows program. It is not obviously visible on the installation window; at the bottom left-hand side it has the text, "Install a .pol package or an unsupported application." Click it for the installation wizard.

---

### Post by smcrossman on 2011-06-16
Well, I've not been able to actual install an OS to try out VirtualBox.  I did download from the repository though, since  I still have issues figuring out how to install other ways.  I did manage to get the non-repository expansion installed yesterday though.  I guess I'd better double check the RAM requirements, although I think I'm okay.

As far as Wine, I haven't found any real documentation or how to on it.  So it has left me baffled. I will check out PlayOnLInux and see if that helpps some.

Thanks for all the input and advice. I'm specifically looking at device specific programs to download medical devices, and the drivers for the unifying receiver and mouse from Logitech. I know that setting up the mouse buttons is possible with available apps through Gnome & Ubuntu, but the ability to transfer from one pc to another isn't....or at least I haven't been able to find anything like that. Then just silly little things like coupon printing and other such web things where they have weird blocks due to OS or browser.  I've actually found more functionality and versatility in the apps available for linux than what I had with Windows, hence the desire to just wipe Windows totally.

---

### Post by Paddy Landau on 2011-06-16
> **smcrossman said:**
> As far as Wine, I haven't found any real documentation or how to on it.  So it has left me baffled. I will check out PlayOnLInux and see if that helpps some.
I wouldn't know how to even start using Wine. PlayOnLinux handles it all for me.

> **smcrossman said:**
> ... the drivers for the unifying receiver and mouse from Logitech.
Logitech seems to "just work" with Linux. I have used wireless and wired Logitech keyboards and mice for years without any problems.

> **smcrossman said:**
> ... the ability to transfer from one pc to another...
Do you mean transferring settings? All settings are stored in files in your home directory. Find the directory, copy it over, and voilà -- the settings are there.

---

### Post by smcrossman on 2011-06-16
> **Paddy Landau said:**
> 
Do you mean transferring settings? All settings are stored in files in your home directory. Find the directory, copy it over, and voilà -- the settings are there.


No I'm specifically referring to their unified receiver & program. It's only for some of their wireless products. It uses one usb receiver and will handle up to 6 devices.  Most commonly a mouse and a keyboard, but it handles remotes and presentors, etc., as well...if the product is designed for that system.

The beauty of it for me is that I can take my mouse (Performance Mouse MX) with its multiple buttons and functions from my primary desktop to the netbook as easily as just re-pairing it with the receiver.  (Yes copying the directory for the set up helps a lot too). Unfortunately I haven't found a way to pair it up without going all the way into windows.  Basically even sitting here in the recliner (My prim desktop's monitor sits here) I could pull the receiver out of the desktop and pair up with the netbook, then, do the same in reverse to go back to using it for the pc.  Or I could pull the receiver and go into the back and use it on the netbook back there, when I move again pull that receiver carry the mouse up here and re-pair....never having to reboot.  the mini receivers stay in or at each pc and I have my functionality and a mouse that works for my ergonomics.

With the ability to do all the command bindings to mouse buttons readily available in Ubuntu, I can probably even find a way to use it to control audio playing from one room to another IF I can work out the pairing up issue.

Hey...I know that I'm asking for a lot and in some cases technology just isn't there yet....Learned that one about 15 years ago....but NOW they have caught up to some of those expectations.....I figure I always have something to look forward to this way!

---

### Post by Paddy Landau on 2011-06-16
Sorry, I've never used the technology you are talking about. I think you should start a brand new thread for that, in case someone can help solve your problem. Do so after you have successfully installed Ubuntu.

You may have to stick with a dual-boot to keep those functions.

---

### Post by smcrossman on 2011-06-16
Yes...this is quite off topic for this thread.  Thanks for your insights....I'll keep watching for anything that seems to be related to the install release....but I think I will back up Ubuntu and do a new, clean install this weekend. Just to be safe and sure that I'm good to go.

---

