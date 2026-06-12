---
title: "Ubuntu 9.04 won't boot up"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by agst on 2009-07-26
Hi, I'm new here:)
 
I had spent the last 2 weeks trying to get the right setup. I have a Dell Inspiron 6400 laptop and wanted to dual boot Ubuntu 9.04 with Windows 7. After a lot of trouble and many installations (and following some threads in here, thanks!) I finally got Win 7 to boot when I pressed the power button and Ubuntu to boot when I pressed the Media Direct button.
 
However I installed some applications and then I noticed GParted wasn't installed anymore. So I installed it again only to find out it said my whole hard drive was unpartitioned! I can boot to Win 7 fine, I can get to the grub menu and boot Ubuntu but it doesn't finish loading. I get some weird colors at the top of the screen and then it just hangs. I have tried safe mode and it does the same thing.
 
I can see all of my partitions using a live cd and i already backed up most files. I don't know how to fix this, please help! I could just reinstall Ubuntu but it would save me A LOT of time if I could just fix this.
 
I don't know if it stopped working because I installed some of the KDE apps, is that possible?

---

### Post by lindsay7 on 2009-07-26
Type these commands into the terminal using the live Ubuntu cd and post the results here.

sudo fdisk -l    (the small case letter L)


sudo cat /boot/grub/menu.lst

---

### Post by SoftwareExplorer on 2009-07-26
And most of your ubuntu settings for your user only would be at /home/yourusername. If you do have reinstall, you might be able to transfer your settings by restoring that folder. For it to work you have to have backed up hidden files. All files with a name that starts with a period (.) are hidden and that is where most settings are stored.

---

### Post by agst on 2009-07-26
here it is, thanks for the quick replies!

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        5228    41945715    7  HPFS/NTFS
/dev/sda3            5229        6448     9799650   83  Linux
/dev/sda4            6449       19457   104494792+   5  Extended
/dev/sda5            6449        6934     3903763+  82  Linux swap / Solaris
/dev/sda6            6935       19457   100590966   83  Linux

ubuntu@ubuntu:~$ sudo cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

this shouldn't be right eh?  hehe

---

### Post by lindsay7 on 2009-07-26
Try the command again, it should be

sudo cat /boot/grub/menu.lst   (this is the the small case letter L in .lst)

---

### Post by SoftwareExplorer on 2009-07-26
What Operating system are you running the 'cat' command off? Is it the liveCD or off the ubuntu install on the hard disk?

Edit: ubuntu@ubuntu problably means live cd.

---

### Post by SoftwareExplorer on 2009-07-26
The live CD doesn't have the file 'cat /boot/grub/menu.lst' is looking for, and even if it did it wouldn't be the version lindsay7 is looking for. So, when you are in the Live CD go to your Linux partition (looks like sda3 or sda6 in this case, if that helps).  When you get into the partition, go to the boot folder. Then go to the grub folder. Then go to menu.lst and open it. Then copy and paste it here.

---

### Post by agst on 2009-07-26
yes i'm running it from the live cd. how should I run it?

I can see the 10 GB Media partition in the Places menu but when i click on it, nothing happens....

---

### Post by SoftwareExplorer on 2009-07-26
> **agst said:**
> Hi, I'm new here:)


Welcome to Ubuntu and the Ubuntu Forums by the way. :D

---

### Post by SoftwareExplorer on 2009-07-26
> **agst said:**
> 
I can see the 10 GB Media partition in the Places menu but when i click on it, nothing happens....

Do you happen to have gparted open at the moment? Gparted locks partitions so you can't open (mount) or unmount them while gparted is open.

---

### Post by agst on 2009-07-26
Thanks!  :)

yeah GParted was open, closed it and it worked!

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
# kopt=root=UUID=77a28922-dc38-404b-b626-37c8f8c943f6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=77a28922-dc38-404b-b626-37c8f8c943f6

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        77a28922-dc38-404b-b626-37c8f8c943f6
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=77a28922-dc38-404b-b626-37c8f8c943f6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        77a28922-dc38-404b-b626-37c8f8c943f6
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=77a28922-dc38-404b-b626-37c8f8c943f6 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        77a28922-dc38-404b-b626-37c8f8c943f6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=77a28922-dc38-404b-b626-37c8f8c943f6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        77a28922-dc38-404b-b626-37c8f8c943f6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=77a28922-dc38-404b-b626-37c8f8c943f6 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        77a28922-dc38-404b-b626-37c8f8c943f6
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1

---

### Post by SoftwareExplorer on 2009-07-26
> **agst said:**
> Thanks!  :)

yeah GParted was open, closed it and it worked!


Wow, that was a majorly lucky guess on my part. 

Now, hopefully lindsay7 can help you more.

I'm going to go and eat lunch.

---

### Post by agst on 2009-07-26
haha  it happens.  thanks!

lindsay?

---

### Post by SoftwareExplorer on 2009-07-26
> **lindsay7 said:**
> Type these commands into the terminal using the live Ubuntu cd and post the results here.

sudo fdisk -l    (the small case letter L)


sudo cat /boot/grub/menu.lst

lindsay7 was the one who wanted to know what happens when you do 'sudo cat /boot/grub/menu.lst', which is basically what I helped you do, except we did it with the mouse instead of the command line.

---

### Post by agst on 2009-07-26
yeah I know, I was just asking if she was around...hehe.  :)

---

### Post by SoftwareExplorer on 2009-07-26
It says that they are online and viewing there control panel.

Edit: just sent a PM telling him we got past the problem and are ready.

---

### Post by lindsay7 on 2009-07-26
Try this and see if it helps.

Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by lindsay7 on 2009-07-26
When we get this working, we need to reset the timeout for your boot up. It is set for 3 seconds which is a little fast to choose which OS you want to boot to.  There are two ways to do this and once we get you going with the dual boot. You can change it.

---

### Post by agst on 2009-07-26
that didn't work.  I reinstalled the grub and same thing.

I can see the grub menu, it's after I get the ubuntu splash screen that it blinks with a few lines at the top of the screen on different colors about 3 or 4 times and then freezes.  when i hit the power button it does something (reads the HD and between those lines of color I see something like a bar loading) and then turns off.  So I'm thinking maybe it's something to do with the display?  Although I already typed my username and password and that didn't seem to get it to load either...

---

### Post by lindsay7 on 2009-07-26
I think what you have is a video driver problem that must have been caused by something that happened when you installed some packages. This is not a boot up problem, so your best bet would be to start a new thread and ask for some help with the problem. If you can give some info on the video card that you are using that would help. I would guess that you probably need to reinstall a driver or reset the system.  I am not going to be any help with that end of things as I have never worked on video problems.  Good luck and try to give as much info on your system as possible.

---

### Post by agst on 2009-07-26
thanks for your help, I'll try that:)

---

