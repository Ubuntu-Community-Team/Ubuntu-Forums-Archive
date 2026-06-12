---
title: "Windows 7 went &quot;invisible&quot; after installing Ubuntu 10.10"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by ChickenMcFail on 2011-01-10
So recently I ordered a Ubuntu 10.10 Live CD. I recieved it today and I went to installing it straight away. So I chose the Advanced Partitioning option. Here, I'll tell you the details of each partition I had:

1. Windows 7 - 150GB of which 40GB used - It contains Windows 7. I gave it too much space but screw it, it doesn't matter.
2. Games, Programs, Downloads - 500GB of which 350GB used - The partition where I always installed and downloaded everything when I was using Windows 7
3. Linux - 50GB of which 0GB used - Made this partition exclusively for Ubuntu
4. Swap - 100mb - The swap partition

Obviously I chose the Linux partition to be the one where I install Ubuntu. Had some problems because I didn't understand the prompts about the root and swap stuff but I googled these and got through these with no problem. Installation was easy and quick. At the end of it I rebooted the computer. When I logged into my brand new Ubuntu account I thought to myself 'how come I didn't get a dual boot screen' but quickly came to conclusion that there must have been one and I just subconciously went through it. But then I rebooted it again and realized that... there IS no boot screen. Inserted my Windows 7 CD to boot from it, but for some reason instead booting from the Windows 7 CD I get the Grub boot screen where I got to choose between... Ubuntu 10.10 and Ubuntu 10.10 (recovery key something something).
I still have the Windows 7 drive INTACT but I can't boot Windows 7 from it.
I googled around for help but only two or three people had the SAME problem as me and they were on an outdated linux version where they had the "menu" file in the /boot/grub/ location.
Can someone explain to me how I can recover my Windows 7?

---

