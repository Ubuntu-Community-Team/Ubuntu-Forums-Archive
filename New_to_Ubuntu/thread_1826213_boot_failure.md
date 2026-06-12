---
title: "boot failure"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by Dna_Boy on 2011-08-16
Hello, 

i'm new here so I hope I'm asking this in the right forum. 

I've noticed my ubuntu gnome version becoming slow in the past days, after some file scanning into an specific shared folder. I was trying to access those files and the system was very slow. After a reboot it was fine again, but if I tried to access those files again, it became unstable again. So I was thinking about how to access those files without causing problems, but then the computer froze and now it doesn't boot at all. 

The last error msgs are:

init: tty1 main process [noparse](1808)[/noparse] terminated with status 255
init: tty1 main process ended, respawning
init: tty1 respawnig too fast, stopped 

I used the live cd, and I did already a disc check and a memory check, no error was reported. Apparently this live cd I own, doesn't have a repair option :(

So, I'm asking what can I do so that I don't lose all the files I have in some folders. If I install a fresh copy, will the system be formated?Will I lose the files? Is there any way I can access them, and eventually copy/move them, using Live cd?

Sorry for my not so good english.

Thanks

---

### Post by Dna_Boy on 2011-08-17
No one can help?

Could someone at least answer some of my questions?

---

### Post by Overcast32 on 2011-08-17
> **Dna_Boy said:**
> No one can help?

Could someone at least answer some of my questions?

I can try to help with backing up the data... maybe :)

I would think you should be able to boot to live CD and copy the data off to a USB Flash drive. Otherwise, the default install will wipe and reformat the disks.

Of course, that being said - I'm pretty sure you can do a custom install and not format, but that would get a lot more complicated. If the Live CD works and can get you to the Internet - you might even be able to find some free Internet storage to upload the data to, if a USB flash drive is a problem for whatever reason. 

If you need the data, I would take care to back it up before doing anything at all. Once you know you have a good backup - it wouldn't hurt to try and 'rescue' the system. At that point, you have your important data, and the system needs repair/reloaded - so you can't really harm anything by attempting a repair or install without formatting - the worst off you might be is having to do a full re-load with clean partitions.

What error does it get on boot?

---

### Post by Blasphemist on 2011-08-17
It's not really that complicated to re-install over an existing installtion and it is right to backup your files and settings before doing that but lets look into the problem better before going that way. 

Exactly what happens when you try to boot? Please describe the boot process you see from start to finish. Also, boot to your cd and download and run this boot info script. Please post its results within code tags so that is easy to read. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Dna_Boy on 2011-08-17
well the boot starts normally, gets to the ubuntu logo and I see the bar going up to 1/3 and then a bunch of msg show up really fast, some with input/output error, and the rest with this: 
init: tty1 main process (1808) terminated with status 255
init: tty1 main process ended, respawning
init: tty1 respawnig too fast, stopped 

it does the some for tty2 tty3 tty5 tty6 etc. And then stops there. 

Meanwhile, I was googling and I found a ubuntu version, live cd with boot repair. So I just tried that and now... it's worst. Now it says, missing operating system :(

