---
title: "Can't use partitioner--no disks shown!"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by mount_evans on 2009-01-26
I am trying to install the 64-bit version of Ubuntu 8.10, dual-boot style, on a blank 500GB secondary drive that is intended just for Linux.

I can get past the (initramfs) prompt by selecting an option earlier to use a driver disk during install--so now I am prompted to put the driver disc in the primary drive in place of the Ubuntu CD, and then replace the Ubuntu CD.  This gets me as far as the Partitioner--Yay!  But now I am stalled there.  There is nothing "clickable" on the partitioner screen, except "Next", "Back", and "Quit".  All the options I would need to actually create a partition are greyed out.  No disks and none of the existing partitions are listed.  Isn't the partitioner supposed to load information about the existing disks?  I tried waiting overnight, and nothing changed.  

I doubt the drives are faulty; the big one is running Windows XP just fine, and the 500GB one has never been formatted, was installed specifically for Ubuntu, and is brand new.

I have looked at the official instructions for installing Ubuntu, and they just assume that the partitioner is working--they don't give any advice on what to do if it isn't.

---

### Post by mount_evans on 2009-01-26
Sorry--forgot to mention, both drives are made by Seagate and are SATA.  The big one is 1.5TB, is formatted NTFS, and is partitioned into a 300GB partition for Windows XP, with the rest of it available for the accumulation of Stuff.  The 500GB drive has never been used for anything.  The motherboard is XFX 8200 GeForce.

---

### Post by caljohnsmith on 2009-01-26
Colorado, huh? That's where I grew up. :) How about opening a terminal (Applications > Accessories > Terminal) and please post:
```
sudo fdisk -lu
sudo lshw -C disk
```

---

### Post by mount_evans on 2009-01-26
> **caljohnsmith said:**
> Colorado, huh? That's where I grew up. :) How about opening a terminal (Applications > Accessories > Terminal) and please post:
```
sudo fdisk -lu
sudo lshw -C disk
```

I'll try that when I get home again, but consider this:  In order to do that, I have to have Ubuntu running.  To get Ubuntu running, I have to boot off of the CD, ignoring the hard disc drives.  Will the commands you suggest behave as expected when there are no hard drives mounted?

---

### Post by caljohnsmith on 2009-01-26
> **mount_evans said:**
> I'll try that when I get home again, but consider this:  In order to do that, I have to have Ubuntu running.  To get Ubuntu running, I have to boot off of the CD, ignoring the hard disc drives.  Will the commands you suggest behave as expected when there are no hard drives mounted?
Yes, you can run those commands from the Live CD and you should be fine. Even though your partitions won't be mounted yet, those commands should show the drives/partitions available.

---

### Post by mount_evans on 2009-01-30
> **caljohnsmith said:**
> Colorado, huh? That's where I grew up. :) How about opening a terminal (Applications > Accessories > Terminal) and please post:
```
sudo fdisk -lu
sudo lshw -C disk
```

I get a description of the two CD/DVD drives; nothing about me hard disks.

---

### Post by mount_evans on 2009-01-30
My motherboard is an XFX 8200 GeForce.  My hard drives are both Seagate Barracudas.  My SATA controler has three different modes:  RAID, SATA, and AHCI.  SATA is the default, and I have left it there.  There is no IDE option for the SATA controler.  On a lark, I tried choosing AHCI, with the option to have it change the AHCI DID for Linux; it didn't help.

Here is the rundown on what happens if I try to install with a couple different boot CDs:

First of all, no matter which CD, there is a message telling me to enable something called an IOMMU.  Anyone know that that is?

Ubuntu 8.10 AMD 64-bit CD:
I can use F4 to specify that I have a driver disc.  When I install, I am prompted for the driver disc, and I get as far as the partitioner, but it cannot see any of my drives.  Every possible action is greyed out.  The only "clickable" items are "Next"," Back", and "Quit".  I can run Ubuntu off of the CD, though.

Ubuntu 8.10 AMD 64-bit Alternate CD:
F4 does not give me the chance to mention a driver disc.  I cannot find an option like that anywhere else, either.  When I install, it complains about my USB hubs not being there or something like that--shame I couldn't make it look at the driver CD.  When it gets to the "Disk Detection" stage, it can't detect any disks.  It gives me a list of driver names to choose from, and I have no idea which one might apply to my Seagate Barracuda drives.  I choose "none of the above", and it give me the chance to insert a floppy.  Not a CD, it has to be a *floppy*.  I inserted my CD anyway, and it tried to read the floppy drive.  Anyway, I never did get it to recognize any disks and I am stuck at essentially the same stage as with the non-Alternate disc.

