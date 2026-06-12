---
title: "Dual boot issues  w/ external HDD."
date: 2010-11-21
forum: New to Ubuntu
---

### Post by skyler1 on 2010-11-21
HeyGuys, im not sure what to do, Dont know where to post this, but im really in panic right now, and i really need help
Im brand new to Linix and everything, and i know nothing, in terms (names of anything)

I am running Windows XP
So let me start from the beginning.
3 days ago i made the pendrive (the .iso on USB)
i booted off the pendrive
I installed Ubuntu on an external hard drive (its a 40G hard drive)
When i was booting off the pendrive i clicked install along side other operating system.
when i restarted my computer i got the 

error:device not found 
grub rescue>

then if i restart the computer, click F2 then exit,
it goes into a grub menu with the options of 
Ubuntu< with linix
Memory test 
Windows vista
Windows xp

so i click xp, and there is my computer

not all i want is no more linix, but i want to save my computer, without damaging it
i also want no more grum menu but im scared to wipe the external drive because if its not plugged in i get the 

error:device not found
grub rescure>

and i really dont know what to do


Please help, personal message or email me at [EMAIL="skylerschaap@hotmail.com"]skylerschaap@hotmail.com[/EMAIL]

Thank you so much

Skyler

I have a netbook (acer aspire one)
There is no CD drive

---

### Post by wilee-nilee on 2010-11-21
> **skyler1 said:**
> HeyGuys, im not sure what to do, Dont know where to post this, but im really in panic right now, and i really need help
Im brand new to Linix and everything, and i know nothing, in terms (names of anything)

I am running Windows XP
So let me start from the beginning.
3 days ago i made the pendrive (the .iso on USB)
i booted off the pendrive
I installed Ubuntu on an external hard drive (its a 40G hard drive)
When i was booting off the pendrive i clicked install along side other operating system.
when i restarted my computer i got the 

error:device not found 
grub rescue>

then if i restart the computer, click F2 then exit,
it goes into a grub menu with the options of 
Ubuntu< with linix
Memory test 
Windows vista
Windows xp

so i click xp, and there is my computer

not all i want is no more linix, but i want to save my computer, without damaging it
i also want no more grum menu but im scared to wipe the external drive because if its not plugged in i get the 

error:device not found
grub rescure>

and i really dont know what to do


Please help, personal message or email me at [EMAIL="skylerschaap@hotmail.com"]skylerschaap@hotmail.com[/EMAIL]

Thank you so much

Skyler

I have a netbook (acer aspire one)
There is no CD drive

So I have asked that this post be made in its own thread. so do as the other poster did click on the bootscript link in my signature, and run the commands just read the instructions and ask any questions needed. You will have generated a text file come back to the thread and and click on the # and paste the text in between.

If you are given a separate thread then PM me so I know where your at. Yeah a individual thread I have you in the auto email so run the script.;)

---

### Post by uRock on 2010-11-21
Bump for being moved to separate thread.

---

### Post by Iowan on 2010-11-21
Moved to separate thread.

---

### Post by wilee-nilee on 2010-11-21
You mods are so awesome.;)

---

### Post by skyler1 on 2010-11-21
I dont quite understand, how do i make this its own thread? 

I am running windows xp

---

### Post by wilee-nilee on 2010-11-21
> **skyler1 said:**
> I dont quite understand, how do i make this its own thread? 

I am running windows xp

Your already there, so just download the script drag it to the desktop, and paste this command into the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

A new file will magically appear come back to this thread and hit the # in the reply panel and paste all the text from that new file in between the code tags. If you look in my signature there is a example of code tags as well

---

### Post by uRock on 2010-11-21
Would the OP have to run that while running the LiveCD? That is if he/she can't boot into Ubuntu to run it?

---

### Post by beew on 2010-11-21
I am not very clear about what you're saying. Are you saying that now you cannot boot into Windows
without the external disk attached?

If you have a Windows XP install disk you can try removing the external drive, boot from the XP disk, choose repair windows (or something like that) and then enter the command ```
fixmbr
``` Then reboot without the CD into Windows. This should work.

I am afraid you have done it the wrong way, if I am not mistaken choosing "installing side by side" would install Ubuntu in the same dirve as Windows. You have to choose "advanced" and set up the partitions in your external drive manually and then in the last (second last? ) step choose advanced and install the bootloader into the external drive (with name like /dev/sdb, which you would know from earlier steps)

---

### Post by skyler1 on 2010-11-21
> **beew said:**
> I am not very clear about what you're saying. Are you saying that now you cannot boot into Windows
without the external disk attached?

