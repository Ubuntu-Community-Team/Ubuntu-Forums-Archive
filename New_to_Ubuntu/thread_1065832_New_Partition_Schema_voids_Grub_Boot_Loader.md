---
title: "New Partition Schema voids Grub Boot Loader"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by zipher on 2009-02-10
****Using a Laptop with Dual Boot Windows XP / Ubuntu Hardy.

I've been experimenting with partitions using [B]parted[B]
[/B][/B]

Unfortunately I seem to have damaged my bootloader rig. Please help/.

Using parted, I invoked 
**rm**[ptn number] 
in order to deal with a duplicate installation of Hardy, erasing one partition known to contain the distro and a randomly selected swap/Solaris ptitn.

Upon trying to reboot, after BIOS I got a simple message:

**Error 18**

Next loaded live session, despite severe networking interupted connection, managed to 'get in' (NB Is there a firewall against Linux on standard broadband packages? but that's another Q)
Having checked out peeps with sim probs, next tried

**grub**
from Terminal,
and used **find../stage1/**
          **root**
          **setup**

Interestingly, this had an effect and from the extra info output I feel that I may have to edit my fstab file ot similar. Please advise.

The effect is, that upon boot there is a revised error message. It reads

**Error 18 - cylinder size exceeds maximum allowable limit**

Neithre Ubuntu nor XP will boot, I get a strange message from Windows too.

Please assist in restoring functionality, thanks in advance.

**PS** Due to severe network issues it will be a protracted fix. Please forgive any delay in response time. Thanks fyr undsnding

---

### Post by caljohnsmith on 2009-02-10
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop (can be the Live CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by zipher on 2009-02-10
Righto, the Boot Info Script's

 **Results** file is pasted below:


```
> [QUOTE]
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d0f77

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *      6,811,560    68,549,354    61,737,795   7 HPFS/NTFS
/dev/sda3          68,549,355   312,576,704   244,027,350   5 Extended
/dev/sda5          68,549,481   303,516,044   234,966,564  83 Linux
/dev/sda6         303,516,108   308,046,374     4,530,267  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="361E715D67871665" TYPE="ntfs" 
/dev/sda5: UUID="f5850bb0-00a8-4044-a886-33e8264943c7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="8cda0d28-ff6e-4a79-b471-4eb95c3d198d" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f5850bb0-00a8-4044-a886-33e8264943c7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f5850bb0-00a8-4044-a886-33e8264943c7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f5850bb0-00a8-4044-a886-33e8264943c7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0108b5c6-3b82-46de-8889-e3bb65e35130 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0108b5c6-3b82-46de-8889-e3bb65e35130 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f5850bb0-00a8-4044-a886-33e8264943c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8cda0d28-ff6e-4a79-b471-4eb95c3d198d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  85.2GB: boot/grub/menu.lst
  85.2GB: boot/grub/stage2
  85.1GB: boot/initrd.img-2.6.24-19-generic
  85.2GB: boot/vmlinuz-2.6.24-19-generic
  85.1GB: initrd.img
  85.2GB: vmlinuz
[/QUOTE]
```


Well, that's the Script from your recommended program.
Interestingly, I currently have Internet Connectivity.

BTW, I've been trying to set up a separate boot partition, that's why all this muddle.

If you can help, thank you.

---

### Post by caljohnsmith on 2009-02-10
So do you get the Grub error 18 before seeing your Grub menu, or after you get the Grub menu and select Ubuntu to boot?

---

### Post by zipher on 2009-02-10
Hello CalJohnSmith:KS and thanks for taking the trouble to look at this prob.

In answer to you question,

**Yes**, the 'enhanced' 

**Error 18 cylinder size exceeds maximum limit**

message *now* occurs after a distro has been selected. So I guess the grub program is working according to setup, but something's still wrong.

Any ideas??

Jon 'zipher' Lamb

---

### Post by caljohnsmith on 2009-02-10
OK, from the Live CD how about doing:
```
sudo mount /dev/sda5 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
Then change all your Ubuntu entries to use (hd0,4) instead of (hd0,5) similar to:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f5850bb0-00a8-4044-a886-33e8264943c7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```
And also change the "#groot..." line to use the same:
```
# groot=[COLOR="Blue"](hd0,4)[/COLOR]
```
Also, do you plan on making a partition out of all that free space in front of the Windows sda2 partition? If you are, I would recommend doing that now, because your Windows boot.ini file is configured to boot only if you have another partition before the Windows partition. Anyway, let me know if you can at least boot Ubuntu, and let me know if you are going to create a partition with the free space in front of the Windows partition. We can work from there.

---

### Post by egalvan on 2009-02-10
> **caljohnsmith said:**
> . We can work from there.

As always, you're the MAN...

And I see that boot-info now runs on PUPPY!!!

How neat is that?!

Thank you!

ErnestG


P.S.
yes, I really like Puppy  :lolflag:

---

### Post by zipher on 2009-02-10
**YES** It works now, I'm in.:popcorn:

***_Muchos Gracias CJS_***
\

Now, I'd like to refine this partition business somewhat, but dunno if I should...

So far as the unallocated space in front of Windows is conserned Of course I'd like to include it in the partition schema.

Since I have a few questions I'd like to ask, may I do so here and now? 
{OK}

1. When selecting my distro I still get the screen with three (3) choices on it, despite having zapped one of the Linux partition pairs already. I'm wondering if I can simply edit this ***OUT*** of the menu.lst file by deleting various lines following end of section marked:

### END SECTION DEBIAN KERNELS AUTOMAGIC...

But obviously not editing out the windows mention.

?

2.Do you know a link for **How to set up a separate boot partition**, please?

3. That unallocated space you mention, could I just leave it for the time being but reconfigure my Win.ini file?  In the long term, I'd like to move the partitions around a bit and give most of the space over to Linux.

Main thing is, thanks for your help and encouragement. It sure feels good to be out of the swamp once more!!!:P
Jon 'zipher' Lamb

---

### Post by caljohnsmith on 2009-02-11
> **zipher said:**
> 
1. When selecting my distro I still get the screen with three (3) choices on it, despite having zapped one of the Linux partition pairs already. I'm wondering if I can simply edit this ***OUT*** of the menu.lst file by deleting various lines following end of section marked:

### END SECTION DEBIAN KERNELS AUTOMAGIC...

But obviously not editing out the windows mention.

Yes, you can remove those boot stanzas since you no longer need them. 
> **zipher said:**
> 
2.Do you know a link for **How to set up a separate boot partition**, please?

Why do you want a separate boot partition? Really the only reason to have a separate boot partition is if you have the type of Grub 18 error that is because your boot files are out-of-range of your BIOS, i.e. if you had an older BIOS that can't access anything on the HDD past either 8.4 GB or 137 GB. But all your Ubuntu boot files are currently located at ~85 GB, and your BIOS can access them just fine since you can boot into Ubuntu now. Therefore I don't see any advantage in your situation in having a boot partition. 
> **zipher said:**
> 
3. That unallocated space you mention, could I just leave it for the time being but reconfigure my Win.ini file?  In the long term, I'd like to move the partitions around a bit and give most of the space over to Linux.

Yes, if you want you can edit your boot.ini file so that you can boot into Windows now; I just figured if you were going to do something with that space, it would be better to do it now so you don't have to modify your boot.ini multiple times. And just a word of caution in case you were thinking of resizing your Windows partition to use that unused space: if you move the starting sector of a Windows XP partition, unfortunately that will break XP and make it unbootable. I know others who with enough hacking and hair-pulling were able to get XP booting after doing something like that, but I don't think it is worth the trouble unless your Windows *really* needs more space. 

Anyway, to try and get Windows booting again you could do:
```
sudo umount /mnt
sudo mount /dev/sda2 /mnt && gksudo gedit /mnt/boot.ini
```
And change both instances of "partition(2)" to "partition(1)":
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(1)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(1)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```
Good luck and let me know how it goes.

> **egalvan said:**
> 
And I see that boot-info now runs on PUPPY!!!

How neat is that?!

Thank you!

ErnestG


P.S.
yes, I really like Puppy  :lolflag:
Meierfra gets 100% credit for doing that, and it turns out it wasn't trivial to do since Puppy does not have some of the basic commands available that other Live CDs do. But that also means the script should be more robust and compatible with a wider range of distros I think, so if you find any other major distros that have problems running the script, please let us know. And by the way, don't let the fact that Meierfra added my name to the script fool you--99% of the script is his creation, I only contributed a few trivial lines of code to help format the output to make it more readable. :)

---

