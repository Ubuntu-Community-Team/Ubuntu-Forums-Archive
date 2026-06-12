---
title: "Restore a normal boot"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by don_diego on 2009-05-16
Something happened to my installation of Jaunty Jackalope and - being a total noobie - I don't know how to correct it:

My laptop will not boot unless I go into grub and select "Ubuntu 9.04, kernel 2.6.7-44-generic (recovery mode)". 

Would anyone please tell me what I must do to restore a normal boot, i.e. without having to go by way of grub? There is no other OS on this laptop, only 9.04.
TIA

---

### Post by x22 on 2009-05-16
welcome to the forum

well, grub boots the so-called "default" kernel after a
time of waiting.  You can control both by editing the
file /boot/grub/menu.lst.  A timeout of 0 gives instant
boot into the default.

---

### Post by don_diego on 2009-05-16
> **x22 said:**
> well, grub boots the so-called "default" kernel after a
time of waiting.  You can control both by editing the
file /boot/grub/menu.lst.  A timeout of 0 gives instant
boot into the default.

Thank you. Just to make sure I understand, if I only leave the one entry in the
menu.lst that actually let's me boot the system that should make it the default.
Correct?

---

### Post by presence1960 on 2009-05-16
> **don_diego said:**
> Thank you. Just to make sure I understand, if I only leave the one entry in the
menu.lst that actually let's me boot the system that should make it the default.
Correct?
Here is the top section of menu.lst x22 is referring you to.
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		15 


To edit the settings run in terminal ```
gksu gedit /boot/grub/menu.lst
```

By entering "0" for the default your first entry in this section of menu.lst will be the default:
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Kubuntu 9.04
rootnoverify    (hd1,1)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1




```

so my Ubuntu 9.04, kernel 2.6.28-12-generic is my default.

I would not remove the recovery mode entry or the memtest entry.

---

### Post by don_diego on 2009-05-16
Thank you, presence1960, I appreciate your advice very much. Before I do any editing of menu.lst and make the only entry that works my default, allow me one more question:

Since the "Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)" in my menu.lst results in a lengthy boot that eventually ends up with another menu (where I select"normal boot") what can I do to make my system boot normally, i.e. without going into recovery mode?

As I stated in my first post, none of the other options currently shown in grub will boot at all and I am afraid setting the one that does work as my default won't really solve my problem.

---

### Post by presence1960 on 2009-05-16
> **don_diego said:**
> Thank you, presence1960, I appreciate your advice very much. Before I do any editing of menu.lst and make the only entry that works my default, allow me one more question:

Since the "Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)" in my menu.lst results in a lengthy boot that eventually ends up with another menu (where I select"normal boot") what can I do to make my system boot normally, i.e. without going into recovery mode?

As I stated in my first post, none of the other options currently shown in grub will boot at all and I am afraid setting the one that does work as my default won't really solve my problem.

I agree about editing. To get a better picture of what your setup looks like why don't you boot up the Live CD & choose try Ubuntu without making any changes to your computer. Open Firefox and come back here. Download this Boot info script to the Desktop : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Or if Ubuntu will boot from recovery mode as you said you can do it from there without Live CD.

Then open a terminal and run this : ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will produce a RESULTS.txt file on your Desktop. Post the contents of this file. When you post it here place CODE tags around the text by highlighting the text and clicking "#" on the toolbar. This will give a better picture of your setup before you proceed.

P.S. sorry for the delay was putting my daughter to bed.

---

### Post by don_diego on 2009-05-17
OK, presence1960, I think I've got it:

```
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

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,351,124    37,351,062  83 Linux
/dev/sda2          37,351,125    39,070,079     1,718,955   5 Extended
/dev/sda5          37,351,188    39,070,079     1,718,892  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="dd75f321-3088-4658-95b4-4c057270fa53" TYPE="ext3" 
/dev/sda5: UUID="57883fd7-443c-4a33-844c-15f1136083dc" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lutz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lutz)


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
timeout        2

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
# kopt=root=UUID=dd75f321-3088-4658-95b4-4c057270fa53 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd75f321-3088-4658-95b4-4c057270fa53

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
```It obviously doesn't mean a thing to me (maybe it never will) but hopefully this is what you need to asses the problem.

P.S. No need to apologize for the delay, daughter must come first. Besides, I am busy reading Keir Thomas's *Pocket Guide*.

---

### Post by presence1960 on 2009-05-17
take a look at the portion of my menu.lst file I posted here. Yours is missing the start up choices such as Ubuntu 9.04 kernel 2.6.28-12 etc. which follow ## ## End Default Options ##

```
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Kubuntu 9.04
rootnoverify    (hd1,1)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

