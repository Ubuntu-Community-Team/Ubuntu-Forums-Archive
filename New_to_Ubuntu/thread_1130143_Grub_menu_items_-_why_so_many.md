---
title: "Grub menu items - why so many"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by studiodude on 2009-04-19
why so many kernals and can they be removed from grub menu.lst - 

there are 10 items in my grub loader, the first two being the kernal i am using and the recovery version, then there are three more sets and another memtest one before my windows installation.  I have edited the list and can succesfully change to boot windows first (I have to for work, unfortunatly) and i had to change the boot number in the grub menu.lst from 0 to 10......... do i really need all the others? Its no bother having them there - just looks a bit messy and i have to hit the up arrow key 10 times to boot into linux when im not at work. can they just be cut out of the list and the default boot number changed accordingly?


> 
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mprince on 2009-04-19
You really only need the latest kernel you are using and the one before it as a backup.

[http://ubuntuforums.org/showthread.php?t=257271](http://ubuntuforums.org/showthread.php?t=257271)

---

### Post by mprince on 2009-04-19
I'd recommend typing 

```
uname -r
```

into a terminal to see which version you are currently running. Make absolutely sure you don't remove that version.

---

### Post by oldos2er on 2009-04-19
> **studiodude said:**
> why so many kernals and can they be removed from grub menu.lst - 
  

 Use Synaptic Package Manager to remove unneeded kernels, it will automatically update your /boot/grub/menu.lst. I like to keep at least two kernels just in case the newer one becomes broken.

---

### Post by studiodude on 2009-04-19
> **mprince said:**
> I'd recommend typing 

```
uname -r
```

into a terminal to see which version you are currently running. Make absolutely sure you don't remove that version.

I did that and the top entryin my menu.lst refers to my 2.6.27-11-generic version reported in the terminal after uname -r.

i made a copy grub menu.bak and posted it here of how i intent to edit it, would anyone mind double checking before i change it to menu.lst - ?

Here goes:

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default	 4


snip-

> 


title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, memtest86+
uuid		2dd4158b-a928-4303-96f7-563321622c6f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


It looks right to me - am I correct in thinking this will work?  I could try it of course, but this is a forum full of people who know the answer and I am grateful for their experience could save me from messing up.

Thanks all for your help.  I feel comfortable in this comunity - its very conducive to learning.

---

### Post by JoshuaRL on 2009-04-19
Yeah, if -11 is working perfect for you then that should work.  But like was suggested earlier its a good idea to go into Synaptic and remove the other kernels too.  Just search for "kernel-image" and remove the ones earlier than the one you want to keep.

---

### Post by studiodude on 2009-04-19
Ok, theres an awful lot of stuff when i search for "kernal-image" 

2 questions if thats ok:


what exactly should i be looking for....these kind of entries seem to be the best candidates - am i right?

linux-image-2.6.27-7-generic
Linux kernel image for version 2.6.27 on x86/x86_64

(with the check box a different color?- indicates installed, right)?


AND 2

Why are they there in the first place? did I mess up on the installation?

---

### Post by CatKiller on 2009-04-19
> **studiodude said:**
>  i had to change the boot number in the grub menu.lst from 0 to 10

I haven't really fiddled with GRUB much, and I didn't use it when I was dual-booting, but I suspect that if you remove all of those spare kernels, your Windows entry will no longer be the eleventh in the list. I don't know for sure that updating GRUB will necessarily also update this entry.

If it doesn't, you should be able to move the Windows entry to before the automagic list, and set the default to 0. Then you won't have to change it again if you install a newer kernel.

> **studiodude said:**
> Why are they there in the first place?

When you install a newer kernel, because of security updates or dist-upgrades or what-have you, the older kernel is kept in case there's something wrong with the new one, so that you can still boot your machine to fix whatever it is that's wrong. You don't necessarily need to keep **all** the old versions once you've established that the new one works.

---

### Post by oldos2er on 2009-04-19
> **studiodude said:**
> Ok, theres an awful lot of stuff when i search for "kernal-image" 

2 questions if thats ok:


what exactly should i be looking for....these kind of entries seem to be the best candidates - am i right?

linux-image-2.6.27-7-generic
Linux kernel image for version 2.6.27 on x86/x86_64

(with the check box a different color?- indicates installed, right)?


AND 2

Why are they there in the first place? did I mess up on the installation?

 That's right, linux-image-2.6.27-7-generic is a kernel. Right-click on it, choose 'Mark for Removal.'. It may want to remove linux-restricted-modules-2.6.27-7 as well; let it.

 The system never removes old or updated kernels unless you specifically ask it to.

---

### Post by -kg- on 2009-04-19
> 
[QUOTE]Quote:
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 4
snip-

> Quote:


title Ubuntu 8.10, kernel 2.6.27-11-generic
uuid 2dd4158b-a928-4303-96f7-563321622c6f
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid 2dd4158b-a928-4303-96f7-563321622c6f
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=2dd4158b-a928-4303-96f7-563321622c6f ro single
initrd /boot/initrd.img-2.6.27-11-generic


title Ubuntu 8.10, memtest86+
uuid 2dd4158b-a928-4303-96f7-563321622c6f
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

It looks right to me - am I correct in thinking this will work? I could try it of course, but this is a forum full of people who know the answer and I am grateful for their experience could save me from messing up.[/QUOTE]

Actually, not quite.  Remember that, for the Default Setting, the numbering convention starts at 0.  Therefore, if you want to autoboot your Windows installation under the above menu.lst configuration, Default would have to be set to "3"..."0" for the normal boot into Ubuntu, "1" for booting into Ubuntu's Recovery Mode, "2" for Memory Test, and "3" for Windows.

As a previous poster has stated, it might be better for you to put the Windows Chainloader entry before the Linux entries and change the Default value back to "0".  That way, when your kernel is updated in the future, the order in the menu.lst won't change and it won't affect what you autoboot into.  Otherwise, every time you have a kernel update, you will be forced to edit menu.lst again to change the Default value or to delete unecessary kernel entries.

Here's an interesting thing I just found out.  From the menu.lst comments above:

> # Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.

This sounded interesting, so [I did some research on it:]("http://www.gnu.org/software/grub/manual/html_node/savedefault.html")

> 13.3.33 savedefault
— Command: savedefault num

    Save the current menu entry or num if specified as a default entry. Here is an example:

              default saved
              timeout 10
              
              title GNU/Linux
              root (hd0,0)
              kernel /boot/vmlinuz root=/dev/sda1 vga=ext
              initrd /boot/initrd
              savedefault
              
              title FreeBSD
              root (hd0,a)
              kernel /boot/loader
              savedefault
         

    With this configuration, GRUB will choose the entry booted previously as the default entry. 

I assume from the above that you edit the Default setting to "Saved" and place the line "savedefault" as the last line below each option in your boot list.  I may have to try this myself just for experimentation purposes.

---

### Post by egalvan on 2009-04-19
Also, to keep the number of kernels down to want you want,
edit this part of menu.lst

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
[COLOR="Red"]# howmany=2[/COLOR]

I have it set to 2, and it only saves the current version, and the previous version...

Much less clutter...


Note, I just checked,
this does not automatically remove the kernels from your hard drive,
you still need Synaptic for that...

---

### Post by studiodude on 2009-04-20
This is all really helpful, thank you so much everyone who has contributed.  Theres a few helpful tricks here apart from the original question.  I&#7743; off to experiment and hopefully not break anything - will report back when finished.

---

### Post by Paqman on 2009-04-20
The easiest way to keep Grub tidy is to install the package startupmanager. You can use it to specify how many kernels you want to use in Grub. I'd set it to one or two.

Note that this won't actually remove the old kernels, you'll still need to go into Synaptic and do this yourself. So if space is a priority you might want to skip startupmanager and just get in the habit of uninstalling the old ones.

---

### Post by studiodude on 2009-04-20
Hi again,

I managed to successfully edit the grub menu list and it is all looking tickety boo now - the only thing I&#7743; concerned about with actually deleting the older kernals is if they are actually being used for anything?  Would this be the case.  Is it ok to go ahead and dump them or are they taking up such an insignificant amount of space that its not worth worrying about and I just leave em where they are? - I have many gigs of space free on the linux installed partition - like 16gb or something, the thing is running like a dream for me at the moment, everything is working and i am getting used to tweaking and playing around with the terminal etc - seriously considering dumping windows altogether if i can sort out one issue I need for work, but i&#314;l start a new thread on that.  

Thanks again everyone.

one week into linux and LOVING it..............!!!!

---

### Post by Paqman on 2009-04-20
No, kernels are only used if you actually boot them. Otherwise they just take up space (potentially dozens of MB, depending on how many there are)

You don't really need to edit /boot/grub/menu.lst manually. If you just remove the kernels through Synaptic the system tidies the list up for you automatically.

---

### Post by oldos2er on 2009-04-20
"I managed to successfully edit the grub menu list and it is all looking tickety boo now - the only thing I&#7743; concerned about with actually deleting the older kernals is if they are actually being used for anything?"

 Again, it's best to use a package manager for this. If you manually delete them, then sometime down the road do a dist-upgrade, apt-get's going to be confused. Not an impossible situation to solve, but much easier to avoid it altogether.

---

### Post by egalvan on 2009-04-22
> **studiodude said:**
> Hi again,

I managed to successfully edit the grub menu list and it is all looking tickety boo now
 - the only thing I&#7743; concerned about with actually deleting the older kernals is if they are actually being used for anything? 

one week into Linux and LOVING it!!!

Older kernels (n.b. not kernals) are not used unless you actually boot into them... as others have stated.
The main (only?) use of older kernels is to have a fall-back option for when a kernel up-date borks your system.

I have the menu.lst set up to only show two kernels.
This keeps the current (latest) one, and the previous (older) one.
The kernels are still installed, but do not show up on the menu.
I only keep three kernel versions installed...
all older ones are deleted via a package manager (Synaptic is easiest for me).

Only once have I had to boot using a previous kernel... 
I did that to verify an error.

Note... you CAN keep all the kernels if you want...
And you can show as many, or as few, as you want...

The best advice...
if you are paranoid, or unsure, then keep all the kernels on the hard drive.
edit menu.lst to show what you need, either via the "# howmany=2" option,
or by putting hash marks ( # ) in front of the stanzas you don't need.

---

### Post by -kg- on 2009-04-23
All in all, unless you *just want* to play with menu.lst and everything (I completely understand learning experiences, and it's the way I first learned to do it), Startup Manager is the easy way to go.  I have it installed, though I still do my configuration by editing my menu.lst for the most part.

Startup Manager has all the menu.lst options that are easily configurable through it's GUI, including the ability to dress up the GRUB menu using colors and even backgrounds.  A nice little piece of software.

---

