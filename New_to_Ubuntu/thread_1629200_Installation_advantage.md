---
title: "Installation advantage?"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Mark Lee on 2010-11-23
To my knowledge there are two ways in which to install Ubuntu: a LiveCD/USB (aka a frugal install), or a full, standard installation (usually made to a hard disk). Is there a visual difference in the files that are loaded during installation? Also, is there an advantage to using one installation method over the other when preparing a dual-boot, removable medium such as an 8 gigabyte USB pen drive? Thanks
                  - Mark Lee

---

### Post by Hippytaff on 2010-11-23
In my opinion, it doesn't make much difference if you use a liveCD or LiveUSB to perform a 'real' install, but someone with much better knowledge than mine might prove me wrong :-)

You can use a liveUSB and make it persistence (ie change all updates, files etc) whereas this cannot be done with liveCD.

---

### Post by cariboo on 2010-11-23
I'm not sure exactly what you mean by frugal install. The two main methods of installing are via the Live CD, or the Alternate Install CD, the only huge difference is that one uses a gui and the other uses a text based installer.

If by frugal you mean only installing what you want, then you are probably wanting to use the the cli install using the alternate install cd then adding only the packages you want.

You can also use the[ mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), to do a net install, which also gives you the option to only install what you want.

---

### Post by Hippytaff on 2010-11-23
> You can also use the[ mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), to do a net install, which also gives you the option to only install what you want.

I didn't know that...that could be useful.

---

### Post by Sef on 2010-11-23
> To my knowledge there are two ways in which to install Ubuntu: a LiveCD/USB (aka a frugal install), or a full, standard installation (usually made to a hard disk). Is there a visual difference in the files that are loaded during installation? Also, is there an advantage to using one installation method over the other when preparing a dual-boot, removable medium such as an 8 gigabyte USB pen drive? 

Actually there are many, many ways to install Ubuntu. Sounds you want a minimal install. That way you can install exactly what you want or do you want another type of installing? In either case go to [Installation]("https://help.ubuntu.com/community/Installation").

---

### Post by candtalan on 2010-11-23
When you use a live CD or a live USB stick you would not usually expect to call it an 'install'. Live sessions are run in RAM and are not really a normal 'install'. However, they are full sessions, using the full capability of the OS.

An install is usually done by starting with a live session or live media. It is useful to first run live to verify that all facilities in the hardware are recognised - audio, video, etc.

A live media can be arranged to have 'persistence' in its media, that is, it can make use of more user space, still running in live session. Maybe updates can also be done, not sure here.

If the complete normal install is done into a removable media, then at issue is - the location of the boot files? There is no problem if the removable media is never removed (!) but if removed, then depending on how the booting arrangements were installed too, there could be some serious issues. For example, the main machine might not boot properly.
hth

---

### Post by C.S.Cameron on 2010-11-23
Is the question which method is better when installing to a 16GB flash drive, persistent or Full?

A persistent install is initially more compact, .7GB + persistence vs 2.7 GB. 
It can't be updated or upgraded.
The splash screen is usually ugly.
Proprietary drivers may not work.
Persistence is limited to 4GB using the common casper-rw file.
Persistence is limited only to the flash drive size if casper-rw and home-rw partitions are used.
Some tutorials and info from the forums may not work with a persistent install, A Full install is just like the real thing.

Both are good options depending on your requirements.

---

### Post by Mark Lee on 2010-11-24
Wow! You folks have given me a lot to consider. My understanding of a "frugal install" comes from this quote from the Unetbootin web site ([http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes]("http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes")):
[INDENT]“If you provide a LiveCD iso file, such as the Ubuntu desktop iso, to UNetbootin and use the hard disk install mode, the resulting install will NOT be a full, standard hard drive installation. Rather, you are simply booting into the live environment, the same way as if you had booted from a live CD or a live USB, except it's being loaded from your hard disk instead. This is often referred to as a "frugal install", as it doesn't install a dedicated bootloader and doesn't make a separate partition, but rather piggybacks off the existing OS's bootloader and installs the files for the live environment inside the existing partition.”[/INDENT]
I am not looking for the most minimal installation that I can achieve, but the most valid one that I can set up for the work that I intend to do. Specifically I want to load the current version of Fontforge and possibly Glyphtracer both of which will require fair amounts of memory. Using the USB Universal Installer I can install Ubuntu with the option to construct a four gig persistent memory at installation time. There is a tutorial for expanding the four gig to the full eight gig of pen drive. My concern is conducting a session that is entirely within RAM. My machine has a three gig RAM and that does sound like a lot, however, dealing with fonts and graphics the RAM could quickly fill. I currently work in a Windows environment which I need to keep, so the question becomes can I do the 'grunt' work (like scanning) in the Windows environment (taking advantage of it memory paging) and transport established work files to Ubuntu to take advantage of software like Glyphtracer? Clear as mud, right?
Mark Lee

---

### Post by C.S.Cameron on 2010-11-24
Persistent USB2 flash drive installs seem slower to me than HDD installs.
I don't think either type of Ubuntu install normally runs in RAM, (as does Puppy).
But you might try the following:

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by mastablasta on 2010-11-24
USBLive (or CD Live) - as mentioned everything runs from ram. So when you turn of the ocmputer everything that wasn't saved somewhere else is lost). all settings and such are also lost. USB (because you can write on it) can be made persistant. which means it will keep settings and programmes. however USB has limited write cycles. 
you can also do full install on USB (again USB has limited lifecycles - swap file could cause more usage of thse cycles?!).
 
For best install i suggest to use hard disk (or a part of it). you will need about 20 GB hard disk and it will take about 7 or 8GB. the rest you can use for programmes and files. if oyu already have windows on you can easilly create a dual boot system, where one OS won't affect the other.

---

### Post by Bartender on 2010-11-24
> **Mark Lee said:**
> I currently work in a Windows environment which I need to keep, so the question becomes can I do the 'grunt' work (like scanning) in the Windows environment (taking advantage of it memory paging) and transport established work files to Ubuntu to take advantage of software like Glyphtracer?Mark Lee

Just a few years ago I wouldnta suggested this, but anymore a guy can pick up a fairly capable P4 PC or equivalent AMD for free or at least dirt-cheap.  So you've got a Windows PC that you use for work, and it's set up the way you want.  And you need to hop back and forth between Windows and Linux.  I'd suggest scrounging up a spare PC.  Install Linux to it, then create a LAN.  Or USB sneakernet if not a real network.  

That way you haven't messed with your Windows PC, and you could hop back and forth between the OS'es.

---

### Post by Mark Lee on 2010-11-24
USB is indeed slower than HDD, however,  finances currently do not allow for a second computer.  I dismissed a dual boot hard drive or a Virtual Box installation because both interfere with CHKDSK operations. As a result I landed on installing to a pen drive.   Termintor14's **Making Ubuntu Insanely Fast using RAM** system may indeed be an answer for the USB lag-time problem, but I do not  have the Linux experience to avoid making a 'hash' of the entire installation. Working on a pen drive, however, I can begin again from scratch. Before I venture off to do that though, I was wondering if first  there would be any positive value of running a disk optimizer on the pen drive itself ?

---