If you have a Windows XP install disk you can try removing the external drive, boot from the XP disk, choose repair windows (or something like that) and then enter the command ```
fixmbr
``` Then reboot without the CD into Windows. This should work.

I am afraid you have done it the wrong way, if I am not mistaken choosing "installing side by side" would install Ubuntu in the same dirve as Windows. You have to choose "advanced" and set up the partitions in your external drive manually and then in the last (second last? ) step choose advanced and install the bootloader into the external drive (with name like /dev/sdb, which you would know from earlier steps)


Basically, if the external hard drive is not connected when i boot windows i get
error:device not found
grub rescue

and it wont boot, 

Its almost like my internal hard drive requires the external to boot

but what i dont get is i have /dev/sdb1/ which is my external
and /dev/sdb2/ which is my internal

---

### Post by wilee-nilee on 2010-11-21
> **uRock said:**
> Would the OP have to run that while running the LiveCD? That is if he/she can't boot into Ubuntu to run it?

You are correct, but they did have a thumb with Ubuntu loaded so I'm working with that information.

This is a netbook and no cd reader, so we have to be a bit creative here. To me it just looks like grub was installed in the HD of the computer not the external. can't tell without the script myself.

---

### Post by skyler1 on 2010-11-21
> **wilee-nilee said:**
> You are correct, but they did have a thumb with Ubuntu loaded so I'm working with that information.

This is a netbook and no cd reader, so we have to be a bit creative here. To me it just looks like grub was installed in the HD of the computer not the external. can't tell without the script myself.

explain in detail how to make the script, 
ill try

---

### Post by beew on 2010-11-21
yeah, your internal and external drive has "become one" so to speak. So the effect of removing the external would be the same as deleting the Ubuntu partition in a dual boot,--you remove the bootloader along with it,--and the fix would be the same.But if you don't have a CD drive and probably don't have a Windows disk this is beyond my knowledge to fix. I would be interested in learning from what others have to say.

---

### Post by skyler1 on 2010-11-21
> **wilee-nilee said:**
> You are correct, but they did have a thumb with Ubuntu loaded so I'm working with that information.

This is a netbook and no cd reader, so we have to be a bit creative here. To me it just looks like grub was installed in the HD of the computer not the external. can't tell without the script myself.

> **beew said:**
> yeah, your internal and external drive has "become one" so to speak. So the effect of removing the external would be the same as deleting the Ubuntu partition in a dual boot,--you remove the bootloader along with it,--and the fix would be the same.But if you don't have a CD drive and probably don't have a Windows disk this is beyond my knowledge to fix. I would be interested in learning from what others have to say.

so you are telling me the fix is get a external CD drive fun the windows cd, (whichone is that) and the click repair windows, then fixmbr?

---

### Post by wilee-nilee on 2010-11-21
> **skyler1 said:**
> explain in detail how to make the script, 
ill try

