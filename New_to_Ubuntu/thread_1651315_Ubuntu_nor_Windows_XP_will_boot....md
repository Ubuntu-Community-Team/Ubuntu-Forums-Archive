---
title: "Ubuntu nor Windows XP will boot..."
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Moulinoski on 2010-12-22
Ever since I installed Ubuntu Netbook Edition for my netbook, I've wanted to install Ubuntu on my slow PC- so I set out to do that.

After a couple of mishaps with the Linux Mint LiveCD putting my monitor to sleep, I used nomodeset and was finally able to get to Linux Mint's desktop- so I install it into a ~45 GB partition in my hard drive... but as fate would have it, my computer crashed. Sooo rather than try Mint again, I ran the Ubuntu LiveCD, used nomodeset again, and installed Ubuntu 10.10 on my PC, using the now empty partition that Mint was going to use. [This post]("http://ubuntuforums.org/showpost.php?p=9975074&postcount=13") helped me a lot.

I don't know how much of the above will be useful for the following... When I restarted my computer, ready to use Ubuntu, nothing happened. So I did some research and figured out how to fix the GRUB, so I did. Marvelous, it works now. So I try using Ubuntu, knowing full well that I'm going to have to press CTRL+ALT+F1 to bring up the terminal so my monitor doesn't fall asleep on me. So I boot ubuntu up and lo and behold, before I can do anything, my monitor falls asleep and I can't seem to get to the terminal (my monitor is in sleep mode anyhow, so maybe I do get to it, but don't know it).

Unhappy and frustrated, I decided to boot Windows XP (I did a dual boot, so I wouldn't lose XP since I still have a use for it). Nothing. It just kept flashing the "_" thing and the rest of the screen all black. After moments of waiting in vain, I turned my computer off. I turned it back on and decided to see if Window's recovery mode was still working. Hey, it was! So I did some hardware tests and they all passed on it... So I decided to try a System Restore on it- not the destructive kind, mind, but the kind that "turns back time" so to speak. Well, that had me reboot my computer and when it did, it seemed to have deleted GRUB...

So I again install GRUB but rather than go back and try it all again I decided to just leave this question here, see if someone else has already gone through this... I've gotten pretty tired of researching stuff (for today)...

**Question 1**: Is there any way that I can boot Windows XP again, preferably without losing any of my files on it, but pretty much everything is backed up so it's not THAT big a deal.

**Question 2**: Is there anything I can do to boot Ubuntu 10.10 on my desktop without it putting my computer to sleep? It doesn't seem like I can get the terminal up.

**Question 3**: If I can't get Ubuntu running on this computer, how can I fix this whole mess so my computer runs Windows XP again?

Fortunately, I can still boot the Ubuntu LiveCD (which is how I fixed the GRUB and how I'm typing all of this).

Some additional information:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18243   146534106    7  HPFS/NTFS
/dev/sda2           23166       24321     9283680    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           18243       23166    39539713    5  Extended
/dev/sda5           18243       18305      499712   82  Linux swap / Solaris
/dev/sda6           18306       23166    39038976   83  Linux

Partition table entries are not in disk order

```What I did to fix GRUB:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

```Thank you all in advance for helping me. Although I have Ubuntu Netbook Edition, I'm still not very well versed with the world of Linux (hence this problem, heh).

EDIT: Ha! So in the GRUB, I used 'e' to enter in options before booting Ubuntu and use nomodeset again, and it booted up perfectly! However, I'm afraid of testing out Windows XP now... :/ Anyways, I'm off to bed now. My head hurts from all this, haha.

SOLVED EDIT: This [post]("http://ubuntuforums.org/showpost.php?p=10274385&postcount=19") is what led me to the fix to my problem. Thank you so much oldfred, and also to meierfra..

---

### Post by wilee-nilee on 2010-12-23
Do the bootscript thang it will show what is where.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between. You can run the script from the Ubuntu install as well.

---

### Post by Moulinoski on 2010-12-23
I should mention I got Ubuntu working now that I installed the NVIDIA drivers, so it's just Windows now that needs fixing. Ubuntu is working perfectly now (meaning no LiveCD and no loud WRRRS :) ).

Here is the output of RESULTS.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sde2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sde3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   293,068,274   293,068,212   7 HPFS/NTFS
/dev/sde2         372,148,560   390,715,919    18,567,360   c W95 FAT32 (LBA)
/dev/sde3         293,068,798   372,148,223    79,079,426   5 Extended
/dev/sde5         293,068,800   294,068,223       999,424  82 Linux swap / Solaris
/dev/sde6         294,070,272   372,148,223    78,077,952  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sde1        E818426118422EBE                       ntfs       HP_PAVILION                   
/dev/sde2        4B6E-6BC0                              vfat       HP_RECOVERY                   
/dev/sde3: PTTYPE="dos" 
/dev/sde5        6790e3c9-99d8-4bc4-bc7a-29d80768c154   swap                                     
/dev/sde6        e7c63d69-45ea-4b94-8790-7d3156e123ac   ext4                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sde1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sde2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sde6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set e7c63d69-45ea-4b94-8790-7d3156e123ac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e7c63d69-45ea-4b94-8790-7d3156e123ac
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
    search --no-floppy --fs-uuid --set e7c63d69-45ea-4b94-8790-7d3156e123ac
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e7c63d69-45ea-4b94-8790-7d3156e123ac ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e7c63d69-45ea-4b94-8790-7d3156e123ac
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e7c63d69-45ea-4b94-8790-7d3156e123ac ro single 
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
    search --no-floppy --fs-uuid --set e7c63d69-45ea-4b94-8790-7d3156e123ac
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e7c63d69-45ea-4b94-8790-7d3156e123ac
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e818426118422ebe
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 4b6e-6bc0
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

=============================== sde6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e7c63d69-45ea-4b94-8790-7d3156e123ac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6790e3c9-99d8-4bc4-bc7a-29d80768c154 none            swap    sw              0       0

=================== sde6: Location of files loaded by Grub: ===================


 172.1GB: boot/grub/core.img
 185.2GB: boot/grub/grub.cfg
 151.6GB: boot/initrd.img-2.6.35-22-generic
 172.1GB: boot/vmlinuz-2.6.35-22-generic
 151.6GB: initrd.img
 172.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd 
```

---

### Post by Moulinoski on 2010-12-23
After running your bootscript program, I had Ubuntu update some programs and then restarted my computer. I noticed that Windows XP and its Recovery Mode were now in dev/sde rather than sda which is where they were...

---

### Post by oldfred on 2010-12-23
We have seen that many drives used by multi-card readers. Did you plug one in?

You have two XP boots listed, the second is your HP recover in sda2. Both Ubuntu and windows think they are installed to sda or drive 0. Ubuntu will work as it also does a search by UUID to find to boot partition. 

Not sure if there are any BIOS changes you can do to change drive order. My multi-card reader always comes up as drives after the hard drives, but I usually do not leave it plugged in.

---

### Post by Moulinoski on 2010-12-23
I'm not sure what you mean by multi-card reader... (do you mean the drive that can read SD, Memory Strick Pro, etc cards? In that case, it's plugged into the computer by default) In any case, I haven't plugged anything into my computer.

I took a peek into the BIOS before all of this and all I can do is change the boot device priority. My BIOS is a Pheonix - AwardBIOS.

How can I fix Windows and Ubuntu thinking they're both in sda1? (Actually, Windows XP and its recovery say they're both in sde now... /dev/sde1 and /dev/sde2).

Also, in GRUB, if I press 'e' while highlighting Windows XP (not the recovery one), it shows this:

```
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e818426118422ebe
drivemap -s (hd0) ${root}
chainloader +1
```Written by hand as best a I could (fortunately, I have this Netbook :) ).

---

### Post by oldfred on 2010-12-23
The boot stanza you posted is in the boot script results your posted above.

The drivemap command in combination with the search by UUID should let grub tell windows to be drive 0 or think it is and then it should work.

When you try to to the first XP entry what happens?

---

### Post by Moulinoski on 2010-12-23
Well, when I select Windows XP (/dev/sde1) from GRUB, all that happens is that there is an underscore '_' blinking in the upper left hand corner of the screen. I've left it there for long stretches of time and nothing happens.

Pressing 'e' while highlighting Windows XP and then pressing CTRL+X gives me the same thing.

Is that what you were asking?

---

### Post by oldfred on 2010-12-23
Yes, I was wondering if you were getting a windows error, or if grub knew something was wrong and returned to the grub menu.

All I can suggest is to experiment with alternatives. The search by UUID should find it. 

I would use e on the grub menu for edit and remove the search line and experiment with hdx numbers, first try the hd0, but use hd4 as in sde or possibly any other number from 0 to 5.

set root='(hd[COLOR=Red]0[/COLOR],msdos1)

I might also try it with and without the mapdevice line.

If you know drive & partition this boot works, so all the other lines are additions with grub2 to make it work 'better'.

menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

---

### Post by Moulinoski on 2010-12-23
Using hd0 and hd4 in set root and taking out drivemap -s (hd0) ${root} gave me the same result as before, just the underscore character blinking on the top left corner of the screen.

Changing hd0 to hd4 on both set root and drivemap gives me

```
A disk read error occurred
Press Ctrl+Alt_Del to restart
```

Doing so just reboots my computer.

Only changing set root gives me the same result as before (the underscore result).

I tried CTRL+C to enter a grub command line and typing in what you wrote but nothing either.

I also tried to write the grub command in the OS selection screen by pressing c. Nothing either.

---

### Post by oldfred on 2010-12-23
When you took out the mapdevice line did you also remove the search line. The search line overrides the set root, if it is found, but some have issue.

Do you have a floppy drive? Do you have a floppy drive configured in BIOS? If no drive and in BIOS, I would remove it from BIOS. But that usually is a grub boot issue.

---

### Post by Moulinoski on 2010-12-23
Taking out the search and mapdevice commands and set root=hd4 gives me

```
  Boting a command list
error: hd4, msdos1 cannot get C/H/S values.
Press any key to continue..._
```Pressing any key sends me back to Windows XP's command line entry. Pretty much the only key that still functions there is ESC which sent me back to the OS select screen. Pressing e here highlights the bottom most option (Windows XP Recovery). I pressed the arrow keys, but nothing happened, however, either the left or right arrow keys booted Ubuntu...

Doing the same as above but leaving set root=hd0, gives me the same result as before (the underscore blinking).

I do not have a floppy drive, however, it was in the boot devices list. I removed it.

After doing that, I highlighted Windows XP and simply pressed ENTER. Blinking underscore again.

Taking off the search and mapdevice lines, and set root=hd1, it gave me the error from before when I tried hd4.

Just to confirm that what I have been doing is okay, you've wanted me to highlight Windows XP (/dev/sde1), press 'e' while highlighting it, and then going from 

```

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e818426118422ebe
drivemap -s (hd0) ${root}
chainloader +1
```to
```

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
chainloader +1
```and experimenting with hd0, correct?

---

### Post by oldfred on 2010-12-23
Yes, but it is just an experiment.

But, the chs error looks interesting. You should not be using chs values at all. cylinders, heads, sectors. That was before LBA or large block allocation for hard drives. LBA has been used for about 10 yrs as drives exceeded chs values.

I would check BIOS settings. I have had posts with these comments. See if any apply.
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode

---

### Post by Moulinoski on 2010-12-23
None of them apply... I think.

In my computer's BIOS, with blue meaning editable options and gray noneditale, under Main:
[COLOR=RoyalBlue]
System Time
System Date
Language [English (US)]

First Channel Device 0 [Memorex DVD+-R]
First Channel Device 1 [None}

Secondary Channel Device 0 [ST3200827AS]
Third Channel Device 0 [None][/COLOR]

[COLOR=Silver]Installed Memory 512 MB/PC2-4200
Memory Bank 1 512 MB/DR2 SDRAM
Memory Bank 2 Not Installed

BIOS Revision 3.04 09/07/2006
Core Version 6.0

[COLOR=Black]Under Advanced,

[COLOR=Silver]Setup Warning

CPU Type AMD Athlon(tm) 64 processor 3500+

CPU Speed 2200 MHz
Cache RAM 512 KB
[COLOR=RoyalBlue]Plug and Play OS [Yes]
Primary Video Adapter [PCI] [COLOR=Black]Can choose Onboard as option[/COLOR]
PS/2 Mouse [Auto Detect]
Onboard 1394 [Enabled]
USB Legacy Mode Support [Enabled]
Onboard LAN [Enabled]
Onbaord LAN Boot ROM [Disabled]
Local Bus IDE Adapter [Primary] [COLOR=Black]Can choose Disabled as option[/COLOR]
SATA1 Controller [Enabled]
Onboard Audio [Auto]
[COLOR=Silver]Superviser Password Disabled
User Password Disabled

[COLOR=Black]Then there's Power (both blue):
After AC Power Failure [Auto]
WOL in S4 [Disabled]

Then Boot,

Boot-time Diagnostic Screen [Enabled]
Boot Device Priority

And finally, Exit.
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by oldfred on 2010-12-23
Really old systems only booted primary master which was set with jumpers on hard drive or cable select by location on cable.

You have your DVD on first channel and Hard drive on secondary. With SATA, BIOS were updated to allow you to boot just about anything, so it should not really matter. But I might try switching hard drive & DVD connectors on motherboard. Again this is just a test and if you are not comfortable doing that, you do not have to as it is probably not the solution. But I am also running out of ideas.

Are your drives IDE and how are jumpers set?

---

### Post by Moulinoski on 2010-12-23
I can't  seem to change the order they're in, although in Boot Device order, the HDD comes before the DVD Drive. Also, in Secondary Channel Device 0 > there's Smart Support... Smart Status Check, Smart Short/Extended Self-Test.

The only mention I see of IDE anything is in the two First Channel Devices, but I honestly don't know what it means in this context, nor do I know what you mean by jumpers.

Edit: Should I try running the Windows Recovery program? At least that works (although I might have to fix grub using a LiveCD...

---

### Post by oldfred on 2010-12-23
That was my next suggestion. To make sure windows still works you can run the windows repairs and directly boot it. Possibly run chkdsk also. Then reinstall grub2, if windows boots ok several times.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r


XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

Sometimes just rerunning all the fixes realigns something, but there are no guarantees. We have many who dual boot from one drive. I have multiple drives so I keep windows XP on one to avoid issues.

---

### Post by Moulinoski on 2010-12-23
Hmm, wait a second... I have a Recovery Partition for XP- can I just use that? Or must I use this Windows XP bootloader CD? I don't get any command prompts in my recovery partition either.

Oh, press R. My bad. X_x

Edit: Hmm, I tried pressing R... But nothing happens.

Actually, now that I see it, it's HP PC Recovery... And I don't have any CD for loading Windows (it came preinstalled on my computer). I could always try Googling the disk itself... Or, I have my dad's computer which is also an XP computer- could I use that computer to make a Recovery CD from it?

Edit: I found [this]("http://ubuntuforums.org/showpost.php?p=4691608&postcount=2") while searching for a Windows XP Bootloader I can use... Meh, that failed... I guess I'll just have to wait to get my hands on the bootloader.

Edit: Wait! It seems I needed a file for the above to which I just got (it was at the end of the instructions, how nice >_>; Well, better somewhere than no where). Something's happening now, so let's see...

Edit: Bah, it ended with E: Unable to locate package ms-sys... I guess I'll just go to sleep and wait for the Bootload CD to "arrive".

BTW, just to clarify: When I asked if I could just start the Recovery partition, I meant do a destructive recovery on it...

---

### Post by oldfred on 2010-12-24
XP computers used to come with the CD. It was when they went to Vista that you stopped getting CDs and only got a partition on the hard drive with a image of the system, not a DVD. Some will also let you create a repair CD, but not usually with XP.

You can download a win7 repair CD, but only use it to run chkdsk. Any other repairs may corrupt it more.

There are some good instructions here using Vista to replace XP MBR:
[http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html](http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html)


But all the other repairs you can do from Ubuntu.

from meierfra - Fixboot is supposed to do the same thing, but it just fails from while to while.
Us synaptic to download testdisk:
How to fix XP/Vista/7 when the boot files are missing meierfra
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
[URL="http://ubuntuforums.org/showthread.php?t=1423998"]
[/URL]

---

### Post by Moulinoski on 2010-12-24
Okay, I used a Windows 7 installation disk that I had lying around (that wasn't the disk I was "obtaining" yesterday, but seeing as it's already available...), I hit Shift+F10 to get a command prompt and wrote in chkdsk. Here's the output as best as I can copy it by hand:

```
X;\Sources>chkdsk
The type of the file system is NTFS.
The volime is in use by another process. Chkdsk
might report errors when no corruption is present.
Volume label is Boot.

WARNING! F parameter not specified.
Running CHKDSK in read-onl mode.

CHKDSK is verifying files (stage 1 of 3)...
  29 file records processed.
File verification completed.
  0 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.

CHKDSK is verifying indexes (stage 2 of 3)...
  43 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  29 file SDs/SIDs processed.
Security descriptor verification completed.
  7 data files processed.
Windows has checked the file system and found no problems.

3086 KB total disk space.
4 KB in 9 indexes.
0 KB in bad sectors.
2485 KB in use by the system.
2048 KB occupied by the log file.
597 KB available on disk.

512 bytes in each allocation unit.
6173 total allocation units on disk. 
1195 allocation units available on disk.
Failed to transfer logged messages to the event log with status 50.

```

Wait a second though... 3086 KB total disk space? O_o What is this doing? Anyways that's the output for chkdsk. I'll try repairing Windows through Linux following your steps.

---

### Post by oldfred on 2010-12-24
Because you did not specify a drive or parameter, it defaulted to the current device. That may have just been the CD?

---

### Post by Moulinoski on 2010-12-24
Yeah that's what I thought, but I didn't know how to specify the drive. Either way, I followed the instructions on the link you posted and I am hapy to say that I have Windows XP and Ubuntu running together on my PC! :D Although, something happened to my system restore points, but no biggie- at least most of my installed programs are still there although now I have to uninstall the useless garbage that the computer came with (like HP Games >_>).

Thank you, thank you, thank you so much!! :D I have edit the first post to add in [Solved], right?
Edit: D'oh, I should have followed the link in your signature. X_X

---

### Post by oldfred on 2010-12-25
Glad your system is working.:)

---

