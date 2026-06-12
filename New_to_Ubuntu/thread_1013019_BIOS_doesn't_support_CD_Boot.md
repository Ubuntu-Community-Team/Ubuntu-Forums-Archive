---
title: "BIOS doesn't support CD Boot"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by ubfu on 2008-12-16
Using Pentium 3 and the motherboard BIOS doesn't support CD Boot.

How do I make it to boot or on a cd rom ?
I do not plan to install ubuntu or other linux distro.
Just wanted to test on a live cd.Such as Knoppix Linux and puppy linux.
Having a floppy disk , how to I make it to boot at cd rom ?

---

### Post by HermanAB on 2008-12-16
Hmm, if it doesn't support CD boot, then it probably doesn't support USB boot either, however, it would be worth a looksee in the BIOS boot sequence setting.  The problem with booting off a floppy disk is that they are too small for anything serious these days.

If it was me, then I would try to upgrade the BIOS - look at the manufacturer web site for an upgrade.

---

### Post by ubfu on 2008-12-16
The pc was like 8 years ago doubt they still keep the bios.

I seriously wanted to create a bootable floppy disk to boot on the cd rom.
Having problem with window 98 which i can't go online.Wanted to diagnostic whether it's win98 driver problem or network card problem.
So the solution is to run a livecd to test without install it.

My previous thread [http://ubuntuforums.org/showthread.php?t=1011901](http://ubuntuforums.org/showthread.php?t=1011901)

Thank you :)

---

### Post by MrWES on 2008-12-16
> **ubfu said:**
> Using Pentium 3 and the motherboard BIOS doesn't support CD Boot.

How do I make it to boot or on a cd rom ?
I do not plan to install ubuntu or other linux distro.
Just wanted to test on a live cd.Such as Knoppix Linux and puppy linux.
Having a floppy disk , how to I make it to boot at cd rom ?

You might want to try this site:

