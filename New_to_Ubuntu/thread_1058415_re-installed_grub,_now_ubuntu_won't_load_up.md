---
title: "re-installed grub, now ubuntu won't load up"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by fishman78 on 2009-02-02
Hi All,

    so I ooops'ed my grub by re-installing XP.  I restored the grub after much effort.  I get the same old grub screen, so that's good.  And my XP boots from grub no problem.  However my ubuntu dies during startup, just a blank screen.  The light on the monitor is green, so it's getting something.  The last message i get when I boot in recovery mode is:

init:  line 231: cannot open /root/dev/console: no such file
     12.442317]  Kernel panic - not syncing:  Attempted to kill init!

I have no idea what this means.  Any thoughts??

Thanks!

fishman78

---

### Post by caljohnsmith on 2009-02-02
It might be you are just having a problem with the newest kernel, so have you tried booting an older kernel from your Grub menu on start up? If so, what happens?

---

### Post by 73ckn797 on 2009-02-02
> **fishman78 said:**
> Hi All,

    so I ooops'ed my grub by re-installing XP.  I restored the grub after much effort.  I get the same old grub screen, so that's good.  And my XP boots from grub no problem.  However my ubuntu dies during startup, just a blank screen.  The light on the monitor is green, so it's getting something.  The last message i get when I boot in recovery mode is:

init:  line 231: cannot open /root/dev/console: no such file
     12.442317]  Kernel panic - not syncing:  Attempted to kill init!

I have no idea what this means.  Any thoughts??

Thanks!

fishman78

What is menu.lst boot info showing?

In terminal enter:
```
gksudo gedit /boot/grub/menu.lst
```Also:
```
sudo fdisk -l
```Post the info.

---

### Post by fishman78 on 2009-02-02
Hi!  Thanks for the replies:

Currently I have two kernels 1) 2.6.27-9 and 2) 2.6.27-4.  Both do the same thing.

Here is the output from sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd24dbd37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       20007    58307917+   7  HPFS/NTFS
/dev/sda3           20008       60801   327677805    5  Extended
/dev/sda5           20008       59720   318994641   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1       77825   625129281    b  W95 FAT32
ubuntu@ubuntu:~$ 

```

and my menu.lst (sorry it's long)

```
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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=ee6110c1-6c9a-42b2-9b56-057b7451daf8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ee6110c1-6c9a-42b2-9b56-057b7451daf8 ro quiet splash nohz=off
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ee6110c1-6c9a-42b2-9b56-057b7451daf8 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-4-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=ee6110c1-6c9a-42b2-9b56-057b7451daf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=ee6110c1-6c9a-42b2-9b56-057b7451daf8 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

note:  I am booting off a live cd to get this.  the menu.lst is empty when I type in the command, but when I mount my drive and look at the file there I get the above.  Hope this helps.  Thanks again!!!

fishman78

---

### Post by 73ckn797 on 2009-02-02
Don't see anything that is obviously wrong.

caljohnsmith is probably on the right track.

---

### Post by fishman78 on 2009-02-02
> **73ckn797 said:**
> Don't see anything that is obviously wrong.

caljohnsmith is probably on the right track.


It worked fine just before I toasted the Grub.  Now it's pooched with the new grub.  The top kernel version is the one I was using (with no problems) before the mishap.

---

### Post by caljohnsmith on 2009-02-02
Thanks for the vote of confidence, 73ckn797, but I have no idea what fishman78's booting problem is at the moment. Hopefully we can help him sort it out. :) Fishman78, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully shed some light on what your booting problem might be.

---

### Post by fishman78 on 2009-02-02
> **caljohnsmith said:**
> Thanks for the vote of confidence, 73ckn797, but I have no idea what fishman78's booting problem is at the moment. Hopefully we can help him sort it out. :) Fishman78, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully shed some light on what your booting problem might be.


This is what I get....

```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

```

Maybe I misunderstood??

---

### Post by caljohnsmith on 2009-02-02
You have to first download the Boot Info Script to your desktop before you can run that command. Please see the link in my previous post in order to download the script.

---

### Post by fishman78 on 2009-02-02
Oh,  I have to download it first....;)  sorry you got a DFU here:p

Here is the file you requested.  And thanks so much for your help!!!!

Edit:  Don't know if this means anything, but during my grub restore I was using commands with stage1 in it.  At the bottom of the file it indicates stage2...  again, don't know what that means...

---

