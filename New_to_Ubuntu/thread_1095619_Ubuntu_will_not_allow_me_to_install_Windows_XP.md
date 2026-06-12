---
title: "Ubuntu will not allow me to install Windows XP"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Edward B. on 2009-03-13
Whenever I put in the Windows XP install CD I get this message:

Could not display "/media/cdrom0/autorun.inf".
There is no application installed for this file type

If I go into the CD and try to run the .exe file, I get this message:

An error occurred while loading the archive.

Command Line Input

[/media/cdrom0/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/setup.exe or
          /media/cdrom0/setup.exe.zip, and cannot find /media/cdrom0/setup.exe.ZIP, period.



I tried booting from the CD on a restart, but I was not able to do so as it required me to press a key on my keyboard and my keyboard will not allow me to make any inputs until the system is started.

I am putting a gun to my head, here, any help would be really appreciated.

---

### Post by Therion on 2009-03-13
Well of course not... You have Ubuntu now, there's no need for XP.  Ubuntu knows this and...  

Okay, I'm kidding.  

What do you want to do, dual boot Ubuntu with XP or just wipe Ubuntu and just go back to Windows XP as your sole OS?

---

### Post by Sealbhach on 2009-03-13
> **Edward B. said:**
> 

I tried booting from the CD on a restart, but I was not able to do so as it required me to press a key on my keyboard and my keyboard will not allow me to make any inputs until the system is started.


There's no point trying to use that XP CD while you're running Ubuntu, you're meant to boot up from it.

What is the error message you get when you press a key?


.

---

### Post by 73ckn797 on 2009-03-13
You are trying to do this bass ackwards. You must, as a previous post says, boot from the XP CD. Be careful though, Windows does not play well with another system on the same hard drive unless you have a second drive to install to. You will then have to configure grub to be able to dual boot.

Bets thing if you want to dual boot is to have had XP already installed. Ubuntu does not run "exe" files.

---

### Post by Edward B. on 2009-03-13
> **Sealbhach said:**
> There's no point trying to use that XP CD while you're running Ubuntu, you're meant to boot up from it.

What is the error message you get when you press a key?


.

My keyboard just will not function until it the OS is loaded. I get no error message... I simply can't use my keyboard, thus I can't choose to boot from the CD.

Hmmm...

I would like to keep Ubuntu and have XP to run games, but if I have to I guess I would go back to XP.

Is there a way to wipe Ubuntu from from the computer, so when I turn the computer on it will have to boot XP from the CD?

---

### Post by Edward B. on 2009-03-13
> **Therion said:**
> Well of course not... You have Ubuntu now, there's no need for XP.  Ubuntu knows this and...  

Okay, I'm kidding.  

What do you want to do, dual boot Ubuntu with XP or just wipe Ubuntu and just go back to Windows XP as your sole OS?

:P

Dual boot ideally, but I will go back to XP if that is the only alternative.

On another note, I have been having this problem with Ubuntu and my graphics card, GeForce FX 5700.

If I choose to have that card installed and running in Ubuntu then it screws up my windows visually. The top of them is kinda cut in off like I showed in [this thread]("http://ubuntuforums.org/showthread.php?t=1086941").

However, if I do not have the graphics card operating in Ubuntu, then every time I start the computer up it boots into this screen displaying nothing but pretty colors. I then have to turn the computer off and turn it back on, at which point it boots into Ubuntu fine. If I enable the graphics card again, I do not have this problem, but the graphic glitches with the windows pops back up again.

Any ideas as to a solution for that?

Thanks, again, for the taking the time to try and help me out here.

---

### Post by redseventyseven on 2009-03-13
Since your graphics card is a separate issue, you may be more likely to get help with it if you start a new topic with a relevant title.

There's a program called "envy" which you'll find in the repositories which automates the process of setting up Nvidia graphics cards.

Alternatively try opening a terminal and typing the command:

```
gksudo nvidia-settings
```
(there may be a way of accessing NVidia Settings through the menu system but I don't know what it is)

Have a little play with these settings and see if that helps.

---

### Post by Sealbhach on 2009-03-14
> **Edward B. said:**
> My keyboard just will not function until it the OS is loaded. I get no error message... I simply can't use my keyboard, thus I can't choose to boot from the CD.


Before you boot up, can you go into the BIOS settings (usually by pressing F2 when the BIOS screen appears) and change the boot order so that it boots from the CD drive before booting from the hard drive?


.

---

### Post by KayakJim on 2009-03-14
You could also install VirtualBox and then run your Windows instance while still in your Ubuntu desktop.

---

### Post by Georgia boy on 2009-03-14
[http://ubuntuforums.org/showthread.php?t=617173&highlight=Play+on+Linux](http://ubuntuforums.org/showthread.php?t=617173&highlight=Play+on+Linux)

I don't know if this will help or not. I was reading some stuff about Wine and came across this article. I personally don't know much about either except for what I read in the forums and also hear others talk about. Maybe someone can further explain this link to you with better understanding. Just thought I would give this a shot to you.

Tom

---

### Post by VraiChevalier on 2009-03-14
> **Edward B. said:**
> 
I tried booting from the CD on a restart, but I was not able to do so as it required me to press a key on my keyboard and my keyboard will not allow me to make any inputs until the system is started.


Sounds to me like the problem is with the type of keyboard and your BIOS. The keyboard is not getting recognized by the BIOS during boot. Is it a USB type of keyboard? If it is try getting a keyboard with the PS2 connector or a USB to PS2 adapter. I've seen this problem before.

As far as installing or reinstalling XP is concerned I would suggest you dual boot Windows XP and Ubuntu. The easiest way to do this would be to install Windows XP first and then install Ubuntu. Be sure to back up any important data first!

---

### Post by Edward B. on 2009-03-14
> **VraiChevalier said:**
> Sounds to me like the problem is with the type of keyboard and your BIOS. The keyboard is not getting recognized by the BIOS during boot. Is it a USB type of keyboard? If it is try getting a keyboard with the PS2 connector or a USB to PS2 adapter. I've seen this problem before.

As far as installing or reinstalling XP is concerned I would suggest you dual boot Windows XP and Ubuntu. The easiest way to do this would be to install Windows XP first and then install Ubuntu. Be sure to back up any important data first!

If I need to end up wiping Ubuntu from the system in order install Windows first, then reinstall Ubuntu, how would I do this? How do I clear Ubuntu from my computer?

Thanks again for the help.

---

### Post by Eisenwinter on 2009-03-14
> **Edward B. said:**
> If I need to end up wiping Ubuntu from the system in order install Windows first, then reinstall Ubuntu, how would I do this? How do I clear Ubuntu from my computer?

Thanks again for the help.
You just install Windows over it. Trust me, Windows will love the fact it gets to be installed as the sole system.

---

### Post by Edward B. on 2009-03-14
> **Eisenwinter said:**
> You just install Windows over it. Trust me, Windows will love the fact it gets to be installed as the sole system.

So if I get BIOS to work by some miracle and set it up for the computer to boot from the CD, then Windows will automatically install over the whole computer wiping out Ubuntu.

In other words - if I manage to boot from the CD and install Windows, can I keep Ubuntu in place or no?

---

### Post by sailthesea on 2009-03-14
Once you've backed up and made a LiveCD for Ubuntu (if you don't already have one) as said just boot the XP disc That will overwrite the whole drive getting rid of Ubuntu 
 You need to find out how to get the keyboard problem sorted first though
 Once that's done run XP for a while and check the HDD out you may need to edit the partitions before you go for a dual boot, definitely scan for errors and defrag, there will be quite a bit of "scorched earth" in there
 After that its just a case of putting that LiveCD in and powering up, the rest you should be able to follow

---

### Post by theozzlives on 2009-03-14
Since the Windows CD (not Ubuntu) won't let you boot from CD [VirtualBox]("http://www.virtualbox.org/") appears too be your only avenue. Windows runs fine in a VM.

---

### Post by -kg- on 2009-03-14
Of course (once you get the keyboard issue resolved) you don't actually have to delete Ubuntu from the hard drive in order to install Windows of any kind.  The following page describes dual booting Vista with Ubuntu (Linux installed first), but should be applicable with any version of Windows:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

---

### Post by betrunkenaffe on 2009-03-14
As was mentioned, this is a problem with your BIOS not supporting your keyboard and so it isn't recognized until your OS loads the necessary drivers to run it. This used to occur on my fiancée's computer before we replaced it. I keep a spare PS2 keyboard and mouse around for exactly this reason, just in case there are ever any problems with a computer that is too old bios wise to have the USB recognition.

Do you have any friends that have PS2 keyboard? If so, have them come over with it or borrow it, it'll only take a few hours and then you can return it. If not, spend 20$ and get a new one (or spend more and get a new mobo). The only other option would be to see if your motherboard has an update bios which might support it.

I'm assuming you installed Linux from boot CD :P

---

### Post by presence1960 on 2009-03-14
> **-kg- said:**
> Of course (once you get the keyboard issue resolved) you don't actually have to delete Ubuntu from the hard drive in order to install Windows of any kind.  The following page describes dual booting Vista with Ubuntu (Linux installed first), but should be applicable with any version of Windows:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

+1 The real issue here is the keyboard. Your keyboard SHOULD function immediately- that is how you get into BIOS. Don't format or install over anything yet. I ran XP in Virtual Box until my DSL went haywire. The techs either didn't know how or didn't want to work with a linux box. So I had to install XP onto a partition so Windows could run natively in it's own partition. The problem is not which order the OS's are installed in, it is your keyboard.

---

### Post by Edward B. on 2009-03-15
Problem.

When I insert the Ubuntu Live CD, Ubuntu will not run it. I get this message:

Error autorunning software
Cannot find the autorun program

Then if I try to enter the CD and run the umenu.exe file, I get this message:

An error occurred while loading the archive.
(null)
Command line output

[/media/cdrom0/umenu.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/umenu.exe or
          /media/cdrom0/umenu.exe.zip, and cannot find /media/cdrom0/umenu.exe.ZIP, period.


Is my computer just screwed up or what?

---

### Post by presence1960 on 2009-03-15
> **Edward B. said:**
> Problem.

When I insert the Ubuntu Live CD, Ubuntu will not run it. I get this message:

Error autorunning software
Cannot find the autorun program

Then if I try to enter the CD and run the umenu.exe file, I get this message:

An error occurred while loading the archive.
(null)
Command line output

[/media/cdrom0/umenu.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/umenu.exe or
          /media/cdrom0/umenu.exe.zip, and cannot find /media/cdrom0/umenu.exe.ZIP, period.


Is my computer just screwed up or what?

You can't run the Live CD from Ubuntu or Windows. You have to insert the CD and reboot (restart). Make sure your CD is set as first boot device in your BIOS if it does not boot.

Do you know what key you need to press to enter BIOS? Every BIOS may be a little different. My key is DEL to enter BIOS. A message displays what key to press when I start the computer. Check yours or refer to your motherboard manual to see which key to press to enter BIOS. You must be willing to do some legwork since we are not physically in front of your machine.

If that does not work get a PS2 keyboard!!

---

### Post by PukingPenguin on 2009-03-15
> **Edward B. said:**
> My keyboard just will not function until it the OS is loaded. I get no error message... I simply can't use my keyboard, thus I can't choose to boot from the CD.



This isn't about Ubuntu. It's probably about your usb keyboard. Lose it, and buy a $9.99 P/S2 keyboard at Wal-mart, and I bet you can make it work....

---

### Post by Edward B. on 2009-03-15
Okay - I've successfully partitioned my hard drive.

My keyboard seems to be working when I reboot it - that is, I can access the BIOS screen and I have the settings clicked to boot from CD.

However, when the text comes up asking me to press any key to boot from CD, I do so and the system boots straight into Ubuntu.

I'm pretty sure I installed Ubuntu by booting from the CD, but now it doesn't seem to be working.

I suppose this could be the keyboard, but I know I installed Ubuntu on this computer from the CD.

---

### Post by Edward B. on 2009-03-15
> **presence1960 said:**
> You can't run the Live CD from Ubuntu or Windows. You have to insert the CD and reboot (restart). Make sure your CD is set as first boot device in your BIOS if it does not boot.

Do you know what key you need to press to enter BIOS? Every BIOS may be a little different. My key is DEL to enter BIOS. A message displays what key to press when I start the computer. Check yours or refer to your motherboard manual to see which key to press to enter BIOS. You must be willing to do some legwork since we are not physically in front of your machine.

If that does not work get a PS2 keyboard!!

Yes, I hit DEL to enter BIOS and it is set up to boot from the CD. This leads me to believe that the keyboard is being detected, but when it starts to boot from the Windows CD for some reason, it goes straight into Ubuntu!

However, if I boot from CD using the Ubuntu CD, then the computer boots correctly (that is, from the Ubuntu CD, not from Ubuntu on my hard drive).

Any ideas on why this is?

---

### Post by Declanthedork on 2009-03-15
It's a bootable CD lol. You have to turn the computer off first.

---

### Post by circa82 on 2009-03-15
> **Edward B. said:**
> Yes, I hit DEL to enter BIOS and it is set up to boot from the CD. This leads me to believe that the keyboard is being detected, but when it starts to boot from the Windows CD for some reason, it goes straight into Ubuntu!

However, if I boot from CD using the Ubuntu CD, then the computer boots correctly (that is, from the Ubuntu CD, not from Ubuntu on my hard drive).

Any ideas on why this is?

I don't know, Edward. <snip>. Maybe your system BIOS also knows the difference?

---

### Post by anewguy on 2009-03-15
It has been my experience in the past that Windows XP will NOT install over the top of any unknown active primary partition type.  I have always had to boot from the LiveCD, run some version of parted (whatever was on that particular release) to remove the Linux partitions.  XP for me at least would only install into non-allocated space.  I suspect this is also why your Windows installation CD starts up and goes straight to Ubuntu.

Try running parted from the LiveCD to remove all the Ubuntu partitions from your drive.  Basically you want a blank drive, free of other partitions (except perhaps a recovery partition if your PC came with one). 

Then, try your Windows CD again.  Once you have Windows installed, you will need to check the disk for errors and defrag it (preferably more than once - it usually takes more than 1 time to really shrink things down).

Now follow one of the myriad of posts and how-to's for dual booting and reinstall Ubuntu.

This is the only way I have ever been able to make this work - Windows seems to want free space to load into, not over the top of other partitions.  It's possible I've missed something and that's why I have to do it that way, but it works.

Dave :)

---

### Post by mhgsys on 2009-03-15
try another keyboard. 

Your suppose to press the "any" key. 
lol.

Seriously, 

Try another keyboard
Windows is a bitch with keyboards and boot cd's
wireless keyboards won't work f.e

---

### Post by egalvan on 2009-03-15
> **Edward B. said:**
> starts to boot from the Windows CD for some reason, it goes straight into Ubuntu!

However, if I boot from CD using the Ubuntu CD, then the computer boots correctly (that is, from the Ubuntu CD, not from Ubuntu on my hard drive).


On many Win-XP install cd's, there is a short message that comes up...
(it is easy to miss...)
the screen is blanked, and at the very top, left side of the screen...


"**To boot from CD, press any key**"

It only shows a few seconds....
if no key is pressed, the machine skips the CD.


As for the USB keyboard not being recognized by the BIOS during boot, this is under the BIOS option named

"USB Legacy"


this should be set to 

"true"
or
"On"
or
"Enabled"

The location varies from one BIOS maker to another. You need to look for it...sorry I can't be of more help.

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

### Post by egalvan on 2009-03-15
> **mhgsys said:**
> Seriously, 

Try another keyboard
Windows is a bitch with keyboards and boot cd's
wireless keyboards won't work f.e

I use (exclusively) wireless Logitech keyboards (and mice)

Since Win2K.

Never a problem.

As long as the BIOS sees it.

Some older BIOS's have problems with USB.

LEGACY mode helps with this.

---

### Post by lisati on 2009-03-15
> **mhgsys said:**
> try another keyboard. 

Your suppose to press the "any" key. 
lol.

Seriously, 

Try another keyboard
Windows is a bitch with keyboards and boot cd's
wireless keyboards won't work f.e
I'm still trying to find the "any" key :D

I agree: try another keyboard. Sometimes they develop faults - a common one in my household is from assorted muck that finds its way in because of people smoking near the computers. They don't always like being dropped either.

---

### Post by egalvan on 2009-03-15
> **lisati said:**
> I'm still trying to find the "any" key :D


Absolutely!

seems the keyboard makers would have figured out just how common this key is... 
Why they don't include it is beyond my understanding.

---

### Post by ugm6hr on 2009-03-15
> **anewguy said:**
> It has been my experience in the past that Windows XP will NOT install over the top of any unknown active primary partition type.  

I have found this too.

However, this is not the problem here, since the Windows installer CD should still boot, but then refuses to see the hard drive in your scenario.

Edward B appears unable to boot to the Windows CD, which is presumably because his USB keyboard is not recognized during the "Press any key" stage of booting the Windows CD (which is not required for the Ubuntu LiveCD).

As others have suggested, borrow a PS2 keyboard from someone.

---

### Post by mister_pink on 2009-03-15
I'll try and consolidate some advice I think:

Some old bios do not support USB keyboards, or need an option in the bios to be changed so that they do. Changing this option is an obvious chicken and egg issue, as you need a working keyboard to change it. However, this does not seem to be the issue here - if you can get into the bios, your keyboard is working.

XP may indeed have issues installing over ubuntu, but again, you would still get into the setup if that were the issue. Should that issue arise later, once you're into the XP setup, then you need to boot the ubuntu live CD and delete ubuntu with the partition editor in System -> Administration.

I suggest you try booting the liveCD. If this works, then your computer is set to boot from cds correctly. 

If you still can't see anything coming up when you try and boot with the XP cd then I think there's probably something wrong with the CD. You can check this one of two ways: either stick it in another computer and try and boot from it, or install virtualbox in ubuntu (sudo apt-get install virtualbox) and make a new virtual machine. Set it to boot from your cd rom drive and see if it will work.

Note that in your situation I don't think a virtual XP install will be much use as you state you want to use it for games. If you have a relatively modern computer though, virtualbox will suffice for most other things.

---

### Post by betrunkenaffe on 2009-03-15
Ok, so it seems you have been able to confirm that your bios should handle the keyboard since you can get into the bios, I couldn't with Fiancee's and in fact started getting errors that keyboard wasn't detected (we ran into it when I bought her a new keyboard).

I have run into some weird windows installer errors however I have installed with an active Linux install in place. Do you have more than 1 partition or just the one? If just the one then boot from the livecd, delete the partition, make another much smaller one (about 5GB or so) and then save the boot table. I'd finish installing Ubuntu again just in case. Restart and use the windows CD, see if you can get in then. This would bypass any issues you might run into with the windows installer and your partitions.

Barring everything else, you'll need to try a ps2 keyboard because the antique installer (even at the time it came it out) that XP uses is probably not liking your keyboard at all.

---

### Post by presence1960 on 2009-03-15
I know firsthand you can install Windows after Ubuntu because I just did it when my DSL went bad and the techs either didn't know how or didn't want to work on a linux box. I created a NTFS partition with gparted. Then booted from my XP install CD and installed XP to the NTFS partition. I still think it is your keyboard. Go buy a $10 PS2 keyboard at Walmart and see what happens. If that does not work WE probably are missing some piece of info on this matter, any ideas OP? Do you have an NTFS partition set up or is it unallocated? Is there anything, no matter how trivial you may have forgotten to tell us?

---

### Post by Hobgoblin on 2009-03-15
> **Edward B. said:**
> 

I tried booting from the CD on a restart, but I was not able to do so as it required me to press a key on my keyboard and my keyboard will not allow me to make any inputs until the system is started.


You need to go into your BIOS and enable USB keyboard support, which may be called USB legacy support or something similar.

For info: The Windows CD detects another operating system, and being "clever" it decides you don't want to boot from the CD after all and boots from the HDD unless you press a key to over ride this feature.

---

### Post by Edward B. on 2009-03-15
> **egalvan said:**
> On many Win-XP install cd's, there is a short message that comes up...
(it is easy to miss...)
the screen is blanked, and at the very top, left side of the screen...


"**To boot from CD, press any key**"

It only shows a few seconds....
if no key is pressed, the machine skips the CD.


As for the USB keyboard not being recognized by the BIOS during boot, this is under the BIOS option named

"USB Legacy"


this should be set to 

"true"
or
"On"
or
"Enabled"

The location varies from one BIOS maker to another. You need to look for it...sorry I can't be of more help.

Thank you!

I feel so retarded, but, yes, I needed to enable USB support in BIOS - it was set to disabled for some reason!

I successfully installed Windows XP on the partition, and then successfully changed it so that Ubuntu now loads instead of Windows XP.

However, when I go to the grub menu Windows XP is not an option!

I have four or five ?versions? of Ubuntu to choose from, but no XP.

This is what I changed my menu options to in the terminal:

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
timeout		3

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
# kopt=root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=94397621-4361-4dea-b99f-08b9e877ce1e

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,1)
makeactive
chainloader+1

-------------

I saved the original menu like the guide said, then pasted into the menu when I restarted Ubuntu after installing XP. Have I done something wrong here? I went back and put a space in the last item between "chainloader" and "+1" but this did nothing.

I can feel it.... it's coming close... the awesomeness of Ubuntu combined with the ability to play good PC games... help me complete my computer's transformation into an evil machine!

(Side note: I could not get on the Internet with my new installation of XP. I have a cable connection that does not require a password or user name. I have an X-Box 360. Whenver I want to switch between my comp and the 360 (using same ethernet cable) I have to call my provider and have them reset the modem. If I reset the modem on my own, it will not work and I will not be able to switch devices. Hopefully, this doesn't translate over to different OS. When I switched from DSL to cable, the cable company assured me there would be no difference in service except for their faster speeds... yeah, right. Load of crap.)

---

### Post by Edward B. on 2009-03-15
Hmmm... just noticed all of the kernels listed above END DEBIAN are the options I have when going to the grub menu.

Should I put the Windows XP info above the END DEBIAN as well? I thought the guide said to enter that info below END DEBIAN, but I may have misunderstood.

---

### Post by carml on 2009-03-15
Your installation is right the way is now,because the list of OS is made so on every dual boot machine, I mean the different OS installed are separated in the list.:)

---

### Post by Edward B. on 2009-03-15
> **carml said:**
> Your installation is right the way is now,because the list of OS is made so on every dual boot machine, I mean the different OS installed are separated in the list.:)

Any idea why this is not working then? 

Slash/

How do I boot into XP?

---

### Post by presence1960 on 2009-03-15
> **Edward B. said:**
> Any idea why this is not working then? 

Slash/

How do I boot into XP?

In terminal > sudo fdisk -l

post the output of this command

---

### Post by carml on 2009-03-15
No ideas, I'm sorry.I have a dual boot machine,but with Windows installed first.Did you tried to reboot once you installed WinXP? 
If all went well you'll notice at the bottom the entry "Windows Xp" or something similar...

---

### Post by anewguy on 2009-03-15
> **presence1960 said:**
> I know firsthand you can install Windows after Ubuntu because I just did it when my DSL went bad and the techs either didn't know how or didn't want to work on a linux box. I created a NTFS partition with gparted. Then booted from my XP install CD and installed XP to the NTFS partition. I still think it is your keyboard. Go buy a $10 PS2 keyboard at Walmart and see what happens. If that does not work WE probably are missing some piece of info on this matter, any ideas OP? Do you have an NTFS partition set up or is it unallocated? Is there anything, no matter how trivial you may have forgotten to tell us?


But -- you're just reinforcing what I said - you have to have an open or ntfs partition FIRST.  You can't install if all the partitions on the disk are all used for Ubuntu.  MANY of us in our less experienced days reinstalled Windows many times trying to get Windows and Ubuntu to co-exist.  That's why the recommended (mind you not the only, but the recommended) way is to install Windows first, then shrink the size of the Windows partition and install Linux.

My reasoning for deleting the partitions and then trying the Windows CD was two-fold - first to get the other partitions off the drive so we knew he was working with a "clean" drive, and second so we could see what kind of error message he would get if it couldn't boot the Windows CD then - it would help us locate the problem.

Dave :)

