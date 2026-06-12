---
title: "Ubuntu Forums problems - Ubuntu wont boot"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by se_anderson on 2009-09-24
I posted a similar message and was advised by email that 
"
LewRockwell has just replied to a thread you have subscribed to entitled - [ubuntu] Ubuntu won't boot! - in the Absolute Beginner Talk forum of Ubuntu Forums.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=1056064&goto=newpost](http://ubuntuforums.org/showthread.php?t=1056064&goto=newpost)

Here is the message that has just been posted:
***************
Each trouble-call should be issued in a new thread

we need more specific detail regarding what is and is-not happening when you initiate the power-on sequence of the machine in question"

When I click on the link I get taken to the thread but my reply is not there, and my control panel says I am not subscribed to any threads??

So I am reposting the original post with an update.
I was trying to install ie4linux and was being told my version of wine was too old (which is wasnt), I remember being asked to add some new repositories for ie4linux.
I ran synaptic to update my system, I was advised there were other updates (firefox etc) I should install, I installed them I needed to reboot. So I rebooted.
The computer powered down and restarted.  The sequence I see in a boot is;
1/ black screen with blinking cursor
2/ image of motherboard splash graphic & bios options
3/ hardware data listed on screen
4/ grub starts loading
5/ubuntu splash screen
6/ubuntu login
When I restarted the computer it got to step 2 and nothing happened, system did not respond to keyboard etc
I put the ubuntu 9.04 CD in and tried to restart, same thing, got to step 2.
After about 5-10 minutes of doing nothing the computer suddenly started loading the CD

It gave me the options of live CD, boot from hard drive, install etc.  I had to replace my usb keyboard with a ps2 to be able to select the correct boot option.  Then i was able to boot up as normal

So the problem is why the 5-10 minute delay in the boot process.?

Here is my results file again;
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009d611

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   964,622,924   964,622,862  83 Linux
/dev/sda2         964,622,925   976,768,064    12,145,140   5 Extended
/dev/sda5         964,622,988   976,768,064    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f46a8b7d-517b-4ce4-877e-bdd4f24ddce4" TYPE="ext3" 
/dev/sda5: UUID="7f018673-27c3-4d92-b9d9-d5779fd653ed" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stuart/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stuart)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=stuart)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, kernel 2.6.24-21-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 9.04, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 9.04, kernel 2.6.24-18-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 9.04, kernel 2.6.24-17-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-17-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-17-generic

title        Ubuntu 9.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 ro  single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f46a8b7d-517b-4ce4-877e-bdd4f24ddce4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7f018673-27c3-4d92-b9d9-d5779fd653ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//10.1.1.3/stuff  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0

=================== sda1: Location of files loaded by Grub: ===================


 469.9GB: boot/grub/menu.lst
 469.8GB: boot/grub/stage2
 469.9GB: boot/initrd.img-2.6.24-16-generic
 470.0GB: boot/initrd.img-2.6.24-16-generic.bak
 469.9GB: boot/initrd.img-2.6.24-17-generic
 469.9GB: boot/initrd.img-2.6.24-17-generic.bak
 469.9GB: boot/initrd.img-2.6.24-18-generic
 470.0GB: boot/initrd.img-2.6.24-18-generic.bak
 469.9GB: boot/initrd.img-2.6.24-19-generic
 469.9GB: boot/initrd.img-2.6.24-19-generic.bak
 470.0GB: boot/initrd.img-2.6.24-21-generic
 469.9GB: boot/initrd.img-2.6.24-21-generic.bak
 470.0GB: boot/initrd.img-2.6.27-11-generic
 470.0GB: boot/initrd.img-2.6.28-11-generic
 469.9GB: boot/initrd.img-2.6.28-13-generic
 470.0GB: boot/initrd.img-2.6.28-14-generic
 470.0GB: boot/initrd.img-2.6.28-15-generic
 469.9GB: boot/vmlinuz-2.6.24-16-generic
 469.9GB: boot/vmlinuz-2.6.24-17-generic
 470.0GB: boot/vmlinuz-2.6.24-18-generic
 469.9GB: boot/vmlinuz-2.6.24-19-generic
 469.9GB: boot/vmlinuz-2.6.24-21-generic
 470.0GB: boot/vmlinuz-2.6.27-11-generic
 470.0GB: boot/vmlinuz-2.6.28-11-generic
 469.9GB: boot/vmlinuz-2.6.28-13-generic
 470.0GB: boot/vmlinuz-2.6.28-14-generic
 470.0GB: boot/vmlinuz-2.6.28-15-generic
 470.0GB: initrd.img
 470.0GB: initrd.img.old
 470.0GB: vmlinuz
 470.0GB: vmlinuz.old

.

---

### Post by nmccrina on 2009-09-24
> **se_anderson said:**
> 
So I am reposting the original post with an update.
I was trying to install ie4linux and was being told my version of wine was too old (which is wasnt), I remember being asked to add some new repositories for ie4linux.
I ran synaptic to update my system, I was advised there were other updates (firefox etc) I should install, I installed them I needed to reboot. So I rebooted.
The computer powered down and restarted.  The sequence I see in a boot is;
1/ black screen with blinking cursor
2/ image of motherboard splash graphic & bios options
3/ hardware data listed on screen
4/ grub starts loading
5/ubuntu splash screen
6/ubuntu login
When I restarted the computer it got to step 2 and nothing happened, system did not respond to keyboard etc
I put the ubuntu 9.04 CD in and tried to restart, same thing, got to step 2.
After about 5-10 minutes of doing nothing the computer suddenly started loading the CD

It gave me the options of live CD, boot from hard drive, install etc.  I had to replace my usb keyboard with a ps2 to be able to select the correct boot option.  Then i was able to boot up as normal

So the problem is why the 5-10 minute delay in the boot process.?


I've noticed that if certain USB devices are plugged in (specifically a USB hub, but also an external hard drive), there is a long period of just a black screen before the BIOS showed up and the boot continued. I always just assumed that GRUB was trying to boot from the USB device, and after failing for a while it would give up and boot from the regular hard drive. So I usually unplug such devices until after the computer is started up. Maybe try that?

---

### Post by se_anderson on 2009-09-25
I have the printer connected with a usb.  it's never caused this problem before.  I'll give it a go.

ps Forum is working

---

### Post by se_anderson on 2009-09-25
Problem solved.  I tried booting without the printer plugged in and it booted normally.
The I rebooted again with the printer plugged into the USB and it also booted normally.

All seems well, hopefully it will stay that way.

cheers! :popcorn:

---

