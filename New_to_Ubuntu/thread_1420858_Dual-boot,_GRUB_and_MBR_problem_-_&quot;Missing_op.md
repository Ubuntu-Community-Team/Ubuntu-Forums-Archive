---
title: "Dual-boot, GRUB and MBR problem - &quot;Missing operating system&quot;"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by seymur on 2010-03-03
I will start from the beginning, it is a little bit confusing, but this is my last hope because I was checking lots of threads, forums, posts for last two days.
In the beginning I had C:, D: - Vista, E:.
C - Physical Disk 1, D and E - Physical Disk 2
I installed Windows 7 to C:, but did not delete Vista fully from D:. Somehow Windows 7 boot record was installed to D: (Vista). I tried to fix it but was not successfull, I just copied some boot folders to C:, but _Win 7 boot record was still on D:_.

_Here comes the main part._ I decided to format D: and install Ubuntu on it.
I made 3 partitions in D; one root, one for /home, and one for swap. (ext4)
So far everything was perfect, my notebook was loading with GRUB, and there was Windows 7 option also.
After using Ubuntu for 2 days I decided to check Win 7, but it said it couldn't load. Then I decided to fix this;
1) I tried bootmgr rebuild and other suggested methods, no good.
2) I tried to change active disk, no good (I couldnt change active disk, stayed the same)
3) I deleted Boot folder in C:

_After that when I try to boot computer it says "Missing operating system", it does not load GRUB._ What I have already checked:

1) My GRUB is in the same place as before, in the root partition. I didnt touch it.
2) I checked grub.cfg file, it was same as when it was working.

My questions:
1) When computer boots, does it first read GRUB or it first loads some windows boot thing and from it it starts GRUB? Because if it is the case, then it means that there is a problem with Master Boot Record, that's why I cannot run GRUB. I just want to make sure the source of the problem.
2) Since my root is separate from my home (different partitions), if I again install Ubuntu on root, will my applications (Firefox add ons for instance), Desktop customizations deleted? Will this fix the GRUB problem?
3) Any suggestions? Please help :)

Thanks for reading. I am noob in Ubuntu (and in Linux), and I am not an IT guy, so sorry for any stupid questions, but I really did my research and tried some solutions (which ironically ended up with worse situation).

---

### Post by seymur on 2010-03-03
This is the result from Boot info Script


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x780b4fe1

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000   7 HPFS/NTFS
/dev/sda2    *      3,084,480    33,350,939    30,266,460  83 Linux
/dev/sda3          33,350,940   197,631,629   164,280,690   5 Extended
/dev/sda5          33,351,003    36,178,379     2,827,377  82 Linux swap / Solaris
/dev/sda6          36,178,443   197,631,629   161,453,187  83 Linux
/dev/sda4         197,634,048   390,719,487   193,085,440   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d379805

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   390,721,535   390,719,488   f W95 Ext d (LBA)
/dev/sdb5               4,096   390,721,535   390,717,440   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0CB6A02FB6A01AEA                       ntfs       WinRE                         
/dev/sda2        1a5813f4-94b9-4d53-b551-1ddd334085d8   ext4                                     
/dev/sda4        D092A54792A53340                       ntfs       Movies                        
/dev/sda5        966a1384-540d-4031-a1f0-ee9b9b37b9f6   swap                                     
/dev/sda6        c83b74ab-5399-41b2-a5bb-51a4a5243dc0   ext4                                     
/dev/sdb5        7C7656F77656B19E                       ntfs       Docs                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /media/1a5813f4-94b9-4d53-b551-1ddd334085d8 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb5        /media/Docs              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/WinRE             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /media/c83b74ab-5399-41b2-a5bb-51a4a5243dc0 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda4        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 1a5813f4-94b9-4d53-b551-1ddd334085d8
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 1a5813f4-94b9-4d53-b551-1ddd334085d8
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=1a5813f4-94b9-4d53-b551-1ddd334085d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 1a5813f4-94b9-4d53-b551-1ddd334085d8
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=1a5813f4-94b9-4d53-b551-1ddd334085d8 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 1a5813f4-94b9-4d53-b551-1ddd334085d8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1a5813f4-94b9-4d53-b551-1ddd334085d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 1a5813f4-94b9-4d53-b551-1ddd334085d8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1a5813f4-94b9-4d53-b551-1ddd334085d8 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb5)" {
    insmod ntfs
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 7c7656f77656b19e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=1a5813f4-94b9-4d53-b551-1ddd334085d8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=c83b74ab-5399-41b2-a5bb-51a4a5243dc0 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=966a1384-540d-4031-a1f0-ee9b9b37b9f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   6.0GB: boot/grub/core.img
   5.1GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-14-generic
   5.8GB: boot/initrd.img-2.6.31-19-generic
   3.9GB: boot/vmlinuz-2.6.31-14-generic
   5.3GB: boot/vmlinuz-2.6.31-19-generic
   5.8GB: initrd.img
   4.2GB: initrd.img.old
   5.3GB: vmlinuz
   3.9GB: vmlinuz.old