---

### Post by Edward B. on 2009-03-15
> **presence1960 said:**
> In terminal 

post the output of this command

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors




Does this help at all?

---

### Post by anewguy on 2009-03-15
I would suggest you just try to rebuild grub since it will auto-detect the disk(s) and OS's.  There are many threads here for doing that, but thought I would post this copy of a reply to another thread - it shows it all.

presence1960 
Gee! These Aren't Roasted!

 
 
 

Join Date: Sep 2008
Location: PA
Posts: 170 
Kubuntu 8.10 Intrepid Ibex 
  Re: Reinstalling XP, retaining dual boot (Intrepid) 

--------------------------------------------------------------------------------

I had my dual boot set up on separate hard disks. I may be wrong, but I believe when you install windows on the same physical disk after Linux Windows will wipe GRUB. All you need to do after Windows is installed is pop in the Ubuntu Live CD, open a terminal and follow these instructions to put GRUB back :


Quote:
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
whatever your hard disk + partition nr is, to install GRUB to a 
partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD  

.
__________________
Kubuntu 8.10 x86-64 - AMD 64 x2 +5400 2.8 Ghz/Biostar TF7050-M2 Mobo/4 Gb dual channel PC 6400 DDR2 RAM/GeForce 8600 GT 512 MB DDR2/250 GB Seagate SATA Hd/160 GB Seagate IDE Hd/DVD-RAM Lightscribe/Apevia Black X-plorer case...built 2/12/2008  
      

