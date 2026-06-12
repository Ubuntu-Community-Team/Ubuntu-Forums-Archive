---
title: "Ubuntu Floppy Drive"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by createdcreature on 2011-05-31
I have a 3.5in Floppy drive with Ubuntu 11.04 Natty Narwhal, but when I put a floppy disk into the drive and click on the drive in 'Computer' it says 'Unable to mount location, no media in the drive'. The fdformat command does not work either. I have tested over 7 different floppy disks, each formatted as FAT, MS-DOS, with no partitions, so it is not a problem with the disks. Is it the drive or Ubuntu? The computer is a 2002-era Packard Bell.

---

### Post by seawolf167 on 2011-05-31
Do any of the different floppy disks you mentioned work in your drive on your Ubuntu installation? Do said disks work on a different computer (say Windows)?

Do you have the floppy drive enabled or turned on in BIOS?

---

### Post by grahammechanical on 2011-05-31
I get the same message but I am not surprised because I do not have a floppy drive installed. Does the LED on the floppy drive light up to show that the drive is being accessed? Is the drive properly connected? is it possible to disable the floppy drive in the BIOS? Has this been done in the past?

Just some ideas that I would examine if I had this problem.

Regards.

---

### Post by coffeecat on 2011-05-31
> **Robert Moyse said:**
> Is it the drive or Ubuntu?

I hate to say it, but it's probably Ubuntu. There's an unresolved bug concerning floppies that's being hanging around for far too long. I haven't checked in Natty yet, but I wouldn't be surprised if this bug is still unfixed and what you are seeing.

Try this. Put a floppy disc in the drive, open a terminal, and:

```
udisks --mount /dev/fd0
```I'm at a machine with no floppy drive at the moment, but when I get a chance later I'll boot up Natty on a machine with one and check to see if this is still working in Natty.

**EDIT**: Yes. That code still works in Natty.

@Robert Moyse, in case you were not aware of this, you need to use floppies slightly differently in Linux. When you drag and drop files to the floppy file manager window, they may not be written immediately, but remain in cache memory. Therefore, before you physically remove the disc, right-click on the desktop icon to unmount it. Pending writes will then be made after which you can safely remove the disc.

---

### Post by jerrrys on 2011-05-31
more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=floppy+drive+natty+11.04&as_qdr=all&sa=Google+Search&lang=en#896](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=floppy+drive+natty+11.04&as_qdr=all&sa=Google+Search&lang=en#896)

---

### Post by createdcreature on 2011-06-04
Thanks for the udisks tip, coffeecat! It is working fine now!

---

### Post by Tippo1 on 2011-07-27
[COLOR=Black]The udisk command worked for me also but just in that one instant case.  
I put another floppy in and tried to read it and got the same garbage as 
before.  "Can't mount disk,  No media detected".  I think I'll simply leave 
the floppy drive out of this computer.  Too much drama  :-)[/COLOR]

---

### Post by createdcreature on 2011-07-28
Nobody uses them nowadays, so it is not a very important bug, like that one with the garbled window crashing the X window system when you use multiple monitors.

---

### Post by stallinux on 2011-09-13
> **Robert Moyse said:**
> Nobody uses them nowadays, so it is not a very important bug, like that one with the garbled window crashing the X window system when you use multiple monitors.

Sorry. Tend to disagree.
[http://en.wikipedia.org/wiki/Floppy_disk#Current_use](http://en.wikipedia.org/wiki/Floppy_disk#Current_use)

Yes, it is no longer mainstream. But who wants mainstream should stay with that other operating system that I will not mention here by name. I really need floppies and for me it is very strange that that support has been stopped. It was working perfectly before on all the machines I have. Now, on all it fails. Not a problem with hardware, or missing disk, or bad disk. It is that somebody messed with the software in Ubuntu. Now: Put it back! And write 1000 times on a piece of paper "I will not mess up the system"! :-)

I also tried
[COLOR=Sienna] udisks --mount /dev/fd0[/COLOR]
as suggested on these pages. But this also fails:
[COLOR=Sienna]"Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: I could not determine the filesystem type, and none was specified"
[/COLOR] 
[SOLVED] --> [UNSOLVED]

---

### Post by cjv8888 on 2011-09-13
Not sure about Natty, but this is what I do to make floppy work in Lucid.

```
To summarize, reading (and writing) a floppy disk in Lucid Lynx (10.04) requires three steps:

1. Allow yourself to use the floppy by going to System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

2. Use the old version of udisks () by going to System->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, click on Package->Force Version, and select the 1.0.1-1build1 version (which is the old version). Then click on apply to finish the installation.

3. Remember to unclick udisks whenever Update Manager wants to install new updates, or you'll get the new version and floppy disks won't work anymore!

After the old udisks is installed (and the machine is rebooted), when you insert a floppy a cute little icon comes up on the desktop and in Nautilus (and on Disk Mounter if you have that installed). Left clicking on the icon and select Mount Floppy Disk will put an icon in Nautilus, and then you read, write, and format the floppy just like any other drive.
```

---

### Post by coffeecat on 2011-09-13
This thread is marked solved because it is solved for the OP. Only the OP and staff can tag or untag a thread as solved.

@stallinux, since the udisks command works seems to work for most people, I suggest you start your own support thread. This is more likely to be productive of help for you. 

Thread closed.

---

