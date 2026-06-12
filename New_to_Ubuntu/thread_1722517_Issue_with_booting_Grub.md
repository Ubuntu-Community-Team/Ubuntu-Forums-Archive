---
title: "Issue with booting Grub"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by hockeyplaya7 on 2011-04-05
Hello any help with this topic is much appreciated...
Ok my situation is kind of complicated and i'll explain as best as I can...
I have a Dell 15R laptop with Windows 7 and Ubuntu dual booted onto it...
I recently was having issues with the Grub and the boot loading and found out I had to do the whole booting from live CD and all the terminal stuff involved with rebooting grub correctly...I managed to do all of that and delete the Dell Datasafe...
After that I got grub to work and confirmed that everything was working on my laptop...
I was exploring the Drive in the Drive Manager in Windows 7 when I discovered I had accidentally installed two of the same Ubuntu drive...One of them was incomplete as I must have loaded it wrong from the CD...Using Drive Manager I deleted this Ubuntu part...
Now i reboot my computer and it loads to the GRUB command line screen...It displays
GNU GRUB version 1.98+20100804
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
grub>_
Any help is much appreciated...

---

### Post by sandyd on 2011-04-05
> **hockeyplaya7 said:**
> Hello any help with this topic is much appreciated...
Ok my situation is kind of complicated and i'll explain as best as I can...
I have a Dell 15R laptop with Windows 7 and Ubuntu dual booted onto it...
I recently was having issues with the Grub and the boot loading and found out I had to do the whole booting from live CD and all the terminal stuff involved with rebooting grub correctly...I managed to do all of that and delete the Dell Datasafe...
After that I got grub to work and confirmed that everything was working on my laptop...
I was exploring the Drive in the Drive Manager in Windows 7 when I discovered I had accidentally installed two of the same Ubuntu drive...One of them was incomplete as I must have loaded it wrong from the CD...Using Drive Manager I deleted this Ubuntu part...
Now i reboot my computer and it loads to the GRUB command line screen...It displays
GNU GRUB version 1.98+20100804
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
grub>_
Any help is much appreciated...
boot using a livecd
run this in the terminal
```

wget -c http://iweb.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh
chmod 777 boot_info_script055.sh
bash ./boot_info_script055.sh

```
and post output

---

### Post by hockeyplaya7 on 2011-04-05
Thank you for responding! attached is the Results that you requested...

---

### Post by lindsay7 on 2011-04-05
I think you just need to recover grub. Here are the instructions for doing this,

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by Quackers on 2011-04-05
Your boot script in code tags, so others can read it
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   6 FAT16
/dev/sda2             206,848    30,926,847    30,720,000   7 HPFS/NTFS
/dev/sda3          30,926,848   383,600,326   352,673,479   7 HPFS/NTFS
/dev/sda4         383,600,638   976,771,071   593,170,434   5 Extended
/dev/sda5         584,232,960   960,770,047   376,537,088  83 Linux
/dev/sda6         960,772,096   976,771,071    15,998,976  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DELLUTILITY                   
/dev/sda2        CC70378A703779F2                       ntfs       Recovery                      
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f0cd8976-3d77-4142-919a-d476eff63376   ext4                                     
/dev/sda6        4476c33f-0bf2-4b6e-b974-b6b793848efa   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f0cd8976-3d77-4142-919a-d476eff63376 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4476c33f-0bf2-4b6e-b974-b6b793848efa none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 398.0GB: boot/grub/core.img
 398.0GB: boot/vmlinuz-2.6.35-22-generic
 398.0GB: vmlinuz
```

Was Windows booting from the grub menu previously?
It appears that you are missing a grub boot file from your sda5 partition.
Has the system booted at all since you repaired grub?

---

### Post by hockeyplaya7 on 2011-04-06
I have solved the issue...
I used a Ubuntu LiveCD to boot into Ubuntu...I then deleted my versions of Ubuntu...(I think they were installed incorrectly and therefore there were issues with it...)
I then downloaded a Windows 7 startup disc and did a Startup Repair...Now it loads from what it used to...
I'm going to attempt to install Ubuntu again and see what happens now...

---