[https://help.ubuntu.com/community/SmartBootManager]("https://help.ubuntu.com/community/SmartBootManager")

After thought; if you're planning on running Puppy Linux, you can use WakePup to boot from a floppy.

Bill

---

### Post by ubfu on 2008-12-16
> **MrWES said:**
> You might want to try this site:

[https://help.ubuntu.com/community/SmartBootManager]("https://help.ubuntu.com/community/SmartBootManager")

After thought; if you're planning on running Puppy Linux, you can use WakePup to boot from a floppy.

Bill

Thanks , went to smartbootmanager link .So which one is the correct file to download
[http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481](http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481)

btmgr-3.7-1.i386.rpm  Mirror	327814	i386
btmgr-3.7-1.src.rpm   Mirror	195409	i386
btmgr-3.7-1.tar.gz    Mirror	193090	i386
sbminst               Mirror	 41220	i386
sbminst.exe           Mirror	 69612	i386
themes-3.7.tgz        Mirror	 30334	i386
user-guide-3.7.tgz    Mirror     37796	i386
:confused:

Went and found wakepup2 [http://www.murga-linux.com/puppy/viewtopic.php?p=122924#122924](http://www.murga-linux.com/puppy/viewtopic.php?p=122924#122924) but how do I insert it into the floppy disk ?

---

### Post by ubfu on 2008-12-17
> **ubfu said:**
> Thanks , went to smartbootmanager link .So which one is the correct file to download
[http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481](http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481)

btmgr-3.7-1.i386.rpm  Mirror	327814	i386
btmgr-3.7-1.src.rpm   Mirror	195409	i386
btmgr-3.7-1.tar.gz    Mirror	193090	i386
sbminst               Mirror	 41220	i386
sbminst.exe           Mirror	 69612	i386
themes-3.7.tgz        Mirror	 30334	i386
user-guide-3.7.tgz    Mirror     37796	i386
:confused:

Went and found wakepup2 [http://www.murga-linux.com/puppy/viewtopic.php?p=122924#122924](http://www.murga-linux.com/puppy/viewtopic.php?p=122924#122924) but how do I insert it into the floppy disk ?

Sorry any help here ?:-?

---

### Post by mrbiggbrain on 2008-12-17
> **ubfu said:**
> Sorry any help here ?:-?


its probably a .img file of a floppy, you need to get a floppy disk image writer.

---

### Post by ubfu on 2008-12-17
> **mrbiggbrain said:**
> its probably a .img file of a floppy, you need to get a floppy disk image writer.

Between this 2 which one I should download ? 

btmgr-3.7-1.i386.rpm 
or
btmgr-3.7-1.src.rpm ?
What is src ?

---

### Post by cariboo on 2008-12-17
I would really have a good look at your bios again. The last time I saw a computer that wouldn't boot from a cd-rom was some of the early pentium 1 motherboards. If you are missing the cd-rom boot option, you probably have a corrupted bios, which could lead to other problems. I would reset the bios and check again. You can reset the bios by using the shorting jumper on the motherboard, or remove the battery for about 5 minutes.

Jim

---

### Post by mrbiggbrain on 2008-12-17
> **ubfu said:**
> Between this 2 which one I should download ? 

btmgr-3.7-1.i386.rpm 
or
btmgr-3.7-1.src.rpm ?
What is src ?

FYI: src stands for source, it means the file contains source code (and probably a makefile if its a program) to put it simple, its the actual programing code, if you wanted to setup, compile, and enhance a program for yourself or others, this would be the option... otherwise you want to go with the version that works best for your processor 386/486/586/686/x86_64

now if you have the ubuntu install cd then you can look under 

*/install/sbm.bin*

copy this to c:/linboot/ (make it if you have too)

the download and setup rawwrite (might be a command line only program) set it up under c:/linboot/ where all the files exstract to c:/linboot/ not a subfolder (like c:/linboot/rawwrite/)

XP: start >> run >> "cmd"

vista start >> (searchbox = cmd >> enter)

the command prompt should load,

type: 
```

cd c:/linboot/

format a:

rawrite -f sbm.bin





```

the reason iv asked you to it it this way is that all the versions youv given me, well not linux specific (tar.gz CAN techicly be opened by some windows programs) are linux centric. well the version o the cd, already uncompressed will work far better and easier for you

---

### Post by philinux on 2008-12-17
My pentium 3 from 1999 booted from cdrom. I'd be amazed if this one didn't. Like caribou says have another look a the bios.

---

### Post by rlunger on 2008-12-17
If you can't boot directly to CD, you can boot to a floppy with a CD mounting program on it, and go from there.  I've done it on various computers that can't boot from CD.  The programs aren't that hard to find or use.  Just try google-ing something like 'bootable cd mounter' or something similar.  BTW, what OS are you using?

---

### Post by Malalo on 2008-12-17
Check out [Bootdisk.com]("http://www.bootdisk.com") there you can easily get an floppy disk image with CD-ROM compatibility. I've used this site lots of times.

---

### Post by ubfu on 2008-12-18
Thank you very much for the suggestion.

Actually , the PC was an old pentium 3 with Window 98 installed which I still don't know why I can't set the booting preferences.When I press enter , it just skip through.I can't select like other motherboard to cd rom.

The pc having problem connecting to the internet.Tested with adsl modem on other pc and it work.I suspect network card or the driver.The only way to test is to boot into linux (puppy or ubuntu or koppnix) and try to connect to the internet.
That's the main reason I wanted it to run on linux plus the window 98 is full with adware.
If it works booting and tested it's the driver fault.I will try to partition the hard disk and dual boot.
Keeping window 98 and also able to boot into linux.

This really giving me a headache.So does the bootdisk works too on any linux ? I saw puppy linux needs it own bootable program while ubuntu also the same.
Or I can just download a disk which candirect boot from cd ? Sorry really poor on computer especially those old window 98.
Thank you , hope someone can guide me step by step

---

### Post by theamber on 2008-12-18
Have you try removing the hard disk? and see if it takes the sequence to the CDROM.

---

### Post by plucky on 2008-12-18
> Actually , the PC was an old pentium 3 with Window 98 installed which I still don't know why I can't set the booting preferences.When I press enter , it just skip through.I can't select like other motherboard to cd rom.


Select the CDrom and use  "Page Up"  or "Page Down" instead of enter to move it up or down.


Good Luck

---

