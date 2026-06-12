---
title: "Linux File Systems and Applications"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by carl_76 on 2009-08-28
Hi.

I'm running 9.04 64bit on an amd64 laptop.  I set up my file system during installation as follows:

boot ~3GB
root ~3GB
home ~250GB (encrypted software raid w/2 external HDs)
swap ~32GB (encrypted)

I'm trying to install an engineering application (Xilinx ISE WebPack) and the installer defaults to this directory: /opt/Xilinx  It also tells me that there is only ~800MB of space left.  I imagine this is because I made the root directory too small.  I changed the directory to /home/carl/Xilinx and then the installer tells me that there are 0MB available which is far from true.  Is this because the home directory is not a valid location for applications?

Also, the file system browser shows a root directory next to a boot directory next to a home directory next to a bunch of other directories including the opt directory the isntaller wants to use.  Are all those other directories aside from home and boot really under the root directory and just displayed separately in the browser?

Is there a way to increase the size of the root partition by decreasing the swap partition without reinstalling?  I'm open to any suggestions to understand and address this problem.

Thanks.


Carl

---

### Post by louieb on 2009-08-28
I've never seen an encrypted swap partition, don't even know why you would do that. Or seen  someone put /home on an encrypted ra1d on external drives).  

With that in mind - if it were a normal install  you could use Gparted run from a live CD to resize partitions. 

