---
title: "Ubuntu 9.04 grub error :15 &quot;menu.lst&quot; is missing &amp; kernel files missing"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Thyagaraj on 2010-06-09
Ubuntu 9.04 grub error :15
"menu.lst" is missing under /boot/grub/
kernel files are missing(vmlinuz...)
I've installed the grub by the following:

grub>root (hd0,4)
grub>setup (hd0)

grub installed successfully......

but if type
grub>boot

the message I'm getting is "Kernel must be loaded"
if i try,

grub>kernel vmlinuz......
no kernel files found under /boot

I tried to upgrade to 9.10 booting from 9.04 live cd but the prompt i got is "No free disk space"(it might be looking space only in the cd)

plz... any one help me

---

### Post by mikewhatever on 2010-06-09
From the live cd, post the output of **sudo fdisk -l**.
Note, you can not upgrade while running from the Live cd. Reinstall is a different story, but you probably don't want to do that.

---

### Post by kansasnoob on 2010-06-09
Please use a Live CD to run the Boot Info Script and post it's results as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Thyagaraj on 2010-06-10
> **kansasnoob said:**
> Please use a Live CD to run the Boot Info Script and post it's results as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)







                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 110284371 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f865

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,204,419    78,204,357  83 Linux
/dev/sda2          78,204,420   312,576,704   234,372,285   5 Extended
/dev/sda5          78,204,483   138,753,404    60,548,922  83 Linux
/dev/sda6         138,753,468   218,821,364    80,067,897  83 Linux
/dev/sda7         218,821,428   312,576,704    93,755,277  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4db0adc6-cb4c-4152-adc9-1087f1cced1f   ext3                                     
/dev/sda5        3baed96a-f2b5-403d-8924-f193eed232d1   ext3                                     
/dev/sda6        e55191b7-0983-4641-ace1-077545567d5f   ext3                                     
/dev/sda7        8cc5a5e3-b1be-4513-8b40-bffebe08d0b1   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


=================== sda5: Location of files loaded by Grub: ===================


  56.5GB: boot/grub/stage2

---

### Post by Thyagaraj on 2010-06-15
plz... I need help in recovering my system from grub problem....
please help me any one.

---

### Post by I8NY on 2010-06-15
you can get super grub boot loader and that might boot Ubuntu but may not fix grub.  But when i get grub errors i have done a reinstall of ubuntu :(

---

### Post by Thyagaraj on 2010-06-15
I can't reinstall my system as it's my company's. It has lot of applications installed on it

---

### Post by louieb on 2010-06-15
Sorry to say but the boot info script shows the install has more than GRUB problems.  

No kernels listed  - bad news not going to boot without one.

No /etc/fstab - lets the kernel (if you had one) - know where the root file system is. - without it all you'll get is the busy box prompt.   

In some cases it is possible to copy missing files from a live CD - but wonder what else is missing. Not that easy  and /etc/fstab will certainly need to be modified by hand.       

Normally don't want to recommend it  - but in this case - the easiest path to recovery is to backup any application data and do a fresh install.

---

