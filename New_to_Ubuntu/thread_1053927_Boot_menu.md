---
title: "Boot menu"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by irishy on 2009-01-29
Help please I have fiesty fawn and xp on my pc and all of a sudden I have lost xp off the boot menu can anyone tell me how to get it back
thanks 
Irishy

---

### Post by sahabcse on 2009-01-29
Try reload and fix  the grub.

visit [http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by irishy on 2009-01-29
Thank you for your reply I apologize for being very basic and new to ubuntu could you explain what is meant by reload and fix the grub I tried to follow the info in your link but to no avail 
thanks again

---

### Post by glennzo on 2009-01-29
Or open a terminal and post the output of these 2 commands
```
sudo cat /boot/grub/menu.lst
sudo /sbin/fdisk -l
```
With that information your boot loader can easily be repaired.

---

### Post by Elfy on 2009-01-29
That just reinstalls grub

Start feisty - which fyi is well out of support now :)

You can add it back to menu list easily enough - can you run these for me please and post results

```
ls -al /boot/grub/menu*
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by glennzo on 2009-01-29
> **forestpixie said:**
> That just reinstalls grubWhat just reinstalls grub?

> **forestpixie said:**
> 
```
ls -al /boot/grub/menu*
cat /boot/grub/menu.lst
sudo fdisk -l
```Basically what I said to do. :rolleyes:

---

### Post by Elfy on 2009-01-29
I wonder what it is you mean glennzo?

What just reinstalls grub? the link in #2

And yes funny how your and my posts are the same - but when I started typing your's wasn't there :rolleyes: perhaps you thought I knew you were going to post.

---

### Post by glennzo on 2009-01-29
OK, now I understand. I didn't bother to follow the link in post #2.

Yes, I thought you knew what I was going to type. A **luminous zuminous horoscope fish** is indeed psychic, no ? :)

---

### Post by irishy on 2009-01-30
I hope this is right thanks for your help 
tony@tony-desktop:~$ ls -al /boot/grub/menu*
-rw-r--r-- 1 root root 6310 2009-01-26 11:07 /boot/grub/menu.lst
-rw-r--r-- 1 root root 5878 2009-01-26 11:07 /boot/grub/menu.lst~
tony@tony-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

tony@tony-desktop:~$ sudo fdisk -l

> 

---

### Post by glennzo on 2009-01-30
You should see Windows as the 6th entry in the boot menu. I've taken the liberty of removing all the garbage from the menu.lst file so that the content is easier to follow. Here's my version of your file.
```
default 0
timeout 10