[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by CatKiller on 2009-08-28
> **carl_76 said:**
> 
Also, the file system browser shows a root directory next to a boot directory next to a home directory next to a bunch of other directories including the opt directory the isntaller wants to use.  Are all those other directories aside from home and boot really under the root directory and just displayed separately in the browser?

They form a [filesystem]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") from /. Not /root, which is the *root user's* Home folder; something else entirely. Any folder could be on another drive, or another computer, or set up however you want. It's all quite flexible.

> 
Is there a way to increase the size of the root partition by decreasing the swap partition without reinstalling?

You certainly won't ever use that much swap. 2GB of swap is all most people are ever likely to need. You can resize partitions, but not from your Ubuntu install; you can't change a partition that's mounted, and that partition is necessarily mounted if you're running GParted from it. Boot from the live cd and change your partitions from that environment with the included partition editor. You'll need to **swapoff** if you're going to be changing the swap partition. Just right-click on the swap partition and you'll see the option.

---

### Post by oldfred on 2009-08-28
My boot (within root) is 880MB with 5 updates to the kernel. You can make it smaller or move it back into root so you can share space. If you move it you will have to reinstall grub to the MBR so it knows where to find the boot info. Root needs to be at least 10GB and if you are installing a lot of software even larger. 

I also keep /home in root but create a /data for just about everything except the config files Ubuntu wants in /home. That keeps /home small enough to easily backup and eliminates any issues of new versions having conflicts with the hidden config files. Others recommend the separate /home so the config and your data stays when you update.

If seems most desktop users using raid have issues. Linux works fine for raid in server configurations where a separate drive (non-raid) is used for booting. Raid may be overkill for the average desktop user. Backups & manual copies to another drive and DVD will normally suffice.

---

### Post by carl_76 on 2009-08-29
Hi.

Thank you for all the suggestions.  I ran into a problem and I also have a question.  First, though, I have the current setup for what I think are good reasons.  Since you know linux better than I you could probably have suggested another way to meet the same ends.  It's worked very well for me as far as meeting my needs, up until now.....

I booted from the LiveCD and used GPartEd to examine the laptop HD.  The encrypted swap space is shown as "unknown" and the only way to modify it is to delete it.  I imagine I can do that and then create a smaller swap, move the home directory over to occupy the free space, and then expand the root partition to allow program installation. 

Is this my best option or do you have other suggestions?

I imagine that if all works well the data on my home directory on the laptop HD will not be altered and that the raid setup with the external drives will not be affected.

Is that correct?

Thanks again for all the help.

Carl

---

### Post by louieb on 2009-08-29
I'm still unclear how your partitions are setup. For example I thought /home was on the external drives, now you say you have /home data on the internal.  Any alteration I suggest would be just guessing.

Please follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  with one exception - the instructions say to use the live CD. I would like you to **download and run the script from your hard drive instal**l.

Also it would be good to provide a screen shot of Gparted with the internal drive displayed. Press <Alt+PrintScreen> to capture just the Gparted window.

---

### Post by carl_76 on 2009-08-29
Hi.

Sorry I didn't explain the setup well.  I'm attaching the gparted screen captures and the beginning of the results.txt file.  If you really want to see the whole thing then I'll post it.

The setup is as follows:

Laptop Internal HD:
boot partition
root partition
home partition
swap partition

External HDs:
raid image of the home partition of the laptop internal HD

Attached are the gparted screen caps.  Note, sdd1, the second external HD is down at the moment.  It is another home image.

I believe it's the root partition I need to expand to make room for installing apps.  Which means I need to shrink the swap partition and move the home partition over.  Is that correct?

Below is the results.txt file beginning:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sda4: _________________________________________________________________________

    File system:       crypt_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypt_LUKS'

sdc1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c74badc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,767,519     9,767,457  83 Linux
/dev/sda2           9,767,520    19,535,039     9,767,520  83 Linux
/dev/sda3          19,535,040   508,007,429   488,472,390  fd Linux raid autodetect
/dev/sda4         508,007,430   625,137,344   117,129,915  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5a2e8d96

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002  fd Linux raid autodetect
```

Thanks for the help.

Carl

---

### Post by Liolikas on 2009-08-29
I believe it's the root partition I need to expand to make room for installing apps. Which means I need to shrink the swap partition and move the home partition over. Is that correct?

Yes. Basically you need:
swap for speed top you can check swap usage (how much you need) if swap full bad lag will appear. ~1Gb it should be. 100Mb-3Gb realistic size.
home for various files music etc.
root for Ubuntu and programs.
You have hundereds of Gb as I see but you gave way too small for root root should have something like 10-20Gb or even more.

---

### Post by louieb on 2009-08-29
> **carl_76 said:**
>   If you really want to see the whole thing then I'll post it.
Yea its long. Still want to see a couple of things - the content of /etc/fstab and the output of the mount command. Maybe something else. Please go ahead and put it all in your post.

---

### Post by carl_76 on 2009-08-29
Ok.  Here's the whole thing:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sda4: _________________________________________________________________________

    File system:       crypt_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypt_LUKS'

sdc1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c74badc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,767,519     9,767,457  83 Linux
/dev/sda2           9,767,520    19,535,039     9,767,520  83 Linux
/dev/sda3          19,535,040   508,007,429   488,472,390  fd Linux raid autodetect
/dev/sda4         508,007,430   625,137,344   117,129,915  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5a2e8d96

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a" TYPE="ext3" 
/dev/sda2: UUID="1755a90e-b45d-487c-96cd-302b55b13c4d" TYPE="ext3" 
/dev/sda3: UUID="c750f144-9e11-7878-7553-320f569f9d49" TYPE="mdraid" 
/dev/sda4: UUID="f1caa503-09be-4982-97e1-b76c101c0b3e" TYPE="crypt_LUKS" 
/dev/md0: UUID="f143e7cd-1adc-4cd7-98bf-6b89e4cf6e49" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="c750f144-9e11-7878-7553-320f569f9d49" TYPE="mdraid" 
/dev/mapper/sda4_crypt: UUID="60e0feb6-723d-4c90-8bc5-f58c10921823" TYPE="swap" 
/dev/mapper/md0_crypt: UUID="e1a1c195-4f1e-452e-9261-484765f6bb24" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/mapper/md0_crypt on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/carl/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carl)


============================= sda1/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
# kopt=root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-15-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-15-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-13-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-13-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


   2.4GB: grub/menu.lst
   2.4GB: grub/stage2
    .1GB: initrd.img-2.6.28-11-generic
    .0GB: initrd.img-2.6.28-13-generic
    .1GB: initrd.img-2.6.28-14-generic
    .0GB: initrd.img-2.6.28-15-generic
    .1GB: vmlinuz-2.6.28-11-generic
    .1GB: vmlinuz-2.6.28-13-generic
    .0GB: vmlinuz-2.6.28-14-generic
    .1GB: vmlinuz-2.6.28-15-generic

=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
# kopt=root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-15-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-15-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-13-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-13-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1755a90e-b45d-487c-96cd-302b55b13c4d ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=1755a90e-b45d-487c-96cd-302b55b13c4d /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=1e0e9737-6f5f-4e92-a1bb-cb290d28ca4a /boot           ext3    relatime        0       2
/dev/mapper/md0_crypt /home           ext3    defaults        0       2
/dev/mapper/sda4_crypt none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   7.4GB: boot/grub/menu.lst
   7.4GB: boot/grub/stage2
   5.1GB: boot/initrd.img-2.6.28-11-generic
   5.0GB: boot/initrd.img-2.6.28-13-generic
   5.1GB: boot/initrd.img-2.6.28-14-generic
   5.0GB: boot/initrd.img-2.6.28-15-generic
   5.1GB: boot/vmlinuz-2.6.28-11-generic
   5.1GB: boot/vmlinuz-2.6.28-13-generic
   5.0GB: boot/vmlinuz-2.6.28-14-generic
   5.1GB: boot/vmlinuz-2.6.28-15-generic
   5.0GB: initrd.img
   5.1GB: initrd.img.old
   5.1GB: vmlinuz
   5.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  3c a7 fd 52 f4 bf 81 50  09 29 27 b7 7b 6d 19 dd  |<..R...P.)'.{m..|
00000080  39 ed a8 bc 27 97 65 ab  ac f6 d4 95 32 61 83 90  |9...'.e.....2a..|
00000090  1a 23 7e 8c 60 c9 bb cc  94 06 a4 de 77 59 a4 48  |.#~.`.......wY.H|
000000a0  4c 23 67 f4 00 00 00 0a  38 31 64 62 38 62 37 34  |L#g.....81db8b74|
000000b0  2d 36 36 65 34 2d 34 32  38 35 2d 61 30 65 35 2d  |-66e4-4285-a0e5-|
000000c0  34 62 31 66 38 30 35 38  30 33 39 35 00 00 00 00  |4b1f80580395....|
000000d0  00 ac 71 f3 00 04 47 39  35 26 8a 93 10 4b 5e d4  |..q...G95&...K^.|
000000e0  36 74 b2 24 64 45 23 b2  9c 5a bc 96 15 fa 67 45  |6t.$dE#..Z....gE|
000000f0  7a 65 51 ef d2 9d 5b 80  00 00 00 08 00 00 0f a0  |zeQ...[.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sda4

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  81 49 c4 d7 85 6e e7 5f  3a b1 ad 99 a6 69 87 94  |.I...n._:....i..|
00000080  db 43 5c 25 f1 e3 05 91  1b bf 21 2d 5d 2d 44 fb  |.C\%......!-]-D.|
00000090  f2 85 6d d6 c5 45 59 57  e4 d0 e4 7d b5 d8 73 1d  |..m..EYW...}..s.|
000000a0  a2 34 7e e3 00 00 00 0a  66 31 63 61 61 35 30 33  |.4~.....f1caa503|
000000b0  2d 30 39 62 65 2d 34 39  38 32 2d 39 37 65 31 2d  |-09be-4982-97e1-|
000000c0  62 37 36 63 31 30 31 63  30 62 33 65 00 00 00 00  |b76c101c0b3e....|
000000d0  00 ac 71 f3 00 04 11 02  8a 5f df 95 12 2a fa ea  |..q......_...*..|
000000e0  d2 8b ae 12 a3 ed 26 e5  1b b9 70 91 a1 09 9e 32  |......&...p....2|
000000f0  ec c2 36 db 37 0c 37 18  00 00 00 08 00 00 0f a0  |..6.7.7.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdc1

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  3c a7 fd 52 f4 bf 81 50  09 29 27 b7 7b 6d 19 dd  |<..R...P.)'.{m..|
00000080  39 ed a8 bc 27 97 65 ab  ac f6 d4 95 32 61 83 90  |9...'.e.....2a..|
00000090  1a 23 7e 8c 60 c9 bb cc  94 06 a4 de 77 59 a4 48  |.#~.`.......wY.H|
000000a0  4c 23 67 f4 00 00 00 0a  38 31 64 62 38 62 37 34  |L#g.....81db8b74|
000000b0  2d 36 36 65 34 2d 34 32  38 35 2d 61 30 65 35 2d  |-66e4-4285-a0e5-|
000000c0  34 62 31 66 38 30 35 38  30 33 39 35 00 00 00 00  |4b1f80580395....|
000000d0  00 ac 71 f3 00 04 47 39  35 26 8a 93 10 4b 5e d4  |..q...G95&...K^.|
000000e0  36 74 b2 24 64 45 23 b2  9c 5a bc 96 15 fa 67 45  |6t.$dE#..Z....gE|
000000f0  7a 65 51 ef d2 9d 5b 80  00 00 00 08 00 00 0f a0  |zeQ...[.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by louieb on 2009-08-29
Looks like it would be safe enough to shrink sda1 down to 1GB or so. Maybe even to .5GB.  Then grow sda2 into the unallocated space. And they are small enough that it would not take long to make a partition image backup of sda1, sda2 and the MBR with partimage before you start.  At least you could get an extra 3GB or so that way.


> 
Is there a way to increase the size of the root partition by decreasing the swap partition without reinstalling? I'm open to any suggestions to understand and address this problem.
Just wondering is this raid0? raid1? or someother?
There might be but I just don't know enough about modify and moving partitions around that are part of an encrypted raid. sda3 is a part of the raid array and is in-between / (root) and swap. If they were normal ext3 formatted partitions you could shrink the swap partition, slide sda3 to the right, then grow sda2 into the unallocated space.

---

### Post by carl_76 on 2009-08-29
> **louieb said:**
> sda3 is a part of the raid array and is in-between / (root) and swap. If they were normal ext3 formatted partitions you could shrink the swap partition, slide sda3 to the right, then grow sda2 into the unallocated space.

Shrinking the swap and moving sda3 to the right and then growing sda2 is what I'd like to do.  It seems that gparted doesn't recognize the encrypted swap as swap so it won't let me resize it.  I'd just have to delete it, create a standard, smaller, swap and then shift sda3 right.  I'm concerned that the change to swap will completely wreck the system.  I think I may have to back up and reinstall.  I'm really hoping to avoid that, though.  Do you have any experience with deleting a swap and then creating a new one of a different size?

I didn't know the root partition was where applications went when I did this setup.  I just thought it was for root user data and since I'd never be working as root......

I installed the system this way because it seemed ideal for my needs and I was thinking I'd have to reinstall again for some reason or other, but everything was working so well that I just kept going with it.

The raid array is raid 1 with two copies of sda3 on external HDs.  Oh, sda3 and the mirrors are encrypted ext3.

---

### Post by louieb on 2009-08-29
Deleting the swap and creating a new smaller one is not a problem once the smaller one is created. Just have to update  /etc/fstab with the new location (if it changed).  
this line in /etc/fstab defines sda4 as swap 
```
/dev/mapper/sda4_crypt none            swap    sw              0       0
```Wonder if encrypted swap really works. please run
```
free -m
```the last line will tell you how much swap space the system sees and how much is being used.

---

### Post by carl_76 on 2009-08-29
Hi.

I don't see in fstab where it specifies the start location of the swap directory, or how it would know to maintain the encryption password after I deleted and recreated the swap.  I did find this, though, but have not read it yet:

[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

I'm not sure if it's what I'm looking for or not.

Here's the mem usage:

```
                      total       used       free     shared    buffers     cached
Mem:          2731        909       1821          0         24        322
-/+ buffers/cache:        563       2168
Swap:        57191          0      57191
```

As you can see I have 3GB of ram that I've hardly used.  Firefox, gnucash, and openoffice are hardly using it.  The swap is huge because when I set up the system I didn't know that the root was where the programs went and I had read something that said it only needed to be about 5GB so that's what I made it.  I made the laptop home the same size as the external drives I was using, 250GB, since it was a raid 1 setup I figured just keep them consistent.  I just used up the remaining free space with the swap.

---

### Post by louieb on 2009-08-29
Can't help with the encryption or what happens to the key if you delete swap and recreate it with encryption. But if you can do with an unencrypted swap then your /etc/fstab entry would look like
```
/dev/sda4 none            swap    sw              0       0
```Or once you delete sda4 you could use Gparted to copy sda2 to the now unallocated space - that would put a copy of your root partition in a new sda4  You can resize at the time of copy to take the whole 32GB of space. 

The main problem to solve if you do that is you will have 2 partitions with the same UUID. That is solved by using tune2fs to give one of them a new UUID.  

2 file would have to be updated with the new UUID /boot/grub/menu.lst and /etc/fstab.  
If you hibernate the computer there is a 3rd /etc/initramfs-tools/conf.d/resume

then after getting all that to work then you can reformat sda2 as swap.  

lol - this is getting kind of complicated.  I trust you have some way to at least to backup your data.

---

### Post by carl_76 on 2009-09-11
Hi.

I decided to reinstall since I wasn't too heavily invested in my previous installation.  I kept the same number of partitions and same structure but increased the size of the root partition and decreased the size of the swap.  I was able to install the application I needed to install after I did that.  

Thanks for all the help.

Carl

---