```

---

### Post by louieb on 2010-03-03
Your Win7 install is missing files  [COLOR=Red]/bootmgr and /Boot/BCD 
[/COLOR] sorry but don't know how to get them back. Might try the [Vista Recovery Disc &#8212; NeoSmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") believe it works for Win7 too.

Before you try use Gparted and  remove the boot flag from sda2 and turn on the boot flag on sdb5 (Your win7 partition). 

You have the Windows boot loader installed in the MBR of both drives. Your getting the missing operating system  probably because of the missing files or the MBR is still pointing to your now deleted Vista partition. 

Looks like the Linux root is in [COLOR=Red]sda2[/COLOR] - you can fix GRUB and Ubuntu - not to reinvent the wheel - take a look at the [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")  it has a section on how to fix the MBR to boot GRUB again.

---

### Post by oldfred on 2010-03-03
Follow louieB advice and just reinstall grub to get your system working. 

To understand what windows is doing it may be useful to understand how windows combines boots:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You also have win7 on an extended partition which makes it difficult to boot. Windows does not work from that but combines its boot into a primary partition and is booting from that. A few of the really knowlegable folks here do have workarounds to make it boot, but it is not easy.

Easiest to to install both windows in primary partitions separately.
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by seymur on 2010-03-03
Thank you very much for your replies. So now I am in the beginning where I was before Grub was down.
Before posting here I tried to re-install Grub, but in terminal it didn't even recognize grub command. Probably I used some old version Grub command.

Anyway, now it loads Grub normally as before, I have too Ubuntus, one is 2.6.31-19 generic, and the other one is -14 generic . I don't know why this is the case, but it was like this before, and I always start Ubuntu 2.6.31-19 generic. Then I have Windows 7 Loader (on dev/sdb/5).
When I try to load Windows 7, it again shows "BOOTMGR is missing".
Before Grub went down, I was trying to fix this problems, used conventional methods but it didn't work (the problem is sdb is somehow locked, to run even chkdsk it says it must be unmounted). I tried through Win 7 recovery comman prompt, bootrec commands. I will try again.
_So my problem is that Boot folder and bootmgr file is not in sdb5_ (i.e. where my Windows 7 is). Because when I installed Win 7 stupid windows put it is boot in Vista boot.
If I solve this then I guess my Win 7 will start.

Questions:
1) About partition, in Gparted, sdb5 is shown in one level under sdb1. It says sdb1 is Extended, then what is sdb5? Is it logical or primary or extended? First I need to know this to start working on bootmgr problem.

[IMG]http://img198.imageshack.us/img198/6519/screenshot1fi.png[/IMG]

2) Also can I put bootmgr in some other partition (primary ntfs, for instance sda4), and direct Grub to boot Windows 7 from there?

---

### Post by seymur on 2010-03-03
I came accross with similar problem in some other forum;
> "When you deleted the XP partition, you removed the boot code from your computer. Now your Windows 7 partition is a "Logical" partition inside an "Extended" partition and cannot boot, even if it had the boot code. I would suggest the simplest repair would be to use GParted to extend the 7.84MB unallocated space to a 100MB primary, active, system partition and follow this from MS to create the 100MB bootable "Reserved System" partition. Then you will have the ability to boot to Windows 7 again."In my case it is Vista partition I deleted. So maybe I should try this. This is basically what I thought to do, to allocate boot to another primary place.

---

### Post by seymur on 2010-03-04
After 6 hours I was able to start Windows 7. The problem with conventional methods was the following;
I have two active partitions (on separate disks). In Primary disk the active partition is Ubuntu. So when I was trying to "startup repair win 7", or to do bootrec operations it was always looking into system (i.e. active) partition Ubuntu. And always showed error related to volume problem, file system problem.
I ran bootsec with /force. Then using Partition Boot Loader _I deactivated Ubuntu partition, so that I had only left with Win 7 active partition._ Then booted with Win 7 disk, and it corrected partition table. [U]After that I again made Ubuntu partition active using Partition boot loader.
Now when I turn on the computer if I choose first harddisk then I load GRUB -> Ubuntu,
If I select second harddisk it loads Windows 7.[/U]

Now in my GRUB there is no Windows 7 entry, so I cannot load Win 7 from GRUB. I am not so keen to reinstall GRUB in case it may mess up win 7 loading. I don't know exactly. I would be glad if somebody helped me to add Win 7 line to GRUB so that I can load win 7 from GRUB. I will check also how to do it. Except this last problem, my main problem is solved, so I will wait some time to see about GRUB, then the thread can be closed (solved).

---

### Post by louieb on 2010-03-04
Nice to see you got both working.
GRUB2 has one great feature. - adding another OS to its menu.
```
sudo update-grub
```

Its the recommended way to modify /boot/grub/grub.conf

---

### Post by seymur on 2010-03-04
> **louieb said:**
> Nice to see you got both working.
GRUB2 has one great feature. - adding another OS to its menu.
```
sudo update-grub
```Its the recommended way to modify /boot/grub/grub.conf

I used that command. It is really great, it directly found Windows 7 on sdb1 (before it was sdb5). Thanks for the help! :) Now everything's back to normal.

One more question, in Grub2 I have _two Ubuntus_, and recovery modes of each. Is it normal? One is** 2.6.31-19 generic**, and the other one is **2.6.31-14** **generic**.

---

### Post by louieb on 2010-03-04
Two or more Ubuntu entries is normal. Every time there is a kernel update you'll get another entry. 

Unlike most updates where the old get replaced but new - when there is kernel update the old one does not get replaced. The Linux kernel is the heart of the OS.  Its a backup for you to use if the updated kernel fails. 

There are ways to limit the number of kernels displayed in the menu - I don't bother - the newest will always be at the top and the default.

---

### Post by Roger Allott on 2010-03-04
> **seymur said:**
> 
One more question, in Grub2 I have _two Ubuntus_, and recovery modes of each. Is it normal? One is** 2.6.31-19 generic**, and the other one is **2.6.31-14** **generic**.

Completely normal. If you want to remove an old linux kernel, you can use Synaptic, but the best method seems to be Ubuntu-Tweak - an excellent program that really ought to be part of the standard Ubuntu install.

The stock advice I've got from folk here is to keep the latest kernel (obviously!) and the most recent legacy kernel, and remove all others just for good housekeeping and tidiness reasons.

This morning, a new kernel (2.6.31-20) came up on Update Manager, so it would seem sensible for you to run Update Manager (and then rebooting) before running Ubuntu-Tweak.

---

### Post by seymur on 2010-03-04
Thanks a lot everybody for help. So it is normal to have other kernels. I will update and then install tweak.
I really like Ubuntu, I think I will stick to it for a long time.
Thread can be marked as solved :)

---