After you try that, post back with what happened.

Dave :)

---

### Post by ugm6hr on 2009-03-15
> **Edward B. said:**
> Does this help at all?

You typed it wrong.

It's sudo fdisk -l (i.e. minus little ell)

---

### Post by presence1960 on 2009-03-15
> **Edward B. said:**
> Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors




Does this help at all?
 No - open a terminal and copy and paste this command in the terminal ```
sudo fdisk -l
```, then press enter. It will ask for your password- enter password then hit enter. Then post the outcome that shows up. here is mine:

> raz@raz-desktop ~ $ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16840   135267268+  83  Linux
/dev/sda2           16841       19457    21021052+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdb2            2612        4569    15727635   83  Linux
/dev/sdb3            4570       29879   203302575   83  Linux
/dev/sdb4           29880       30401     4192965   82  Linux swap / Solaris


P.S. just realized you may not know that is a lower case L, not a 1(one) in sudo disk -l

---

### Post by Edward B. on 2009-03-15
Whoops - those little "l's" and "1's" mess me up.

Here's what the terminal showed:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf139f139

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23651   189976626   83  Linux
/dev/sda2   *       23652       30025    51199155    7  HPFS/NTFS
/dev/sda3           30026       30401     3020220    5  Extended
/dev/sda5           30026       30401     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)