I think this boot repair killed my all options.. :(

---

### Post by Blasphemist on 2011-08-17
Hopefully you haven't killed anything but do try not to make things worse. Please do boot the cd, run the boot info script and post the results. Also, do fully describe the current situation.

---

### Post by Dna_Boy on 2011-08-18
I attached the file from that script you said to this post, I hope it helps. 

Meanwhile, I was trying to install XP in another disk so that I could try and read the disk on a windows environment, but before I did the check for errors using that new boot cd I downloaded and it turns out that the disk has problems. In fact, first only one of the disks was being detected with live cd, so I changed it to another SATA port and now both show up, and the one with the files I need, is the one with problems.  But apparently, I can't see the files with ubuntu live cd, it says that 350GB are occupied in that disk, which was right before the fail, but when I mount the drive, they don't show up, or I can't see them. 

At this point only thing I want is to recover those files.. If I connect the disk to a windows SO, will they show up using linux reader??

---

### Post by Blasphemist on 2011-08-19
You still need to provide more specifics for us to be very good at helping but I'll try. 

At boot, the pc BIOS looks at the first sectors of the first hard disk to hand off the boot process to. Changing the physical connections like you did may have changed which drive it tries to access for that hand off, or it may not have. 

Both Linux and Windows can see, read and act on ntfs or fat partitions if that is what houses the files you want to recover. I think you'll have more choices for recovery software possibilities using Linux but do as you want. GParted is a good Linux tool for resolving certain things such as disk structure issues. You'll likely have to look at testdisk and it's partner photorec for certain other recovery efforts. Those are commonly used tools but not your only options depending on the actual issue. Using these tools requires doing some learning depending on what needs done but that is because fortunately we don't experience this kind of thing often.

Here are some things I see from the results of the boot info script. The first hard disk has a linux boot loader installed to its master boot record. No boot loader seems to be installed on the second hard disk and a windows boot loader is installed to the third hard disk. Ext3 file system is shown for the first hard disk and that is right for older Ubuntu versions. The vfat file system for sdc is also OK but for both drives the actual boot files are not found. This is an issue.

Here are links to some resources you could use. You'll need to be very specific about what has been done already and exactly what happens now for us to help much more.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
[http://technet.microsoft.com/en-us/library/dd799232(WS.10).aspx#PartitionRules](http://technet.microsoft.com/en-us/library/dd799232(WS.10).aspx#PartitionRules)
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by srs5694 on 2011-08-19
The Boot Info Script output you posted screams "hardware fault" for your second disk /dev/sdb. You seemed to be beginning to understand that in post #7, but it's not clear which disk is which or whether you ran the Boot Info Script before or after juggling your disks around.

My recommendation is that you first track down the source of the hardware fault. Some things you can do include:


[list]
[*]Run a SMART utility on the disk. In Linux, smartctrl and GSmartControl are two such utilities. The Palimpsest Disk Utility also gives access to SMART data. Unfortunately, the data can be difficult to interpret, so you may need to peruse it and post back with questions. Most disk manufacturers also provide SMART utilities, but they usually run under Windows, or sometimes from DOS boot floppies.
[*]If the computer can't detect the disk at all, try changing cables and/or plugging the disk into a different disk port on the motherboard. It could be you've got a bad cable, a flaky port, or something along those lines.
[*]You could try to access the problem disk on another computer entirely. This might work if you've got some serious and fundamental hardware problem on the computer's motherboard, but it's a bit of a long shot.
[/list]


In any event, if you can get the disk to work reliably by swapping cables or whatnot, then that serves as the solution as well as a diagnostic measure. My concern, though, is that the disk may have gone bad internally, which will probably show up in a SMART diagnostic as the disk having a large number of bad sectors or some other serious problem. If that's the case, you might find it difficult or impossible to recover your data. Somebody on this forum might be able to provide suggestions once you post SMART details, or you might need to pay a data recovery specialist. You should prepare yourself for the possibility that you won't be able to recover anything, though. I hope it won't come to that, but it's a distinct possibility.

---

### Post by 123456789123456789123456 on 2011-08-19
If I understand this correctly you physically attached the drive to a different port on the motherboard?  If so, the drive may not be damaged at all but could be motherborad failure.  specifically hard drive controler failure.  possible solutions, get pci hard drive controller, replace motherboard.

try taking out disk, converting to usb by use of a sata/ide to usb converter cabel, boot from live cd, see if the disk works and responds correctly.

---

### Post by retchid on 2011-08-19
why does everyone scream hard disk failure

never had a hard disk fail yet (only in apple mac but that got stood on)

just bad sectors and boot sector problems all cured by reformat

TIP never use home for keeping docs on or anything for that matter (goes for windows as well)
just gets wiped - seperate partition or even better 2nd drive - and even that should be split into drive  2 partitions)

Still annoying though when you have to reformat and reinstall progs - I dont have patience to back up anything but then reinstalling usually improves system - sometimes you gotta break it to make it better

---

### Post by Dna_Boy on 2011-08-22
Ok, First of all, thank you all for the help and inputs. :) 
I know something about computers, I just don't know a lot about linux. :)

Second, as some of you already said, it is in fact hardware error, like I became to realize earlier. So I tried a different approach, _before I was able to read all this_. I took the disk with errors (several bad sectors) and connected it to a windows XP system I have in another PC, with a SATA-to-usb connector. I downloaded LINUX READER software and gave it a try. It works great, I was able to copy all the files from all the files I wanted, except a few that are unreadable, probably because of the sectors that don't work anymore. That software doesn't allow you to write in the disc, but lets you copy everything, and with that connector, is pretty fast. Good thinking 12345678... lol

After I copy and verify everything, I guess I'm gonna take that disk and throw it out the window. There are some files that are unrecoverable with software, but it still costs a bit to recover them in those professional data recovering enterprises. 

Thank you all again. Problem kinda solved :)

---