### Post by caljohnsmith on 2009-02-02
Unfortunately it looks like the problem is you are missing a lot of important system files in Ubuntu, but to what extent, I don't know yet. How about posting the output of:
```
sudo mount /dev/sda5 /mnt && ls -l /mnt /mnt/home/*
nautilus /mnt/home &
```
And while you are posting the output of the first command, the nautilus file browser should come up and show you your /home directory; how about going through your home directory and let me know if all your personal files are still there.

---

### Post by fishman78 on 2009-02-02
> **caljohnsmith said:**
> Unfortunately it looks like the problem is you are missing a lot of important system files in Ubuntu, but to what extent, I don't know yet. How about posting the output of:
```
sudo mount /dev/sda5 /mnt && ls -l /mnt /mnt/home/*
nautilus /mnt/home &
```
And while you are posting the output of the first command, the nautilus file browser should come up and show you your /home directory; how about going through your home directory and let me know if all your personal files are still there.

Here be the output from the command:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && ls -l /mnt /mnt/home/*
/mnt:
total 84
drwxr-xr-x  3 root root  4096 2009-01-29 22:47 boot
lrwxrwxrwx  1 root root    11 2008-12-26 11:32 cdrom -> media/cdrom
drwxr-xr-x  3 root root  4096 2008-12-26 11:37 home
lrwxrwxrwx  1 root root    33 2009-01-28 22:54 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx  1 root root    32 2008-12-26 18:14 initrd.img.old -> boot/initrd.img-2.6.27-9-generic
drwxr-xr-x  7 root root 12288 2009-02-01 04:49 lib
drwxr-xr-x  4 root root  4096 2009-01-29 22:46 lib32
lrwxrwxrwx  1 root root     4 2008-12-26 11:32 lib64 -> /lib
drwx------  2 root root 16384 2008-12-26 11:32 lost+found
drwxr-xr-x  7 root root  4096 2009-02-01 00:51 media
drwxr-xr-x  2 root root  4096 2008-08-08 18:05 mnt
drwxr-xr-x  2 root root  4096 2009-01-29 04:14 opt
drwxr-xr-x  2 root root  4096 2008-08-08 18:05 proc
drwxr-xr-x 13 root root  4096 2009-02-01 04:38 root
drwxr-xr-x  2 root root  4096 2009-01-29 22:46 sbin
drwxr-xr-x  2 root root  4096 2008-10-01 19:56 srv
drwxr-xr-x  2 root root  4096 2008-09-25 12:48 sys
drwxrwxrwt 13 root root  4096 2009-02-01 00:51 tmp
drwxr-xr-x 12 root root  4096 2008-12-26 17:48 usr
drwxr-xr-x 15 root root  4096 2008-10-01 20:23 var
lrwxrwxrwx  1 root root    30 2009-01-28 22:54 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx  1 root root    29 2008-12-26 18:14 vmlinuz.old -> boot/vmlinuz-2.6.27-9-generic

/mnt/home/ubuntu:
total 40
drwxr-xr-x   7 1000 1000  4096 2009-01-31 23:51 Desktop
drwxr-xr-x   7 1000 1000  4096 2009-01-28 23:01 Documents
drwxr-xr-x   6 1000 1000  4096 2009-01-28 02:58 Downloads
drwxr-xr-x   2 1000 1000  4096 2009-01-20 02:04 Linux Tools
drwxr-xr-x 263 1000 1000 12288 2009-01-26 03:11 Music
drwxr-xr-x  11 1000 1000  4096 2009-01-29 12:00 Pictures
drwxr-xr-x   2 1000 1000  4096 2008-12-26 17:43 Public
drwxr-xr-x   4 1000 1000  4096 2009-01-23 11:53 Videos
ubuntu@ubuntu:~$ nautilus /mnt/home &
[1] 10568
ubuntu@ubuntu:~$ 

```

And it looks like all my files are there and working.  Am I looking at a fresh install?

---

### Post by caljohnsmith on 2009-02-02
> **fishman78 said:**
> 
And it looks like all my files are there and working.  Am I looking at a fresh install?
I'm glad to hear all your personal files are there, but yes, I think your best bet is a fresh Ubuntu install. I would go ahead and move your personal files to some other partition or drive, and then reinstall Ubuntu. Good luck and let us know how it goes.

---

### Post by fishman78 on 2009-02-02
> **caljohnsmith said:**
> I'm glad to hear all your personal files are there, but yes, I think your best bet is a fresh Ubuntu install. I would go ahead and move your personal files to some other partition or drive, and then reinstall Ubuntu. Good luck and let us know how it goes.

I will back them up and re-install.  Then I'll phone Mr. Gates and tell him I don't want to be his friend anymore:(

My main concern is my vbox XP image.  I hope I can save and reload that..

Thank you so much for your help.  You are an asset to the community!!  I really appreciate it!!

---