Does that help?

---

### Post by presence1960 on 2009-03-15
> **Edward B. said:**
> Whoops - those little "l's" and "1's" mess me up.

Here's what the terminal showed:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf139f139

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23651   189976626   83  Linux
/dev/sda2   *       23652       30025    51199155    7  HPFS/NTFS
/dev/sda3           30026       30401     3020220    5  Extended
/dev/sda5           30026       30401     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)




Does that help?

put this as your windows entry on menu.lst :

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP 
root		(hd0,1)
savedefault
chainloader	+1
```

that should do it.

---

### Post by presence1960 on 2009-03-15
> **anewguy said:**
> I would suggest you just try to rebuild grub since it will auto-detect the disk(s) and OS's.  There are many threads here for doing that, but thought I would post this copy of a reply to another thread - it shows it all.

presence1960 
Gee! These Aren't Roasted!

 
 
 

Join Date: Sep 2008
Location: PA
Posts: 170 
Kubuntu 8.10 Intrepid Ibex 
  Re: Reinstalling XP, retaining dual boot (Intrepid) 

--------------------------------------------------------------------------------

I had my dual boot set up on separate hard disks. I may be wrong, but I believe when you install windows on the same physical disk after Linux Windows will wipe GRUB. All you need to do after Windows is installed is pop in the Ubuntu Live CD, open a terminal and follow these instructions to put GRUB back :


Quote:
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
whatever your hard disk + partition nr is, to install GRUB to a 
partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD  

.
__________________
Kubuntu 8.10 x86-64 - AMD 64 x2 +5400 2.8 Ghz/Biostar TF7050-M2 Mobo/4 Gb dual channel PC 6400 DDR2 RAM/GeForce 8600 GT 512 MB DDR2/250 GB Seagate SATA Hd/160 GB Seagate IDE Hd/DVD-RAM Lightscribe/Apevia Black X-plorer case...built 2/12/2008  
      

After you try that, post back with what happened.

Dave :)

Dave, I thought about this route, but I thought he was having enough difficulty with commands right now. But this or editing menu.lst will work. BTW difficulties are a good thing because through it all we actually learn something by following someone else's guidance. if we paid attention we now know something new we didn't know previously.

---

### Post by egalvan on 2009-03-15
The following are totally OPTIONAL, but can make life easier...

you have your menu.lst

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]time out 3[/COLOR] <-- [I]the time grub waits to continue,
three seconds is kinda short, I have mine set at 30...
 gives me enough time to glance at the monitor while doing other things.[/I]

--------------

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]hiddenmenu [/COLOR] <-- [I]if this is enabled, then the grub menu is hidden, and you have to press 'esc' to see the menu...
 within the 'timeout' period mentioned before.
changing this to (add [COLOR="Red"]#[/COLOR] to the front)
[/I]
[COLOR="Red"]#[/COLOR]hiddenmenu

*allows the menu to be seen.*

--------------------

# Pretty colours
[COLOR="Red"]#color cyan/blue white/blue[/COLOR]  <-- [I]this prints the text in colors, instead of plain white text on blackk screen.

removing the # gives a more pleasing GRUB boot menu...
I prefer it, your likes may differ.[/I]

#Pretty colours
color cyan/blue white/blue


ErnestG

---

### Post by presence1960 on 2009-03-15
> **egalvan said:**
> The following are totally OPTIONAL, but can make life easier...

you have your menu.lst

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]time out 3[/COLOR] <-- [I]the time grub waits to continue,
three seconds is kinda short, I have mine set at 30...
 gives me enough time to glance at the monitor while doing other things.[/I]

--------------

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]hiddenmenu [/COLOR] <-- [I]if this is enabled, then the grub menu is hidden, and you have to press 'esc' to see the menu...
 within the 'timeout' period mentioned before.
changing this to (add [COLOR="Red"]#[/COLOR] to the front)
[/I]
[COLOR="Red"]#[/COLOR]hiddenmenu

*allows the menu to be seen.*

--------------------

# Pretty colours
[COLOR="Red"]#color cyan/blue white/blue[/COLOR]  <-- [I]this prints the text in colors, instead of plain white text on blackk screen.

removing the # gives a more pleasing GRUB boot menu...
I prefer it, your likes may differ.[/I]

#Pretty colours
color cyan/blue white/blue


ErnestG
```