title Ubuntu 8.04.2, kernel 2.6.24-23-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-22-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-21-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-19-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f04a0047-c917-437d-a2dc-f3d4be369bdb ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```
Based on this you should see
```
Ubuntu
Ubuntu
Ubuntu
Ubuntu
Ubuntu
Microsoft Windows XP Home Edition
```
when the boot menu loads. Is this what you see?

---

### Post by Elfy on 2009-01-30
A luminous zuminous horoscope fish is indeed psychic, no ? - Only on even days :)

I don't know if you're intention is to get the OP to rewrite his boot menu.lst with your version, but I'd be a bit worried with having no recovery option in menu.lst and removing the information update-grub uses to write to the file when kernels are updated.

---

### Post by glennzo on 2009-01-30
> **forestpixie said:**
> A luminous zuminous horoscope fish is indeed psychic, no ? - Only on even days :)

I don't know if you're intention is to get the OP to rewrite his boot menu.lst with your version, but I'd be a bit worried with having no recovery option in menu.lst and removing the information update-grub uses to write to the file when kernels are updated.No. I  just cleaned all the junk out so it's easier reading. Being a Fedora fanboy (running Ubunru Intrepid as we speak) I don't see the need for all that "crap" in there anyhow. My opinion aside, I believe that you'd have agree that either way he should at least see an option for XP in his boot menu as it was originally written. Odd that he claims that it's not there. Maybe he means that XP won't boot ?

On a side note, and an honest question, is it often that Ubuntu users need a recovery option? What about memtest. Something that is frequently used?

---

### Post by Elfy on 2009-01-30
Oh yea - indeed - the xp should have been in the menu list without a doubt - I guess it was hidden somewhere at the bottom.

I'd be inclined to remove some of the older kernels and let update-grub clear out some of the dross. I do wonder myself that the deal is indeed > Maybe he means that XP won't boot ? certainly it's not booting Feisty 
- it looks to be Hardy.




> On a side note, and an honest question,  is it often that Ubuntu users need a recovery option? What about memtest. Something that is frequently used?I use recovery option with some frequency - but then I'm a bit of a fiddler - I'd certainly keep the most recent :) But then I only let grub keep 2 sets anyway. Only ever used memtest once myslef and then from a livecd.

---

### Post by glennzo on 2009-01-30
I would have cleaned out all but the 2 newest kernels too but I'm not all to familiar with the Ubuntu way of doing things. As for all the notes, I guess they're useful for newbies but I like my menu text clean. I've actually installed Ubuntu after Fedora so Ubuntu's grub is handling the booting duties here. Too lazy to reinstall Fedora's grub. No matter. It works either way.

I've used memtest once or twice. Takes *way* to long for an impatient guy like me though. Quicker to install new memory :p

---

### Post by Elfy on 2009-01-30
If you mean all the stuff commented out - then only the ## comments out, the lines preceded with # are used by grub update after ### BEGIN AUTOMAGIC KERNELS LIST

I played about with fedora once - I got confused by it's grub :) ended up chainloading it on my buntu menu :D

---

### Post by irishy on 2009-01-31
That is how it was  but now the bottom item just says other operating systems and when I click on it it just says error message use any key to continue
thanks again
I do apologise for my supplying the wrong info my op systems are Hardy Heron and xp and I cannot boot xp up because it is no longer on the list. One thing that happened just before my problem started I had allowed ubuntu to check the disc on start up it had been attempting to check the same for several start ups has this any relevance
thanks

---

### Post by Elfy on 2009-01-31
Open synaptic - search for linux-image

It will show you all the different kernels that you have installed - you can remove a lot of them. Assuming that you have no problems with -23 then I would uninstall all of the older ones, leaving just -23 and -22 installed.

Once it's finished then you will be back to having just a few options.

Is there not an arrow or something at the bottom to get to the xp - I'm guessing that you lose the rest of the screen

---

### Post by irishy on 2009-01-31
I thank you for sorting that out for me I am now back to the original boot menu, how was it possible for the boot menu to have become that full
thanks

---

### Post by Elfy on 2009-01-31
Every time that there is a kernel upgrade it gets added to the menu list - you can tell it to not list as many or remove them as and when just like you've now done.

You could if you wanted to change


> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=[COLOR="Red"]all[/COLOR] to a number - 2 or more then you'll only see the newest ones.

---

### Post by irishy on 2009-01-31
Thanks for everything

---

### Post by glennzo on 2009-01-31
> **forestpixie said:**
> If you mean all the stuff commented out - then only the ## comments out, the lines preceded with # are used by grub update after ### BEGIN AUTOMAGIC KERNELS LISTI wasn't aware that there was any difference in the number of hash marks used. So any line with a single hash mark is actually read and acted upon by the system during kernel updates ?
> **forestpixie said:**
> 
I played about with fedora once - I got confused by it's grub :) ended up chainloading it on my buntu menu :DThat's interesting. I find Fedora's grub simple and Ubuntu's grub a bit too much. Guess it's all in perception.

---

### Post by glennzo on 2009-01-31
> **irishy said:**
> That is how it was  but now the bottom item just says other operating systems and when I click on it it just says error message use any key to continue
thanks again
I do apologise for my supplying the wrong info my op systems are Hardy Heron and xp and I cannot boot xp up because it is no longer on the list. One thing that happened just before my problem started I had allowed ubuntu to check the disc on start up it had been attempting to check the same for several start ups has this any relevance
thanksIrishy, write down the error message and post it here. It will probably be very relevant to us being able to help you get this fixed.

---

### Post by Elfy on 2009-01-31
> **glennzo said:**
> I wasn't aware that there was any difference in the number of hash marks used. So any line with a single hash mark is actually read and acted upon by the system during kernel updates ?

Yea for instance

# defoptions=quiet splash - makes sure that quiet and splash are added to new kernel boot stanzas

This bit is quite blunt about the whole thing :) > ## DO NOT UNCOMMENT THEM, Just edit them to your needs

---

### Post by glennzo on 2009-01-31
Oh, I've been looking at **## DO NOT UNCOMMENT THEM, Just edit them to your needs** since the first Ubuntu I installed. Never paid any attention to it :rolleyes: I suppose that there's a page somewhere that will cover everything I need to know about Ubuntu grub. Would be an interesting read. Got any links? Searching this forum, as with other forums, is pretty useless. Never seem to get the results I'm looking for. Most of the results are only vaguely related to the search terms.

This also explains why a ton of comments are added to my menu.lst every time there is a kernel update.

Irishy, don't mean to be hijacking your thread here. I'm doing some learning here too so I guess we have 2 conversations going on at the same time so hang in there and one or both of us will help you get this sorted. I may not have the knowledge to fix grub the Ubuntu way but I've sure done it enough with Fedora and other distros.

---

### Post by Elfy on 2009-01-31
First off I believe that irishy is finished now - certainly I think his boot works ok now > Thanks for everything

Yes I don't know much about other forums, but it's not the easiest to search I use uboontu.com or googlebuntu.com usually.

I go here for most of my grub thinking - [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) and for errors [http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

But there is a handbook - [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

I think though that we'll be needing to forget grub and start thinking about grub2 eventually - tried once and it was a painful experience :)

I shall bear you in mind if I get fedora issues again, as I said I ended up adding it chainloader to my buntu menu

---

### Post by glennzo on 2009-01-31
Thanks for your help and the links Forest Pixie. Much appreciated. Off to stir the pot here in the Ubuntu Forums? ;)

---