### Post by s.fox on 2011-01-10
Thread moved to  [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by hansolo4949 on 2011-01-10
Try running sudo update-grub2 in your terminal, and tell us if windows poppes up upon reboot after that.

hansolo4949

---

### Post by ChickenMcFail on 2011-01-10
Don't know if it's because of the "update-grub2" command but now I just go straight to Ubuntu even with the Windows 7 CD inside the CD drive.
And yes, I did set booting from CD in BIOS.

Also, by "terminal" did you mean the ALT+F2 thing?
If no, then tell me how to access it please.

---

### Post by Synthetic Sam on 2011-01-10
> **ChickenMcFail said:**
> Don't know if it's because of the "update-grub2" command but now I just go straight to Ubuntu even with the Windows 7 CD inside the CD drive.
And yes, I did set booting from CD in BIOS.

Also, by "terminal" did you mean the ALT+F2 thing?
If no, then tell me how to access it please.
Press Ctrl+Alt+T then type:
```
sudo update-grub
``` then reboot the system and see if you get your grub menu with Windows 7 on it.

---

### Post by ChickenMcFail on 2011-01-10
I'm still going straight into Ubuntu :(
Is there any way to FORCE grub?

---

### Post by Synthetic Sam on 2011-01-10
> **ChickenMcFail said:**
> I'm still going straight into Ubuntu :(
Is there any way to FORCE grub?
GRUB must be running for you to boot to ubuntu, but I would suggest that it hasn't found your windows installation, and that's why it is skipping the boot menu.

You could try holding shift while booting, and see if windows is in the GRUB menu that appears.

Alternatively post the output of the terminal from the command that I gave before.

---

### Post by ChickenMcFail on 2011-01-10
[[IMG]http://img89.imageshack.us/img89/8192/screenshotdr.th.png[/IMG]](http://img89.imageshack.us/img89/8192/screenshotdr.png)
Uploaded with [ImageShack.us](http://imageshack.us)
Here's a screenshot of what shows up after the command.
It doesn't detect the Windows image in the other partition :(

---

### Post by 67GTA on 2011-01-10
Windows is a PITA when it comes to this. I can't count the number of windows installs I've screwed because resizing the partition moved some "precious" system file. First make sure it is still there. Post the output of ```
sudo fdisk -l
``` If this shows your NTFS partition, then you probably just moved some system files. You can also install gparted to get a graphical view of your partitions.

---

### Post by ChickenMcFail on 2011-01-10
[[IMG]http://img214.imageshack.us/img214/6290/screenshot1u.th.png[/IMG]](http://img214.imageshack.us/img214/6290/screenshot1u.png)
I never resized anything.
I made a linux partition before I even got the Live CD.

---

### Post by TechWiz2100 on 2011-01-10
Grub will always show regardless of how many options there are and Ubuntu install always creates 2 options, Ubuntu and Ubuntu Recovery Mode

I think he needs to re-install grub

---

### Post by wilee-nilee on 2011-01-10
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Do this we are really not going to get to the bottom of this without the information provided in the by file generated by running the script. W7 is probably missing the boot files, due to a partition removal most likely, the script will tell us.

---

### Post by ChickenMcFail on 2011-01-10
Here you go
Also, I don't need to boot Ubuntu from a CD. It is installed and it works fine (although I don't have sound for some strange reason).
It's the Windows 7 that's "invisible". :(

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800  82 Linux swap / Solaris
/dev/sda2             206,848   304,742,399   304,535,552   7 HPFS/NTFS
/dev/sda3         304,744,446   409,599,999   104,855,554   f W95 Ext d (LBA)
/dev/sda5         304,744,448   409,599,999   104,855,552  83 Linux
/dev/sda4         409,600,000 1,465,145,343 1,055,545,344   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9923cb87-5e40-419a-818d-34277d4c2d6c   swap                                     
/dev/sda2        EC7E6AFE7E6AC146                       ntfs       Windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2A6E17626E17265B                       ntfs       Games, Programs, Downloads    
/dev/sda5        b9017f23-59a9-473e-ab50-3c9f7987578a   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sda2        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9017f23-59a9-473e-ab50-3c9f7987578a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9017f23-59a9-473e-ab50-3c9f7987578a ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 186.3GB: boot/grub/core.img
 186.3GB: boot/grub/grub.cfg
 156.8GB: boot/initrd.img-2.6.35-22-generic
 186.3GB: boot/vmlinuz-2.6.35-22-generic
 156.8GB: initrd.img
 186.3GB: vmlinuz
```

---

### Post by 67GTA on 2011-01-10
Open gparted in Ubuntu and make sure the ntfs partition has the "boot" option checked. To do this, right click on the ntfs partition and select "manage flags". If it wasn't already checked, check it and rerun ```
sudo update-grub
``` If the boot flag is already checked, then we can try adding windows to grub manually and see if it will boot.

---

### Post by ChickenMcFail on 2011-01-10
Where is gparted?
I looked in System>Administration and System>Preferences and didn't find it. Maybe I was stupid and missed it?

---

### Post by hansheijmans on 2011-01-10
You should probably perform a recovery of your Windows 7 boot, using the W7 install disc. Then you can "recover" from this recovery by re-installing grub2, without harming your Ubuntu installation.

See attachment (I prefer the chroot method).

---

### Post by ChickenMcFail on 2011-01-10
The thing is, I can't boot from the Windows 7 disc. It goes straight to ubuntu. Doesn't matter if I set it in the BIOS to boot from CD.

---

### Post by wilee-nilee on 2011-01-10
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
     Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

As I suspected when you removed another partition you removed the highlighted files. So first imstall gparted in Ubuntu, open it right click on sda2 then flg then click boot. Then use a W7 recovery or install disc to do this.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:

BootRec.exe /FixBoot (#updates PBR partition boot)

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is a W7 recovery/repair disc link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by wilee-nilee on 2011-01-10
double post

---

### Post by hansheijmans on 2011-01-10
> **ChickenMcFail said:**
> The thing is, I can't boot from the Windows 7 disc. It goes straight to ubuntu. Doesn't matter if I set it in the BIOS to boot from CD.

Can you try booting and press some sort of boot option key (e.g. F8 with AMI BIOSes) during POST? Or maybe your W7 CD (or DVD) is corrupt?

---

### Post by 67GTA on 2011-01-10
> **ChickenMcFail said:**
> Where is gparted?
I looked in System>Administration and System>Preferences and didn't find it. Maybe I was stupid and missed it?
Sorry, you have to install it. Open the software manager and look for it. wilee-nilee's last post is where I was headed. Follow his last post.

---

### Post by hansheijmans on 2011-01-10
The ability to boot from CD/DVD is the key now! Wilee-nilee's method looks fine to me to repair W7 boot.

---

### Post by ChickenMcFail on 2011-01-10
> **wilee-nilee said:**
> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
     Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

As I suspected when you removed another partition you removed the highlighted files. So first imstall gparted in Ubuntu, open it right click on sda2 then flg then click boot. Then use a W7 recovery or install disc to do this.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:

BootRec.exe /FixBoot (#updates PBR partition boot)

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is a W7 recovery/repair disc link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Thank you so much.
I've checked the boot thing in gparted (downloaded it through the Ubuntu Software Centre).
Downloading the repair disc right now. Considering the speed of my internet this may take some time.
If it won't finish today, I'll bump the thread tommorow with a double post and say whether it worked or not ;)

---

### Post by TechWiz2100 on 2011-01-10
Some BIOS allow you to press keys like F8 or F12 to give you a menu of devices that you can boot from and force boot from that device vs booting thru the boot list. Also removing your hard drive from the list of bootable devices in BIOS should help you get to that Live CD

---

### Post by florus on 2011-01-10
The swap partition should not be set as the boot partition.

---

### Post by ChickenMcFail on 2011-01-11
All right, I did everything right up to the part where I boot from CD.
I just go straight into the grub thing now, again. I have no idea what's happening.
The CD drive just gets completely ignored :( What can be wrong?

EDIT: I also know that the CD Drive works... If I insert the Ubuntu 10.10 Live CD, it boots from it perfectly fine. It's just that if I insert a Windows 7 Install Disc or Windows 7 Recovery Disc, it doesn't boot from it. :(

---

### Post by wilee-nilee on 2011-01-11
> **ChickenMcFail said:**
> All right, I did everything right up to the part where I boot from CD.
I just go straight into the grub thing now, again. I have no idea what's happening.
The CD drive just gets completely ignored :( What can be wrong?

EDIT: I also know that the CD Drive works... If I insert the Ubuntu 10.10 Live CD, it boots from it perfectly fine. It's just that if I insert a Windows 7 Install Disc or Windows 7 Recovery Disc, it doesn't boot from it. :(

There is a out of the bios boot from menu, mine is f12 with this key prompt immediately at powering on, if you can find your that may be what is needed. Also see if that disc will boot on another computer if not then it may be the cd.

---

### Post by ChickenMcFail on 2011-01-11
I was really stupid. The CD was indeed damaged to the point that it didn't work.
I borrowed someone else's Windows 7 CD. I managed to boot using it.
So I got to the language selection screen, pressed ENTER and then (because it's a Windows 7 install disc, not Windows XP) I had a graphical display. I had the choice between "Install Windows 7" and "Repair Windows 7".
I chose the Repair Option. The program started looking for an installation of Windows 7 on my HDD. After it found it, it told me that the boot or something is damaged and asked me if I want to repair it and restart. Of course I clicked YES.
My computer restarted, I changed the boot from CD to Hard Drive and... it went into the Grub. And I -again- had the choice between Ubuntu and Ubuntu recovery mode.
Decided to boot from CD again, I chose the "repair windows 7" option again and in the Installation list it did list "Windows 7 Ultimate (recovered)".
Why can't I boot it? Is there still something wrong? I feel so hopeless :(

Also, thanks for the help people, I can see that the Linux community is much better at explaining problems even though Windows is much simpler to explain :)



EDIT: I figured the updated bootscript results may prove useful (or not, but worth posting it anyway, can't hurt)
I've noticed that there is a bit of stuff added in the Windows 7 drive. Not sure if it makes any difference though:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800  82 Linux swap / Solaris
/dev/sda2    *        206,848   304,742,399   304,535,552   7 HPFS/NTFS
/dev/sda3         304,744,446   409,599,999   104,855,554   f W95 Ext d (LBA)
/dev/sda5         304,744,448   409,599,999   104,855,552  83 Linux
/dev/sda4         409,600,000 1,465,145,343 1,055,545,344   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9923cb87-5e40-419a-818d-34277d4c2d6c   swap                                     
/dev/sda2        EC7E6AFE7E6AC146                       ntfs       Windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2A6E17626E17265B                       ntfs       Games, Programs, Downloads    
/dev/sda5        b9017f23-59a9-473e-ab50-3c9f7987578a   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9017f23-59a9-473e-ab50-3c9f7987578a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9017f23-59a9-473e-ab50-3c9f7987578a ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 186.3GB: boot/grub/core.img
 186.3GB: boot/grub/grub.cfg
 156.8GB: boot/initrd.img-2.6.35-22-generic
 186.3GB: boot/vmlinuz-2.6.35-22-generic
 156.8GB: initrd.img
 186.3GB: vmlinuz
```

---

### Post by wilee-nilee on 2011-01-11
Your closer look at the Windows 7 link, it is a visual look at getting to the command line on the booting the W7 disc. Then run the command I listed, your still missing the high lighted part.sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   :   **/bootmgr**/Boot/BCD /Windows/System32/winload.exe

Here is the instructions again copy them and look at the W7 forum link it is the same as the instructions here to get to that W7 terminal. Don't just try what you think will work follow these instructions to the letter.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) **Select the command prompt (console) and type in the following command**
```

BootRec.exe /FixBoot
``` 
[B]
Look at this link to get orientated on getting to the command line.[/B]
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by ChickenMcFail on 2011-01-11
That's the problem D:
At this bit:
[IMG]http://www.sevenforums.com/attachments/tutorials/25674d1251414836-mbr-restore-windows-7-master-boot-record-mbr_04.png[/IMG]
If I select "Windows 7 Ultimate (recovered)" and press NEXT it says something about the version on the CD/DVD not being the same version as Windows on my HDD (both are "Windows 7 Ultimate" though).
I can't get past that bit, therefore I can't get into the Command Prompt.
This is ridiculous but what can I do :(

---

### Post by wilee-nilee on 2011-01-11
> **ChickenMcFail said:**
> That's the problem D:
At this bit:
[IMG]http://www.sevenforums.com/attachments/tutorials/25674d1251414836-mbr-restore-windows-7-master-boot-record-mbr_04.png[/IMG]
If I select "Windows 7 Ultimate (recovered)" and press NEXT it says something about the version on the CD/DVD not being the same version as Windows on my HDD (both are "Windows 7 Ultimate" though).
I can't get past that bit, therefore I can't get into the Command Prompt.
This is ridiculous but what can I do :(

You can make a good burn of the recovery disc and use it.

---

### Post by Quackers on 2011-01-11
What happens if you click on NEXT in that screen? Windows has partly repaired the boot sector. Re-running startup repair once or maybe twice may be enough to repair Windows.

---

### Post by ChickenMcFail on 2011-01-11
> **Quackers said:**
> What happens if you click on NEXT in that screen? Windows has partly repaired the boot sector. Re-running startup repair once or maybe twice may be enough to repair Windows.
Nope.
Tried it. The first time I ran repair it automatically located a problem and fixed it.
To fully fix it I need to choose the top option and press "Next" but I can't.

Also, for some reason I can't burn a good copy of the recovery disc. I just can't boot from it.
I'll try again with another CD but it will most likely not work :( I'm so close to fixing it, thanks to you guys, but I can't... :(

EDIT: I know why it says it's a wrong version. My Windows 7 is 32 bit, the CD I have contains 64 bit Windows 7.
Now I know the cause but it doesn't help me at all :(

---

### Post by wilee-nilee on 2011-01-11
> **Quackers said:**
> What happens if you click on NEXT in that screen? Windows has partly repaired the boot sector. Re-running startup repair once or maybe twice may be enough to repair Windows.

After thinking and knowing now that this is W7 ultimate, the swap replaced the original windows 200Mib boot partition. This boot partition is really used in the Ultimate version as part of the encryption. So if the user is actually only able to get to this screen with another ultimate disc that may be the cause.

I will have to go to school and will be gone soon for about 9-10 hours so it is good to see you on to help, as always.:)

---

### Post by Quackers on 2011-01-11
I don't understand. By recovery disc do you mean repair disc (I know Windows calls it a recovery dsic)? A Windows Vista/7 repair disc? If you can't boot from it, how did you get to the screen you posted a screenshot of?

---

### Post by ChickenMcFail on 2011-01-11
> **wilee-nilee said:**
> After thinking and knowing now that this is W7 ultimate, the swap replaced the original windows 200Mib boot partition. This boot partition is really used in the Ultimate version as part of the encryption. So if the user is actually only able to get to this screen with another ultimate disc that may be the cause.

I will have to go to school and will be gone soon for about 9-10 hours so it is good to see you on to help, as always.:)
Thank you :P
I've edited my previous post right before your post... I know why the "versions" are different.
Still doesn't help me though. I need a working CD :s

---

### Post by ChickenMcFail on 2011-01-11
> **Quackers said:**
> I don't understand. By recovery disc do you mean repair disc (I know Windows calls it a recovery dsic)? A Windows Vista/7 repair disc? If you can't boot from it, how did you get to the screen you posted a screenshot of?

I got that using the Windows 7 Ultimate **64bit Install** disc. Because it's 64bit I cannot get past that screen as my Windows 7 is 32bit.
My Windows 7 Ultimate **32bit** Install disc is not working so I can't use it.
My Windows 7 Recovery/Repair 32bit disc I downloaded and burned onto a CD isn't working as well.

I'm stuck until I don't get a working 32bit repair or install disc.
Sucks to be me.

---

### Post by Quackers on 2011-01-11
Yes, wilee-nilee, no problem:-)
The swap partition has undoubtedly over-written the first 2 Windows boot files.
Also the boot flag needs to be on sda2, not sda1, unless that has already been changed.

---

### Post by ChickenMcFail on 2011-01-11
> **Quackers said:**
> Yes, wilee-nilee, no problem:-)
The swap partition has undoubtedly over-written the first 2 Windows boot files.
Also the boot flag needs to be on sda2, not sda1, unless that has already been changed.
It has been changed to sda2.
sda1 is the swap partition
sda2 is the windows partition
sda3 is... I have no idea what it is. Gparted says it's 50gb just like my linux partition but it appeared from nowhere
sda4 is my general files partition, where I install everything on Windows
sda5 is my linux partition

---

### Post by Quackers on 2011-01-11
> **ChickenMcFail said:**
> I got that using the Windows 7 Ultimate 64bit INSTALL disc.
My Windows 7 Ultimate **32bit** Install disc is not working so I can't use it.
My Windows 7 Recovery/Repair 32bit disc I downloaded and burned onto a CD isn't working as well.

I'm stuck until I don't get a working 32bit repair or install disc.
Sucks to be me.

Just to get things straight, so you have 32 bit Windows 7 installed but only have a working 64 bit installation disc? That won't work, I don't think.
Your 32 bit repair download needs to be burned as an image (if it's an .iso file) not just burnt to disc - are you aware of that?

---

### Post by ChickenMcFail on 2011-01-11
> **Quackers said:**
> Just to get things straight, so you have 32 bit Windows 7 installed but only have a working 64 bit installation disc? That won't work, I don't think.
Your 32 bit repair download needs to be burned as an image (if it's an .iso file) not just burnt to disc - are you aware of that?
Yes, I am aware of that :p
I'm not new to computers. I'd call myself pretty damn experienced.
But Linux is just completely new to me.
I know that I cannot put the .iso file onto the CD and burn it. You burn everything that's inside the .iso file.

---

### Post by Quackers on 2011-01-11
Well, you burn the .iso file as an image using ImgBurn or similar in Windows or Brasero in Ubuntu.

---

### Post by wilee-nilee on 2011-01-11
> **ChickenMcFail said:**
> Yes, I am aware of that :p
I'm not new to computers. I'd call myself pretty damn experienced.
But Linux is just completely new to me.
I know that I cannot put the .iso file onto the CD and burn it. You burn everything that's inside the .iso file.

W7 has a built in cd burner right click the ISO then burn to cd it is that simple. **Oops** except you can't get into W7 my mistake carry on.:)

---

### Post by ChickenMcFail on 2011-01-11
Joke's on you, I have another PC with Windows 7 installed!
And I did use that built-in iso burner last time, that's why it didn't work. I just checked and it showed that the CD is **still empty**. That may explain why I couldn't boot from it...
This time I "unrar'ed" these files and copied them on the CD, then commanded Windows to burn these on the CD. Now it shows that they're there. I'll reboot right now and try to boot from the CD. Wish me luck! ;)

---

### Post by Quackers on 2011-01-11
Good luck :-)

---

### Post by ChickenMcFail on 2011-01-11
Well whoop-dee-doo, I still can't boot the repair disc despite the files physically being there.
I am not enjoying this :|

---

### Post by wilee-nilee on 2011-01-11
Were on your side ChickenMcfail, good luck. I don't think that will work if not just right click on the ISO in that W7 set up then burn to cd.

---

### Post by Quackers on 2011-01-11
Lol, here's another way of making the disc.
In your other Windows 7 machine (assuming it is running the 32 bit version!) go to Control Panel, then to Backup & Restore Centre. In the left pane you will see an option to "create a Windows (or system) recovery disc". Put a cd in the drive and click on that option. That should get you a bootable repair disc.

---

### Post by ChickenMcFail on 2011-01-11
Aww God, I'm the most unlucky person ever...
The other Windows is 64bit...

---

### Post by Quackers on 2011-01-11
Do you have a close neighbour with either 32 bit Vista or Win 7 :-)

---

### Post by ChickenMcFail on 2011-01-11
Nope.
I'm trying to find a GOOD iso burning software so this time the Recovery CD will work.
Know of anything?

---

### Post by ChickenMcFail on 2011-01-11
Double post

---

### Post by Zero2Nine on 2011-01-11
> **ChickenMcFail said:**
> Nope.
I'm trying to find a GOOD iso burning software so this time the Recovery CD will work.
Know of anything?

For Windows? ImgBurn. [http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by Quackers on 2011-01-11
From inside Windows I have had no problems with ImgBurn. It's a free program available for download here
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)

Don't click on the big arrow, that's for driver checking software. Download from the different language sections below.

If this doesn't work we may have to try Lilo.

---

### Post by ChickenMcFail on 2011-01-11
All right, before both of your posts I downloaded "Free Image Burn Wizard" from FreeVideoAudioSoft (I think).
Burned the iso into the CD and... it works!
I got into the console this time, used that command, and it said something along the lines of "operation completed"!
...but I still get the grub. And I still only have a choice between Ubuntu and Ubuntu Recovery thing.

WHAT AM I DOING WRONG? D:


EDIT: Updated bootscript results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800  82 Linux swap / Solaris
/dev/sda2    *        206,848   304,742,399   304,535,552   7 HPFS/NTFS
/dev/sda3         304,744,446   409,599,999   104,855,554   f W95 Ext d (LBA)
/dev/sda5         304,744,448   409,599,999   104,855,552  83 Linux
/dev/sda4         409,600,000 1,465,145,343 1,055,545,344   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9923cb87-5e40-419a-818d-34277d4c2d6c   swap                                     
/dev/sda2        EC7E6AFE7E6AC146                       ntfs       Windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2A6E17626E17265B                       ntfs       Games, Programs, Downloads    
/dev/sda5        b9017f23-59a9-473e-ab50-3c9f7987578a   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Repair disc Windows 7 32-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9017f23-59a9-473e-ab50-3c9f7987578a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9017f23-59a9-473e-ab50-3c9f7987578a ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9017f23-59a9-473e-ab50-3c9f7987578a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 186.3GB: boot/grub/core.img
 186.3GB: boot/grub/grub.cfg
 156.8GB: boot/initrd.img-2.6.35-22-generic
 186.3GB: boot/vmlinuz-2.6.35-22-generic
 156.8GB: initrd.img
 186.3GB: vmlinuz
```

Did ANYTHING change?

---

### Post by Quackers on 2011-01-11
Maybe nothing. The repair program can only repair one thing at a time. You had 2 boot files missing, so the first repair fixed one of them (I hope that wasn't 64 bit!) and now the second time hopefully repaired the second file. Try running startup repair one more time and reboot. Hopefully Windows will then boot by default. Even if it doesn't there are still options :-)

---

### Post by ChickenMcFail on 2011-01-11
I told it to AutoFix any problems with starting Windows. Seems like it was doing something but it didn't work.
I booted it from CD again to retype that command into console again:
```
BootRec.exe /FixBoot
```
This too, didn't work.
:(

Gonna go to sleep now (it's 22:49 in UK). Will be back tommorow afternoon (GMT time) again, if anyone has any more ideas, post them. Everything's appreciated ;)

---

### Post by Quackers on 2011-01-11
From the command prompt in the repair console you can run
```
bootrec.exe /fixmbr
```
please note the space between exe and /fixmbr

I'm in the UK too :-)

---

### Post by ChickenMcFail on 2011-01-11
I was lurking for the next 10 minutes as I was getting ready to go to sleep.

And so I used that command... and... it worked!
I'm in Windows 7! WOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO :D

Thanks to everyone in the thread :D
The best thing in Linux is it's community. You people are so helpful!
You have no idea how happy you made me!

__[****]("http://[URL")**** This is now the soundtrack of my life: [http://www.youtube.com/watch?v=DuDeBcpLITQ](http://www.youtube.com/watch?v=DuDeBcpLITQ)__[URL="http://www.youtube.com/watch?v=DuDeBcpLITQ"]
[/URL]

---

### Post by Quackers on 2011-01-11
Lol, luvverly :-)
 You realise of course that grub now need to be re-installed so that Ubuntu will boot up? That's not a major problem.
You will need to boot from the Ubuntu live cd/usb and select "try Ubuntu". When the desktop loads go to Applications menu > Accessories > Terminal and click on that.
In the terminal please copy/paste the following commands in to the terminal, one at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
then reboot and Ubuntu will boot directly. When the desktop arrives you should open up a terminal and run ```
sudo update-grub
``` and watch to see that the Windows loader (/dev/sda2) is found, as grub.cfg is run.
If it is, reboot to your shiny new grub menu and select Windows and confirm it boots ok.
Then go and have a party :-)

---

### Post by ChickenMcFail on 2011-01-11
Thank you again!
Everything works perfectly! :)

EDIT: Now I'll finally go to sleep without worrying about Windows and Linux. Thanks yet again! :P

---

### Post by Quackers on 2011-01-11
Aha! Now go to sleep :-) You'll sleep better now!
You're welcome.

---