sudo apt-get install startupmanager
```

will accomplish these tasks and many more by installing startup manager

---

### Post by anewguy on 2009-03-15
> **presence1960 said:**
> Dave, I thought about this route, but I thought he was having enough difficulty with commands right now. But this or editing menu.lst will work. BTW difficulties are a good thing because through it all we actually learn something by following someone else's guidance. if we paid attention we now know something new we didn't know previously.

I was a little leary myself, but since it didn't seem to be going anywhere at the time, I thought what the heck.  It's good to see others are getting him through this.  When I didn't see valid output from fdisk I was a little worried, but you guys got him straightened out.

Thanks!
Dave :)

---

### Post by anewguy on 2009-03-15
> **egalvan said:**
> Absolutely!

seems the keyboard makers would have figured out just how common this key is... 
Why they don't include it is beyond my understanding.

Back when I was working in tech support, you'd be amazed at how many people asked where that key was.  When I told them to just press any key they would get upset and say "I don't HAVE an any key!".  Eventually I just told them to press the space bar or enter.

Dave :)

---

### Post by Edward B. on 2009-03-16
> **presence1960 said:**
> put this as your windows entry on menu.lst :

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP 
root		(hd0,1)
savedefault
chainloader	+1
```

that should do it.

XP is still an option to boot into.

