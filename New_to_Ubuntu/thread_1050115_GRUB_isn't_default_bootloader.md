---
title: "GRUB isn't default bootloader"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by mmitt on 2009-01-25
How can I make GRUB the default one? Mine uses the Vista-Longhorn bootloader at startup and if I choose ubuntu, then it goes to GRUB. Can I just skip the Vista one? I just installed with wubi.
Thanks!

---

### Post by diablo75 on 2009-01-25
Don't think so; not with a Wubi install.  Next best thing you might do is edit your /boot/grub/menu.lst file as root and reduce the count down timer to something short, if not 0 seconds so you won't be bothered by the menu.  In Applications>Accessories>Terminal:

```
sudo gedit /boot/grub/menu.lst
```

Look for the line that says "timeout 10" or something like that.

Change the 10 to something smaller, like 3 or 2 or whatever you want.

---

### Post by mmitt on 2009-01-25
> **diablo75 said:**
> Don't think so; not with a Wubi install.  Next best thing you might do is edit your /boot/grub/menu.lst file as root and reduce the count down timer to something short, if not 0 seconds so you won't be bothered by the menu.  In Applications>Accessories>Terminal:

```
sudo gedit /boot/grub/menu.lst
```

Look for the line that says "timeout 10" or something like that.

Change the 10 to something smaller, like 3 or 2 or whatever you want.
No I'm serious. It goes first to Vista-Longhorn bootloader. If I choose Vista, it boots straight to vista. If I choose ubuntu, it goes to GRUB and then I van choose Ubuntu or Vista (again). Can I just skip the Longhorn loader part?

---

### Post by diablo75 on 2009-01-25
> **mmitt said:**
> No I'm serious. It goes first to Vista-Longhorn bootloader. If I choose Vista, it boots straight to vista. If I choose ubuntu, it goes to GRUB and then I van choose Ubuntu or Vista (again). Can I just skip the Longhorn loader part?

You might try to edit your C:\boot.ini file.  There is also a timeout setting in there that you can reduce to 0 if you wish.  Just make sure your grub menu has an available option to load Vista.

Also know that Wubi does not install Ubuntu in its own partition, but rather in a folder called Ubuntu on your C:\ which is then "tricked" into believing it is on it's own partition.  Had you installed Ubuntu by loading the live or alternate CDs at boot, instead of using Wubi, you would already be using Grub as the default boot loader.

---

### Post by mmitt on 2009-01-25
> **diablo75 said:**
> You might try to edit your C:\boot.ini file.  There is also a timeout setting in there that you can reduce to 0 if you wish.  Just make sure your grub menu has an available option to load Vista.

Also know that Wubi does not install Ubuntu in its own partition, but rather in a folder called Ubuntu on your C:\ which is then "tricked" into believing it is on it's own partition.  Had you installed Ubuntu by loading the live or alternate CDs at boot, instead of using Wubi, you would already be using Grub as the default boot loader.
Ok I see. But won't Vista-Longhorn just boot what the default is? (It is set to Vista.) I just want GRUB to come before Vista-Longhorn. I was also wondering, can i put my ubuntu files on its own actual partition after the install? I'm quite liking it.

---

### Post by caljohnsmith on 2009-01-25
In order to get a clearer picture of your setup related to booting, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to switch entirely to Grub.

---

### Post by mmitt on 2009-01-25
[#]=> Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst /bootmgr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb25d11f

Partition  Boot        Start          End         Size  Id System

/dev/sda1                 63   23,165,729   23,165,667   7 HPFS/NTFS
/dev/sda2    *    23,165,730  488,392,064  465,226,335   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0A86B67086B65BBF" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="7E70E2D970E29765" LABEL="Partition_1" TYPE="ntfs" 
/dev/loop0: UUID="c63a8e32-b2a7-4a78-9120-8fcf43ec7f61" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/max/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=max)

==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=7E70E2D970E29765 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=7E70E2D970E29765 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=7E70E2D970E29765 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7E70E2D970E29765 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7E70E2D970E29765 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
chainloader    +1


=================== sda2: Location  of files loaded by Grub: ===================


  16.4GB: ubuntu/disks/boot/grub/menu.lst
  16.2GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
  16.5GB: ubuntu/disks/boot/initrd.img-2.6.27-9-generic
 137.0GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
 192.8GB: ubuntu/disks/boot/vmlinuz-2.6.27-9-generic

=============================== StdErr Messages: ===============================

No errors were reported.[/#]

---

### Post by caljohnsmith on 2009-01-25
OK, thanks for posting that, it clarifies your setup. Since you are using a Wubi install of Ubuntu, then you can't use the standard Legacy Grub on start up as your boot loader. If you wanted to give Ubuntu its own partition and do a standard install, you could then use Grub on start up instead of the Windows boot loader. Or if you want to modify your Vista boot loader, you could use "[EasyBCD]("http://neosmart.net/dl.php?id=1")", and I believe that will enable to change the default OS that gets booted if you don't do anything on start up. But unless you do a standard Ubuntu install, you'll have to use Vista's boot loader, unless you want to install "Grub4DOS" inside of Vista and use that as your boot loader. I'm not sure what advantage there would be to using Grub4DOS instead of Vista's boot loader though for your particular setup.

---

### Post by mmitt on 2009-01-25
> **caljohnsmith said:**
> OK, thanks for posting that, it clarifies your setup. Since you are using a Wubi install of Ubuntu, then you can't use the standard Legacy Grub on start up as your boot loader. If you wanted to give Ubuntu its own partition and do a standard install, you could then use Grub on start up instead of the Windows boot loader. Or if you want to modify your Vista boot loader, you could use "[EasyBCD]("http://neosmart.net/dl.php?id=1")", and I believe that will enable to change the default OS that gets booted if you don't do anything on start up. But unless you do a standard Ubuntu install, you'll have to use Vista's boot loader, unless you want to install "Grub4DOS" inside of Vista and use that as your boot loader. I'm not sure what advantage there would be to using Grub4DOS instead of Vista's boot loader though for your particular setup.
Ok. I wanted to do a full install of Ubuntu but Vista wouldn't let me shrink the partition I wanted to use for ubuntu to anything less than 8GB lol. I don't get the swap partition thing anyway, I mean why would I want to split may RAM? I would actually love to do this if I could get more help :P. Thanks for your idea about Grub4DOS. I'm going to use that lol. Ok hope to hear back soon, I'm loving the ubuntu forums so far.

---

### Post by caljohnsmith on 2009-01-25
How about checking out [this post]("http://ubuntuforums.org/showpost.php?p=6523094") of some tricks you can do to shrink your Vista partition, and let me know if that helps at all. If not, you could try using Ubuntu's gparted (System > Admin > Partition Editor on the Live CD) to shrink the Vista partition. By the way, the swap partition is like Windows "page file", meaning that swap is a temporary space that Ubuntu can use when you get low on free RAM. It's always good to have at least a little swap space, even if you have lots of RAM. Also, if you ever want to "hibernate" your computer, you would need to have a swap space as large as your RAM in order to do that. Good luck and let me know how it goes.

---