Go to this site and down load the boot script with the thumb, it will go to downloads, just drag that download to the desk top and run this command. 
Download this first:[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
then with the download on the desktop open a terminal from the menu-accessories and run this command in the terminal.

Copy and paste this command it is legit we use it all the time.

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will generate a file on the desktop full of text. Come back to the thread while still on the thumb, open a reply, and click on the # in the reply panel you will see code tags just paste all the scrpit in between.

---

### Post by skyler1 on 2010-11-21
> **wilee-nilee said:**
> Go to this site and down load the boot script with the thumb, it will go to downloads, just drag that download to the desk top and run this command. 
Download this first:[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
then with the download on the desktop open a terminal from the menu-accessories and run this command in the terminal.

Copy and paste this command it is legit we use it all the time.

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will generate a file on the desktop full of text. Come back to the thread while still on the thumb, open a reply, and click on the # in the reply panel you will see code tags just paste all the scrpit in between.


Command Prompt is that a terminal?

if it is it said its not a reconizable command

what does  thumb mean?

---

### Post by wilee-nilee on 2010-11-21
> **skyler1 said:**
> Command Prompt is that a terminal?

if it is it said its not a reconizable command

You have to have the download I put a link for on the desktop for the command to work. Did you do this and did you open the terminal in menu accessories?

---

### Post by uRock on 2010-11-21
> **skyler1 said:**
> Command Prompt is that a terminal?

if it is it said its not a reconizable command

what does  thumb mean?
Are you currently using Windows or Ubuntu. You have to be running Ubuntu for the commands to work.

---

### Post by wilee-nilee on 2010-11-21
The command is correct here is a screen shot of what you should see the terminal, and arrows pointing at the bootscript and the file generated for posting. Don't worry, we all start somewhere we just want to help if we can.;) Thumb is the pendrive just another name for a usb flash drive.
[ATTACH]176229[/ATTACH]

---

### Post by skyler1 on 2010-11-21
> **wilee-nilee said:**
> The command is correct here is a screen shot of what you should see the terminal, and arrows pointing at the bootscript and the file generated for posting. Don't worry, we all start somewhere we just want to help if we can.;) Thumb is the pendrive just another name for a usb flash drive.
[ATTACH]176229[/ATTACH]


i got the result.txt, what do i do now?

---

### Post by wilee-nilee on 2010-11-21
> **skyler1 said:**
> i got the result.txt, what do i do now?

highlight all the text and right click and click copy, the open a reply and click on the # you will see this [code ][/code ] just left click in between the code tags and right click paste. Your doing good I know this is confusing, it took me longer to figure it out then you have been at it.

---

### Post by skyler1 on 2010-11-21
> **wilee-nilee said:**
> highlight all the text and right click and click copy, the open a reply and click on the # you will see this [code ][/code ] just left click in between the code tags and right click paste. Your doing good I know this is confusing, it took me longer to figure it out then you have been at it.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb2 has 
                       297893887 sectors, but according to the info from 
                       fdisk, it has 297908609 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,840,063    74,838,016  83 Linux
/dev/sda2          74,842,110    78,139,391     3,297,282   5 Extended
/dev/sda5          74,842,112    78,139,391     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    14,683,409    14,683,347  12 Compaq diagnostics
/dev/sdb2    *     14,684,160   312,592,769   297,908,610   7 HPFS/NTFS

/dev/sdb2 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c99b9b64-02a8-4f1c-9f83-562f9f56a11a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d55745b4-15f9-48a3-a284-2fc53bebd28c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0280624D8062476F                       ntfs       PQSERVICE                     
/dev/sdb2        34EA6ADBEA6A993E                       ntfs       ACER                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c99b9b64-02a8-4f1c-9f83-562f9f56a11a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c99b9b64-02a8-4f1c-9f83-562f9f56a11a ro single 
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 0280624d8062476f
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 34ea6adbea6a993e
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=d55745b4-15f9-48a3-a284-2fc53bebd28c none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
  30.5GB: boot/initrd.img-2.6.35-22-generic
   2.3GB: boot/vmlinuz-2.6.35-22-generic
  30.5GB: initrd.img
   2.3GB: vmlinuz

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-11-21
So it looks like when you installed Ubuntu you  just didn't point the grub2 bootloader at the correct master boot record=MBR. You have Grub 2 the Ubuntu bootloader in the same HD as XP, and no bootloader in the external. so for the time being lets just get the bootloader on the external as it should be and put that HD to be read first in the bios. before I give you the instructions are you with me here?

---

### Post by skyler1 on 2010-11-21
> **wilee-nilee said:**
> So it looks like when you installed Ubuntu you  just didn't point the grub2 bootloader at the correct master boot record=MBR. You have Grub 2 the Ubuntu bootloader in the same HD as XP, and no bootloader in the external. so for the time being lets just get the bootloader on the external as it should be and put that HD to be read first in the bios. before I give you the instructions are you with me here?

Were going to get a bootloader in the external drive right

---

### Post by wilee-nilee on 2010-11-21
> **skyler1 said:**
> Were going to get a bootloader in the external drive right

Yes, hold on now for a few moments.;)

---

### Post by oldfred on 2010-11-22
I want to be sure which is the external and which is the internal. You have a 40GB drive and a 160GB drive. If the 40GB is the external it has reversed the normal numbering as the internal is normally sda. With both drives plugged in do you boot into Ubuntu ok when you choose in BIOS (or one time boot key like f12 on my system) to boot the 160GB drive?

Windows is installed in the 160GB drive and it has the UBuntu/grub boot loader. Ubuntu is installed in the 40GB drive and has no boot loader.

I would install grub to the 40GB drive which in the script is sda. After we have installed that and confirmed that it boots we can install a windows style boot loader to sdb the 160GB drive.

To install grub2 to sda. If you can currently boot.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

Reboot and in BIOS choose to boot the 40GB drive first and the 160GB second (which still does not have a boot loader). If and only if it boots ok then we will install lilo which works just like windows in booting from the MBR and will boot windows. We only want part of lilo that installs to the MBR.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by wilee-nilee on 2010-11-22
Just for the record the OP needs some sleep so we are going to continue tomorrow. the answers are all posted in post #26 so we just want to make sure everybody understands.;)

---

### Post by skyler1 on 2010-11-22
> **oldfred said:**
> I want to be sure which is the external and which is the internal. You have a 40GB drive and a 160GB drive. If the 40GB is the external it has reversed the normal numbering as the internal is normally sda. With both drives plugged in do you boot into Ubuntu ok when you choose in BIOS (or one time boot key like f12 on my system) to boot the 160GB drive?

Windows is installed in the 160GB drive and it has the UBuntu/grub boot loader. Ubuntu is installed in the 40GB drive and has no boot loader.

I would install grub to the 40GB drive which in the script is sda. After we have installed that and confirmed that it boots we can install a windows style boot loader to sdb the 160GB drive.

To install grub2 to sda. If you can currently boot.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

Reboot and in BIOS choose to boot the 40GB drive first and the 160GB second (which still does not have a boot loader). If and only if it boots ok then we will install lilo which works just like windows in booting from the MBR and will boot windows. We only want part of lilo that installs to the MBR.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR


The external is the 40g and the intrernal is the 160
Im really new at this, and i find it really confusing, im just going to ask if you can be really slow with me, because i have a very hard time with this all

thank you so much

---

### Post by oldfred on 2010-11-22
You need to install grub2 to the 40GB drive. Are you booted into Ubuntu or do you have to use liveCD?

---

### Post by skyler1 on 2010-11-22
> **oldfred said:**
> You need to install grub2 to the 40GB drive. Are you booted into Ubuntu or do you have to use liveCD?

booted in ubuntu, followed you instructions, i now have a boot loader on the external

how do i get one on windows so that i can boot even if the external isnt connected?

Please speak slow with me im new..

---

### Post by skyler1 on 2010-11-22
> **oldfred said:**
> You need to install grub2 to the 40GB drive. Are you booted into Ubuntu or do you have to use liveCD?

What should i do next?

---

### Post by oldfred on 2010-11-22
It makes a difference which commands to use depending on whether you are in the Ubuntu install on your 40GB drive or working off a liveCD. It is a little easier if you are just working from your Ubuntu install.

So which is it?

---

### Post by skyler1 on 2010-11-22
> **oldfred said:**
> It makes a difference which commands to use depending on whether you are in the Ubuntu install on your 40GB drive or working off a liveCD. It is a little easier if you are just working from your Ubuntu install.

So which is it?

I just booted ubuntu off my external hardrive

---

### Post by oldfred on 2010-11-22
From a terminal - Applications, Accessories, Terminal

Paste each of these lines that do not start with #, the # is a comment:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
```
sudo fdisk -l
```
#if it's "/dev/sda"  then just run:
```
sudo grub-install /dev/sda
```
#If that returns any errors run:
```
sudo grub-install --recheck /dev/sda
```
#Then:
```
sudo update-grub
```

If you get no errors, reboot and choose the external drive to boot from in BIOS.

---

### Post by skyler1 on 2010-11-22
> **oldfred said:**
> From a terminal - Applications, Accessories, Terminal

Paste each of these lines that do not start with #, the # is a comment:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
```
sudo fdisk -l
```#if it's "/dev/sda"  then just run:
```
sudo grub-install /dev/sda
```#If that returns any errors run:
```
sudo grub-install --recheck /dev/sda
```#Then:
```
sudo update-grub
```If you get no errors, reboot and choose the external drive to boot from in BIOS.


Alright done, i used all those commands, and i just booted off the external, it worked great,

Correct me if im wrong, but there is now a boot loader on the external drive rght.
whats next?

---

### Post by oldfred on 2010-11-22
We want to install a windows boot loader to the internal drive. Then without changing BIOS you can boot Ubuntu when external is plugged in and when it is not plugged in it defaults to the internal & boots windows.

While you can use windows tools to run a fixMBR, this works just as well. The windows boot loader just looks for the active (boot flag) partition and jumps to that partition to boot. The lilo boot loader does exactly the same thing, but we will not install the lilo code in the partition. It will give error messages about the rest of the code missing but we just want the part the will go into the MBR. 

You may want to double check with fidsk that the 160GB drive is still [COLOR=Red]sdb[/COLOR].

#Restore basic windows boot loader - universe enabled in system, administration software sources or Update Manager, settings.
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/[COLOR=Red]sdb[/COLOR] mbr
```#May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by skyler1 on 2010-11-22
> **oldfred said:**
> We want to install a windows boot loader to the internal drive. Then without changing BIOS you can boot Ubuntu when external is plugged in and when it is not plugged in it defaults to the internal & boots windows.

While you can use windows tools to run a fixMBR, this works just as well. The windows boot loader just looks for the active (boot flag) partition and jumps to that partition to boot. The lilo boot loader does exactly the same thing, but we will not install the lilo code in the partition. It will give error messages about the rest of the code missing but we just want the part the will go into the MBR. 

You may want to double check with fidsk that the 160GB drive is still [COLOR=Red]sdb[/COLOR].

#Restore basic windows boot loader - universe enabled in system, administration software sources or Update Manager, settings.
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/[COLOR=Red]sdb[/COLOR] mbr
```#May show error messages about the rest of lilo missing, ignore, we just want MBR

I dont really understand,  do i have to do anything before writing the commands in terminal

---

### Post by skyler1 on 2010-11-22
> **skyler1 said:**
> I dont really understand,  do i have to do anything before writing the commands in terminal


Also, does this make sence?

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb2 has 
                       297893887 sectors, but according to the info from 
                       fdisk, it has 297908609 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,840,063    74,838,016  83 Linux
/dev/sda2          74,842,110    78,139,391     3,297,282   5 Extended
/dev/sda5          74,842,112    78,139,391     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    14,683,409    14,683,347  12 Compaq diagnostics
/dev/sdb2    *     14,684,160   312,592,769   297,908,610   7 HPFS/NTFS

/dev/sdb2 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c99b9b64-02a8-4f1c-9f83-562f9f56a11a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d55745b4-15f9-48a3-a284-2fc53bebd28c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0280624D8062476F                       ntfs       PQSERVICE                     
/dev/sdb2        34EA6ADBEA6A993E                       ntfs       ACER                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c99b9b64-02a8-4f1c-9f83-562f9f56a11a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c99b9b64-02a8-4f1c-9f83-562f9f56a11a ro single 
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
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c99b9b64-02a8-4f1c-9f83-562f9f56a11a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 0280624d8062476f
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 34ea6adbea6a993e
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=d55745b4-15f9-48a3-a284-2fc53bebd28c none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
  30.4GB: boot/grub/grub.cfg
  30.5GB: boot/initrd.img-2.6.35-22-generic
   2.3GB: boot/vmlinuz-2.6.35-22-generic
  30.5GB: initrd.img
   2.3GB: vmlinuz

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-11-22
Only if you do not have Ubuntu set to also download from Universe. Most do.

If when you run the command it says not found then you do not have Universe enabled.

Run the commands and see what happens.

Boot script looks good. It shows grub in both sda & sdb. Once we install lilo you then should be able to boot sdb without sda being plugged in.

---

### Post by skyler1 on 2010-11-22
> **oldfred said:**
> Only if you do not have Ubuntu set to also download from Universe. Most do.

If when you run the command it says not found then you do not have Universe enabled.

Run the commands and see what happens.

Boot script looks good. It shows grub in both sda & sdb. Once we install lilo you then should be able to boot sdb without sda being plugged in.


This is what teminal showed 

```
sudo apt-get install lilo
[sudo] password for skyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 160 not upgraded.
skyler@skyler-Aspire-one:~$ sudo lilo -M /dev/sdb mbr
Backup copy of /dev/sdb in /boot/boot.0810
The Master Boot Record of  /dev/sdb  has been updated.
skyler@skyler-Aspire-one:~$ 

```

Is that good, what do i do?

---

### Post by skyler1 on 2010-11-22
> **skyler1 said:**
> This is what teminal showed 

```
sudo apt-get install lilo
[sudo] password for skyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 160 not upgraded.
skyler@skyler-Aspire-one:~$ sudo lilo -M /dev/sdb mbr
Backup copy of /dev/sdb in /boot/boot.0810
The Master Boot Record of  /dev/sdb  has been updated.
skyler@skyler-Aspire-one:~$ 

```Is that good, what do i do?

I dont know what you made me do, but that boot loader worked and i can boot windows without the external drive attached

It worked, Thank you so much

How do i call this thread soved :) 

is there anymore you want me to do

---

### Post by oldfred on 2010-11-22
Glad it worked.

Have you fully tested to see if you remove external it still works? That may depend on drive order settings in BIOS.

See my signature for instructions on solved.

If you have further questions on a new issue, you can start a new thread with a good title to attract users that know about that specific issue.

---