This is what I have on menu file.

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
timeout		3

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
# kopt=root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=94397621-4361-4dea-b99f-08b9e877ce1e

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=94397621-4361-4dea-b99f-08b9e877ce1e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		94397621-4361-4dea-b99f-08b9e877ce1e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP 
root		(hd0,1)
savedefault
chainloader	+1





Does this look okay?

---

### Post by ugm6hr on 2009-03-16
> **Edward B. said:**
> Does this look okay?

Yes.

Give it a try.

---

### Post by Edward B. on 2009-03-16
> **ugm6hr said:**
> Yes.

Give it a try.

Well, the good news is that it looks okay.

Bad news is that it doesn't work. When I go into the grub menu I am still given only the four or five options of Ubuntu - no Windows XP.

To make matters worse, my [earlier problem]("http://ubuntuforums.org/showthread.php?t=1093829") with Ubuntu during start up has inexplicably returned even with my graphics card uninstalled.

Garr.... might be left with no choice but to return to Windows.

---

### Post by Edward B. on 2009-03-16
Okay, if I need to wipe Ubuntu and just install XP, how would I best go about doing that now that I have the hard drive partitioned with Ubuntu on one section and XP on another?

---

### Post by Edward B. on 2009-03-16
I've also noticed since installing XP on the partition, that Ubuntu does not play video well on the Internet. YouTube, in particular, is exhibiting a significant choppiness... of course, I suppose this could be YouTube...