```

I would suggest reinstalling GRUB. Follow this how to:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD
```.

P.S. or did you not copy all the text from the file?

---

### Post by don_diego on 2009-05-17
> **presence1960 said:**
> take a look at the portion of my menu.lst file I posted here. Yours is missing the start up choices such as Ubuntu 9.04 kernel 2.6.28-12 etc. which follow ## ## End Default Options ##

Yes, mine shows the 2.6.28000-11 as the first choice and no -12 at all . The other one is -14 of which the recovery mode at least let's me boot.  

> I would suggest reinstalling GRUB. Follow this how to:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD
```.
P.S. or did you not copy all the text from the file?Yes, it is all there. 

Unfortunately I don't have the Live CD for 9.04 or I would do exactly as you suggest right now. (I had installed from the 8.10 disk and let it upgrade to 9.04. Maybe that's how grub got messed up?) I'll download the LiveCD iso tomorrow and burn a disk. I'll let you know how I make out.

In the meantime, thanks a bunch for your help, it is much appreciated.

---

### Post by presence1960 on 2009-05-17
> **don_diego said:**
> Yes, mine shows the 2.6.28000-11 as the first choice and no -12 at all . The other one is -14 of which the recovery mode at least let's me boot.  

Yes, it is all there. 

Unfortunately I don't have the Live CD for 9.04 or I would do exactly as you suggest right now. (I had installed from the 8.10 disk and let it upgrade to 9.04. Maybe that's how grub got messed up?) I'll download the LiveCD iso tomorrow and burn a disk. I'll let you know how I make out.

In the meantime, thanks a bunch for your help, it is much appreciated.

Something definitely went haywire during the upgrade process. Hopefully restoring GRUB will solve it. If not I would recommend doing a clean install.

---

### Post by don_diego on 2009-05-17
> **presence1960 said:**
> Something definitely went haywire during the upgrade process. Hopefully restoring GRUB will solve it. If not I would recommend doing a clean install.

You said it, something certainly went VERY wrong. 

I didn't read your reply until just now, but had decided to do just as you suggest - a new, clean install. Worked like a charm and the system boots just like it should. This was an easy choice to make since I had not done anything yet like customizing or adding any programs. 

BTW, my grub still shows the 2.6.28-11 generic kernel, not the -12 that yours does. But as long as it works I guess there is nothing to worry about. 

Once again I want to thank you for taking the time to help me. I am sure I'll be back here with  question as I learn more about Ubuntu and either don't understand something or run into another problem.

Sincerely,
Lutz W.

---

### Post by presence1960 on 2009-05-17
> **don_diego said:**
> You said it, something certainly went VERY wrong. 

I didn't read your reply until just now, but had decided to do just as you suggest - a new, clean install. Worked like a charm and the system boots just like it should. This was an easy choice to make since I had not done anything yet like customizing or adding any programs. 

BTW, my grub still shows the 2.6.28-11 generic kernel, not the -12 that yours does. But as long as it works I guess there is nothing to worry about. 

Once again I want to thank you for taking the time to help me. I am sure I'll be back here with  question as I learn more about Ubuntu and either don't understand something or run into another problem.

Sincerely,
Lutz W.

You will get the 2.6.28-12 kernel on an update. Glad it is working right now.

---