So, what do I do next?

---

### Post by Branimir on 2009-01-30
I don;t know what is SATA mode but ubuntu works well with AHCI
(native sata) mode.

Greetsa, Branimir.

---

### Post by PmDematagoda on 2009-01-30
When the Ubuntu live CD has started up and you reach the desktop, what is the output of:-
```
fdisk -l
```

---

### Post by mount_evans on 2009-01-30
> **caljohnsmith said:**
> Colorado, huh? That's where I grew up. :) How about opening a terminal (Applications > Accessories > Terminal) and please post:
```
sudo fdisk -lu
sudo lshw -C disk
```

Sorry, here is exactly what resulted:
```

ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo lshw -C disk
  *-cdrom:0               
       description: DVD-RAM writer
       product: DVD RW AD-7190A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM SD-R1202
       vendor: TOSHIBA
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1026
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
ubuntu@ubuntu:~$ 

```
The first command produced nothing.  Was it supposed to?

---

### Post by caljohnsmith on 2009-01-30
You're definitely right, Ubuntu doesn't even see your HDDs for some reason (both commands should have shown a list of your drives). You said that Windows XP on your main HDD still boots OK? When you are in XP, does it see your 500 GB secondary drive? Can you give some more info about your computer, like how old is it, how much RAM does it have, how fast is the processor, have you ever upgraded the BIOS, and what type of HDDs do you have (IDE, SATA, or USB)? Also, how about going into your BIOS, and please let me know what your HDD related settings are, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc.

---

### Post by mount_evans on 2009-01-30
> **PmDematagoda said:**
> When the Ubuntu live CD has started up and you reach the desktop, what is the output of:-
```
fdisk -l
```
In an earlier version of this thread, I was asked something similar; I posted the complete output in a reply that I will attempt to link to here:

[http://ubuntuforums.org/showpost.php?p=6644736&postcount=7](http://ubuntuforums.org/showpost.php?p=6644736&postcount=7)

---

### Post by mount_evans on 2009-01-30
> **Branimir said:**
> I don;t know what is SATA mode but ubuntu works well with AHCI
(native sata) mode.

Greetsa, Branimir.

Sigh.  Someone on Usenet said the exact opposite, that I needed to put my SATA in IDE mode because AHCI wouldn't work with Ubuntu.  One of my options is AHCI with the option to "change the AHCI DID for Linux".  Any reason why I would want to change it for Linux?

---

### Post by mount_evans on 2009-01-30
> **caljohnsmith said:**
> You're definitely right, Ubuntu doesn't even see your HDDs for some reason (both commands should have shown a list of your drives). You said that Windows XP on your main HDD still boots OK? When you are in XP, does it see your 500 GB secondary drive? Can you give some more info about your computer, like how old is it, how much RAM does it have, how fast is the processor, have you ever upgraded the BIOS, and what type of HDDs do you have (IDE, SATA, or USB)? Also, how about going into your BIOS, and please let me know what your HDD related settings are, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc.

I have started a new thread where I start by listing a lot of that stuff:

[http://ubuntuforums.org/showthread.php?p=6644811#post6644811](http://ubuntuforums.org/showthread.php?p=6644811#post6644811)

I bought the motherboard earlier this month, ditto the Seagate drives.  I *wish* I had IDE emulation for the SATA ports; according to someone on usenet, that is the only SATA mode that Ubuntu supports.

---

### Post by PmDematagoda on 2009-01-30
At mount_evans:- Please try and keep posts which belong in one thread within that one thread without creating additional others because it just confuses people in the end without achieving any productive solution.

---

### Post by mikechant on 2009-01-30
Hmmm. Worth trying the RAID option (even though you're not using RAID). I had a problem a bit like this last year and Linux would only recognize the disk in RAID mode. However, if this works you might then find that Windows won't boot until you switch back to SATA mode. I used this as a workaround (as I hardly use Windows) until my problem was properly solved by a Kernel update - you might find if RAID mode works you can install updates which will fix your problem.

Also, it might be worth burning a Live CD for Ubuntu 9.4 Alpha and seeing if that can see your disk with fdisk, since 9.4 will have a newer Kernel.

---

### Post by mount_evans on 2009-01-31
> **mikechant said:**
> Hmmm. Worth trying the RAID option (even though you're not using RAID). I had a problem a bit like this last year and Linux would only recognize the disk in RAID mode. However, if this works you might then find that Windows won't boot until you switch back to SATA mode. I used this as a workaround (as I hardly use Windows) until my problem was properly solved by a Kernel update - you might find if RAID mode works you can install updates which will fix your problem.

Also, it might be worth burning a Live CD for Ubuntu 9.4 Alpha and seeing if that can see your disk with fdisk, since 9.4 will have a newer Kernel.

I have now tried RAID and AHCI mode; the results were unchanged.

---

### Post by mount_evans on 2009-02-01
> **mikechant said:**
> Also, it might be worth burning a Live CD for Ubuntu 9.4 Alpha and seeing if that can see your disk with fdisk, since 9.4 will have a newer Kernel.

Burned a 9.4 CD, and pretty much whatever I try to do, it just craps out on me with the CAPS LOCK and SCROLL LOCK lights flashing.  Can't check the disk for errors, since it craps out on me if I do that, too.:(

Someone told me that Linux doesn't work with Nvidia chipsets, period, end of story, forever and ever amen.  Is it that simple?

---

### Post by mikechant on 2009-02-03
*Someone told me that Linux doesn't work with Nvidia chipsets, period, end of story, forever and ever amen. Is it that simple?*

I came across this:
[http://www.linuxquestions.org/questions/linux-hardware-18/onboard-sata-drivers-for-xfx-geforce-8200-662850/](http://www.linuxquestions.org/questions/linux-hardware-18/onboard-sata-drivers-for-xfx-geforce-8200-662850/)

And they seem to have been sucessful with AHCI mode *and* kernel parameter
pci=nomsi

In general, googling for
"XFX 8200 GeForce linux" gave results which seem to indicate that at least some people are working OK with this.

---

### Post by mount_evans on 2009-02-04
:KS[COLOR="Magenta"][SIZE="6"][FONT="Arial Black"]Success![/FONT][/SIZE][/COLOR]:KS  
Though let me give a little background; someone recommended the following URL:

[http://unixzen.com/?articles/2008/10/05/ubuntu-8-10-on-the-xfx-8200.html](http://unixzen.com/?articles/2008/10/05/ubuntu-8-10-on-the-xfx-8200.html)

Some of his instructions just didn't seem to apply to my boot CD, though; for example, he says:

[LIST]
[*]Boot the Ubuntu CD / HDD
[*]Jump into the Ubuntu boot loader by pressing ESC just as it detects the CD
[*]Edit the first option by pressing e
[*]Cursor down to the second line (starts with kernel) and press e
[*]Go to the end of the line and remove the splash option replacing it with 'pci=nomsi'
[/LIST]

...but hitting ESC had no affect on my Ubuntu CD, it came up as always.  I did, however, find the word "splash" in the list of Boot Options that show when you hit F6.  So I replaced the word "splash" with "pci=nomsi", and hit return.  It booted Ubuntu, and saw my disks!  I partitioned, formatted, and installed.  I still couldn't successfully boot Ubuntu off of the hard drives, but once I added "pci=nomsi iommu=noaperture " to all of the lines in /boot/grub/menu.lst that begin with "kernel", everything worked.  To be clear, here is what my menu.lst file looks like:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		0b093473-7174-474c-bd50-b67c48c2d493
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0b093473-7174-474c-bd50-b67c48c2d493 ro quiet splash pci=nomsi iommu=noaperture 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		0b093473-7174-474c-bd50-b67c48c2d493
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0b093473-7174-474c-bd50-b67c48c2d493 ro  single pci=nomsi iommu=noaperture 
initrd		/boot/initrd.img-2.6.27-11-generic

```
etc.

I appended "pci=nomsi iommu=noaperture " to the end of the line instead of replacing the word "splash"; does it make a difference?  Does anyone know of anything else I need to correct or take care of before I get too settled in to this installation?  My previous experiment with Ubuntu had one thing going on that I didn't like:  Each time I would boot, it would run some sort of check on my Windows-formatted drives and create a bunch of new files as some sort of "repair" operation.  I would just as soon that Ubuntu treated those drives as something to look at but not touch until I say so.  Any ideas?

---

### Post by hotstovejer on 2009-02-13
My coworkers and I just got a bunch of these, and 32bit 8.10 installed just fine, per one of my co workers. My boss said that he had to flash the BIOS to get his 64bit 8.10 to work. I haven't built mine yet (Tonight!) so I am going to flash the bios before I get too into it. Try that and see what you get!

Thanks!

Jeremy

---