---

### Post by kelvin spratt on 2009-03-16
> **Edward B. said:**
> Well, the good news is that it looks okay.

Bad news is that it doesn't work. When I go into the grub menu I am still given only the four or five options of Ubuntu - no Windows XP.

To make matters worse, my [earlier problem]("http://ubuntuforums.org/showthread.php?t=1093829") with Ubuntu during start up has inexplicably returned even with my graphics card uninstalled.

Garr.... might be left with no choice but to return to Windows.

If you remove your graphics card you don't have a display so you will not see any of the things you say, so are you running a internal card ie built in and plugging in a card as well if so you need to plug the monitor into the removable card and reset you bios for that card. 
You can't just put entries into your grub menu 1st and make Xp work use the Xp install disc to restore mbr.
Then use the Ubuntu live cd and follow the previous instructions for grub or just wipe Ubuntu off no need to reinstall XP.
then you need to install drivers for your choppy video.

---

### Post by presence1960 on 2009-03-16
can you add this under ### END DEBIAN AUTOMAGIC KERNELS LIST 

and keep a line space between ### END DEBIAN AUTOMAGIC KERNELS LIST & your windows entry.

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

I compared your menu.lst to mine and this seems to be the only difference. Try it see what happens,

---

### Post by ugm6hr on 2009-03-16
> **Edward B. said:**
> When I go into the grub menu I am still given only the four or five options of Ubuntu - no Windows XP.

There should at least be an entry, given you have added a "title" line; whether it boots Windows is a different issue.

Can you show what else is in your /boot/grub/ folder?

```
ls -la /boot/grub
```

---

### Post by Edward B. on 2009-03-16
Not sure if this is what you were looking for or not:

total 240
drwxr-xr-x 2 root root   4096 2009-03-16 17:58 .
drwxr-xr-x 3 root root   4096 2009-03-02 18:55 ..
-rw-r--r-- 1 root root    197 2009-03-02 17:55 default
-rw-r--r-- 1 root root     15 2009-03-02 17:55 device.map
-rw-r--r-- 1 root root   8108 2009-03-02 17:55 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-03-02 17:55 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-03-02 17:55 installed-version
-rw-r--r-- 1 root root   8712 2009-03-02 17:55 jfs_stage1_5
-rw-r--r-- 1 root root   5082 2009-03-16 17:58 menu.1st
-rw-r--r-- 1 root root   4960 2009-03-16 16:41 menu.1st~
-rw-r--r-- 1 root root   4798 2009-03-02 18:54 menu.lst
-rw-r--r-- 1 root root   4798 2009-03-02 18:54 menu.lst~
-rw-r--r-- 1 root root   7352 2009-03-02 17:55 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-03-02 17:55 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-03-02 17:55 stage1
-rw-r--r-- 1 root root 121460 2009-03-02 17:55 stage2
-rw-r--r-- 1 root root   9556 2009-03-02 17:55 xfs_stage1_5

I, like many other things, can not make heads or tails of this.

---

### Post by Edward B. on 2009-03-16
> **presence1960 said:**
> can you add this under ### END DEBIAN AUTOMAGIC KERNELS LIST 

and keep a line space between ### END DEBIAN AUTOMAGIC KERNELS LIST & your windows entry.



I compared your menu.lst to mine and this seems to be the only difference. Try it see what happens,

Did not work - got same results. Thanks, though.

---

### Post by meierfra. on 2009-03-16
> -rw-r--r-- 1 root root 5082 2009-03-16 17:58 menu.1st
-rw-r--r-- 1 root root 4960 2009-03-16 16:41 menu.1st~
-rw-r--r-- 1 root root 4798 2009-03-02 18:54 menu.lst

You are editing the wrong file. You need to edit "menu.lst"  (the "l" is a lower case "L" not the number one.)

---

### Post by Edward B. on 2009-03-16
> **meierfra. said:**
> You are editing the wrong file. You need to edit "menu.lst"  (the "l" is a lower case "L" not the number one.)

....

....

I am retarded. :D

That was the problem. I can now boot into XP, no problem.

*smacks forehead*

Wow....

Thanks for everything, guys, I really appreciate it.

Two minor questions now:

1) Was the 1 (number 1) file I edited doing anything? Should I change that or is it just a nothing file that I was changing?

2) Can not connect to Internet through XP. I'm guessing this is likely an issue with my cable provider?

Thanks again!!!

---

### Post by presence1960 on 2009-03-16
Edward, where did those files -> menu.1st with the number "1" come from? Did you create them? They are not needed, You should be working with the one with a lower case "L" -> menu.lst. Back in post 50 you stated you get confused between the two characters. Stick with the lower case "L".

---

### Post by presence1960 on 2009-03-16
> **Edward B. said:**
> ....

....

I am retarded. :D

That was the problem. I can now boot into XP, no problem.

*smacks forehead*

Wow....

Thanks for everything, guys, I really appreciate it.

Two minor questions now:

1) Was the 1 (number 1) file I edited doing anything? Should I change that or is it just a nothing file that I was changing?

2) Can not connect to Internet through XP. I'm guessing this is likely an issue with my cable provider?

Thanks again!!!

