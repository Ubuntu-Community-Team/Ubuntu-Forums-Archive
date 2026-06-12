---
title: "Ubuntu 8.10: frequent lock-ups and shutdowns"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by RickB68 on 2009-01-25
First off, let me tell you what got me into this ;-).  I had no plans to run Linux when I purchased my new hardware to build a PC.  So, that could be why I'm having lock-ups and shutdowns.  But anyways, I'm running Ubuntu 8.10 on new hardware.

Here's the skinny on my hardware:
MoBo: Gigabyte EP45-UD3R
Processor: Intel 3.0Ghz Core 2 Duo
RAM: G Skill 4 x 2GB DDR2 1066
Video: ATI Radeon HD4850

What can I do to narrow down the possibilities of what is causing this?  

Thanks for any help on this, I know I'll love Linux if I can make my machine more stable!

Regards,
Rick

---

### Post by zephyrcat on 2009-01-25
The first thing I would try is a memtest. Boot up your system and go to the grub menu (the list of operating systems you can boot - you may need to press a key to get to it) then choose memtest86. This will take some time, but it scans for bad memory. If you get errors, you will probably need to return the RAM.

---

### Post by RickB68 on 2009-01-25
OK, thanks!  I will try that!

---

### Post by RickB68 on 2009-01-25
OK, I thought I could find the memtest....I've seen it before on this machine just yesterday.  I can't remember nor can I find how to get into it (???)

---

### Post by paydaydaddy on 2009-01-25
Memtest is on the live cd. Boot to the live cd and you can select memtest from the options menu. Let it run for several hours. If errors are detected check individual ram modules.

---

### Post by linux6994 on 2009-01-25
Upon boot up you will see grub loading and it will give you a few seconds in which to ESC. At the bottom of the list you will see MEMTEST. Are the lock ups after performing a particular task? Email, Browser, streaming video?

---

### Post by sumit.kalra999 on 2009-01-25
perform the following tasks:

1. Turn On or Restart the system
2. Use the arrow keys to move to the entry labeled Ubuntu, memtest86+
3. Press Enter. The test will run automatically, and continue until you                       
   end it by pressing the Escape key
4. Allow the test to run for at least one full pass

---

### Post by RickB68 on 2009-01-25
> **linux6994 said:**
> Upon boot up you will see grub loading and it will give you a few seconds in which to ESC. At the bottom of the list you will see MEMTEST. Are the lock ups after performing a particular task? Email, Browser, streaming video?

Most common in firefox.  I had to reboot 3 times before I got my first post in LOL!  But that said, I haven't been able to keep it stable enough to try much else other than the updates.

I will try to hit escape, but the window of oppurtunity there is very small ;)

> **sumit.kalra999 said:**
> perform the following tasks:

1. Turn On or Restart the system
2. Use the arrow keys to move to the entry labeled Ubuntu, memtest86+
3. Press Enter. The test will run automatically, and continue until you                       
   end it by pressing the Escape key
4. Allow the test to run for at least one full pass

sumit, this is not a dual boot pc, it goes into loading ubuntu so fast, there's nothing to "arrow" around in.  I barely have time to see anything.

---

### Post by RickB68 on 2009-01-25
The test showed errors and before it was finish, displayed a weird cross-hatched looking pattern on the display and then stopped responding.

Should I try 1 stick at a time and retest?  Or could this be a compatibility issue with the motherboard?

Thanks!
Rick

---

### Post by wesley_of_course on 2009-01-25
Hello RickB68 !    It sounds like your "Timeout " in  /boot/grub/menu.lst
 is set to zero , don't know what the default is but it can be easily changed by issuing the following command in a terminal ; 

```
 gksudo gedit /boot/grub/menu.lst
```   ,  in my case on line 
19  - timeout  I have set it to 15 which gives me 15 seconds to "choose"
my distro .  Remember to save after changing this and if timeout is changed you'll be able to react . Up and down arrows when used will "stop" the clock and then choose and hit enter . 

for reference ; 
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
default         0

[COLOR=Red]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15[/COLOR]

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

splashimage=(hd0,0)/boot/grub/splash.xpm.gz

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, kernel 2.6.24-22-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.2, kernel 2.6.24-20-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-20-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro quiet splash
initrd        /boot/initrd.img-2.6.24-20-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-20-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-20-generic root=UUID=1e64c7d9-456b-46f4-9a72-30649436b51f ro single
initrd        /boot/initrd.img-2.6.24-20-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title        Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb3)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b0c76e0c-1c9c-4300-bfd1-dcf3021c2af9 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb3)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b0c76e0c-1c9c-4300-bfd1-dcf3021c2af9 ro single 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title        Ubuntu 7.10, memtest86+ (on /dev/sdb3)
root        (hd1,2)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title        Linux Mint, kernel 2.6.22-14-generic (on /dev/sdb4)
root        (hd1,3)
kernel        /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb4 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title        Linux Mint, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb4)
root        (hd1,3)
kernel        /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb4 ro single 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title        Linux Mint, kernel memtest86+ (on /dev/sdb4)
root        (hd1,3)
kernel        /boot/memtest86+.bin  
savedefault
boot

 

```   Ya I know , I know   I'll clean it up  ,,,,, someday !Sorry about the long post and hope it helps !

---

### Post by RickB68 on 2009-01-25
Thanks Wesley.  

Just an FYI, I pulled 3 of the 4 sticks and It's been up now since I booted it back up.  Still too early to tell, but the "feel" and responsiveness of everything is now better.  I'll post an update to my experiments and further testing.

thanks everyone!

---

### Post by zephyrcat on 2009-01-25
I am guessing you custom built this system?

First, make absolutely sure that your motherboard supports the RAM you put in. Every motherboard has a maximum total memory supported, so make sure that is high enough.

Next, put in each stick one by one and test with memtest. (Yes, it is a pain.) You will probably find that one or two of them are messed up.

If you build the computer yourself (or at least bought the RAM yourself), you will need to ask for a replacement. Most places, including Newegg, require you to return all of the memory if it came in a "kit." (e.g. if you bought two sticks of RAM that came together, you have to return both together.)

Bad RAM really stinks.

---

### Post by RickB68 on 2009-01-27
Yeah, what I purchased is supposed to be supported.  It's capable of 16GB of 1066 or 1366+.  This memory is 4 x 2GB sticks @ 1066.

Yeah, I'll do that single stick test.  It did come from NewEgg and they were sold in pairs.  Thanks!

---