It (file with #1 in it)is serving no purpose, it is not needed!! Glad you finally got it going  :)

---

### Post by meierfra. on 2009-03-16
[QUOTE=anewguy]I would suggest you just try to rebuild grub since it will auto-detect the disk(s) and OS's. [/QUOTE]

Just for future references, reinstalling grub does not auto-detect the OS's. Infact, reinstalling grub does not change "menu.lst"  at all.

You can use "sudo update-grub" to auto-detect all the Ubuntu kernels. But "update-grub" will no detect any other OS's 

The only program I know  which auto-detects all the OS's is "os-proper". But "os-proper" only works in conjugation with  a Debian installer and, as far as I know, cannot be used after Ubuntu is installed.

---

### Post by anewguy on 2009-03-16
> **meierfra. said:**
> Just for future references, reinstalling grub does not auto-detect the OS's. Infact, reinstalling grub does not change "menu.lst"  at all.

You can use "sudo update-grub" to auto-detect all the Ubuntu kernels. But "update-grub" will no detect any other OS's 

The only program I know  which auto-detects all the OS's is "os-proper". But "os-proper" only works in conjugation with  a Debian installer and, as far as I know, cannot be used after Ubuntu is installed.


Maybe not the proper terminology, but when the mbr has been overwritten, such as a Windows install, the method mentioned does restore the mbr to point to the grub disk containing the menu.lst.  This was an attempt at trying to get the mbr restored without going into a lot of detail for a newbie.  So technically no update-grub does not detect OS's, etc., it simply installs the mbr with a pointer to the disk pointed to by (hd0,1) in the examples posted in this thread.  It does, however, detect the kernels installed and it does update the menu.lst unless you specify otherwise.  I apologize if this was taken quite literally, when it was meant as a simple incentive to try to use update-grub to get the mbr pointing back to the Ubuntu disk.

Dave :)

---

### Post by presence1960 on 2009-03-16
I am just glad Edward got it working finally. BTW meierfra, I appreciate your knowledge of Linux. I always try to learn from your posts. It is funny now but Edward was a tough nut to crack. First with the USB keyboard support in BIOS being disabled (even after someone told him to check it at least 20 posts earlier-LOL) then with the confusion between "1" and "l". It's funny now but while everyone was trying to help him it wasn't funny then! Welcome to the community Edward...enjoy!

---

### Post by Edward B. on 2009-03-17
> **presence1960 said:**
> I am just glad Edward got it working finally. BTW meierfra, I appreciate your knowledge of Linux. I always try to learn from your posts. It is funny now but Edward was a tough nut to crack. First with the USB keyboard support in BIOS being disabled (even after someone told him to check it at least 20 posts earlier-LOL) then with the confusion between "1" and "l". It's funny now but while everyone was trying to help him it wasn't funny then! Welcome to the community Edward...enjoy!

Man, I seriously hope I didn't tick anyone off here with my own ineptitude. I really appreciate everyone's help – just about the fastest response times I've seen on a forum.

Maybe it's just me, but "l" and "1" look a lot alike to me, which was causing all of the problems. The BIOS thing was my fault – I didn't notice that someone had mentioned early on to check the BIOS menu to make sure it was supporting the keyboard. I guess I just read that "Your BIOS may not support the keyboard – get a PS2 keyboard."

I'm glad someone repeated that information because I did see it the second time around.

Oh, and I'm sure I will be back on this forum in a matter of days with more questions. 

Although I'll try to pay better attention to the answers I get this time. :)

---

### Post by stchman on 2009-03-17
> **Edward B. said:**
> Whenever I put in the Windows XP install CD I get this message:

Could not display "/media/cdrom0/autorun.inf".
There is no application installed for this file type

If I go into the CD and try to run the .exe file, I get this message:

An error occurred while loading the archive.

Command Line Input

[/media/cdrom0/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/setup.exe or
          /media/cdrom0/setup.exe.zip, and cannot find /media/cdrom0/setup.exe.ZIP, period.



I tried booting from the CD on a restart, but I was not able to do so as it required me to press a key on my keyboard and my keyboard will not allow me to make any inputs until the system is started.

I am putting a gun to my head, here, any help would be really appreciated.

If you want to install XP within Ubuntu you need Virtual Box.

You can also install XP in a dual boot environment.  Now installing XP after Ubuntu will cause GRUB to be wiped out.

---

### Post by presence1960 on 2009-03-17
> **Edward B. said:**
> Man, I seriously hope I didn't tick anyone off here with my own ineptitude. I really appreciate everyone's help – just about the fastest response times I've seen on a forum.

Maybe it's just me, but "l" and "1" look a lot alike to me, which was causing all of the problems. The BIOS thing was my fault – I didn't notice that someone had mentioned early on to check the BIOS menu to make sure it was supporting the keyboard. I guess I just read that "Your BIOS may not support the keyboard – get a PS2 keyboard."

I'm glad someone repeated that information because I did see it the second time around.

Oh, and I'm sure I will be back on this forum in a matter of days with more questions. 

Although I'll try to pay better attention to the answers I get this time. :)

You didn't piss me off, I was glad to try to help you, as I am sure everyone else is too! Mistakes are part of learning, now you know a few things that you didn't prior. The first time I tried Ubuntu I downloaded the iso and burned it to a disk. I didn't bother to read anything at all and I screwed up the install when it came to partition my hard drives. I wiped my windows install, didn't like Ubuntu (or so I thought) and then formatted the Ubuntu partition. Rebooted expecting windows to come up and a black screen with a blinking cursor. I was so mad! But that was my fault because I did no prep, I just jumped right in because I thought I knew what to do. Maybe if I had read then came to the forum my original install would have worked. Live and learn!

---

