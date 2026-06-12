---
title: "Erase a CD-RW via Command Line?"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Ahunt on 2010-12-08
This question is one that arose as part of a slightly more complex issue on [another thread]("http://ubuntuforums.org/showthread.php?p=10209045"). Since it is really a separate issue I started a new thread on it.

Is it possible to erase (or blank) a CD-RW from the command line? If so what is the command syntax?

Thank you for any assistance you can render.

---

### Post by hwychld on 2010-12-08
Should be possible using wodim

```
wodim dev=/dev/cdrom blank=fast
```Make sure you replace /dev/cdrom with whatever the proper device is on your system.

To write an ISO image

```
wodim dev=/dev/cdrom image.iso
```

---

### Post by sisco311 on 2010-12-08
To get the device name of the CD/DVD drive, run:
```
sudo lshw -class disk
```

and check out the community documentation:
[uhelp]community/CdDvd/Burning[/uhelp]
the ArchWiki pages are usually good:
[https://wiki.archlinux.org/index.php/CD_Burning](https://wiki.archlinux.org/index.php/CD_Burning)

---

### Post by Ahunt on 2010-12-08
Thank you for that reply!

I am using Lubuntu 10.10. I started off by trying:

```
$ wodim -scanbus
```

to get the identity of the CD drive and it returned:

```
The program 'wodim' is currently not installed.  You can install it by typing:
sudo apt-get install wodim
```

I thought all Ubuntu flavours had wodim, but perhaps Lubuntu doesn't? Is there any reason not to go ahead and install wodim?

---

### Post by sisco311 on 2010-12-08
> **Ahunt said:**
> Is there any reason not to go ahead and install wodim?

Nope, you can remove it if you don't need it anymore.

---

### Post by Ahunt on 2010-12-08
> **sisco311 said:**
> To get the device name of the CD/DVD drive, run:
```
sudo lshw -class disk
```

and check out the community documentation:
[uhelp]community/CdDvd/Burning[/uhelp]
the ArchWiki pages are usually good:
[https://wiki.archlinux.org/index.php/CD_Burning](https://wiki.archlinux.org/index.php/CD_Burning)

Thank you for that hint! As you can see I was going to try that as a first step, but using wodim!

I entered the command you suggested:

```
sudo lshw -class disk
```

and it returned a lot of info. Which CD drive ID do I use?

```
*-disk                  
       description: ATA Disk
       product: WDC WD1600AAJB-0
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCAV2U881476
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000ec423
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM GH22NP20
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/disk
       version: 2.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/disk
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
```

---

### Post by Ahunt on 2010-12-08
> **sisco311 said:**
> Nope, you can remove it if you don't need it anymore.

Not sure what you mean by "remove it". Wodim is not installed apparently. Is there another way to erase the CD from the command line then without wodim?

---

### Post by sisco311 on 2010-12-08
> **Ahunt said:**
> Not sure what you mean by "remove it". Wodim is not installed apparently. Is there another way to erase the CD from the command line then without wodim?

I mean, you can uninstall (remove) wodim.

You can use any *logical name* listed in the **-cdrom* stanza.

Usually /dev/sr0 (/dev/sr[0-9]) is the device name and all the others (/dev/cdrom, /dev/cdrw...) are just symlinks to it.

---

### Post by Ahunt on 2010-12-08
Okay thank you for the explanation on the nomenclature, so it sounds like hwychld's suggestion above of "/dev/cdrom" would work fine.

I am still not clear what you mean by "I mean, you can uninstall (remove) wodim." According to the command reply I got it is not currently installed. hwychld's suggestion was to use wodim to erase the CD-RW, so wouldn't I need to install wodim, rather than remove it?

I only ask because Lubuntu 10.10 uses XFburn as the default CD burner application and I wanted to make sure wodim wouldn't conflict with it.

---

### Post by sisco311 on 2010-12-08
> **Ahunt said:**
> Okay thank you for the explanation on the nomenclature, so it sounds like hwychld's suggestion above of "/dev/cdrom" would work fine.

Yes.

> **Ahunt said:**
> 
I am still not clear what you mean by "I mean, you can uninstall (remove) wodim." According to the command reply I got it is not currently installed. hwychld's suggestion was to use wodim to erase the CD-RW, so wouldn't I need to install wodim, rather than remove it?


You can install wodim and when you don't need it anymore you can uninstall it.

> **Ahunt said:**
> 
I only ask because Lubuntu 10.10 uses XFburn as the default CD burner application and I wanted to make sure wodim wouldn't conflict with it.

They don't; anyway the package manager takes care of conflicting packages. It will prompt you if a package conflicts with another.

---

### Post by Ahunt on 2010-12-08
Ah, okay I see, thank you for the clarification. 

In this case I will probably need it on an on-going basis. The [previously cited thread]("http://ubuntuforums.org/showthread.php?p=10209045") explains the underlying issue in more depth, but the short version is that XFburn for some reason will not erase a CD on Lubuntu 10.10 and neither will Brasero (tried it, it crashes) nor K3B ([outstanding bug]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/581926") on the issue), so I thought that a command line erase would be just easier.

I'll give it a try and report back here to let everyone know how that works out.

---

### Post by Ahunt on 2010-12-08
Okay wodim installed fine. I ran

```
wodim dev=/dev/cdrom blank=fast
```

and got 

```
$ wodim dev=/dev/cdrom blank=fast
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... giving up.
wodim: Device or resource busy. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```

I am going to have to read through the readme and see what it says. Any other suggestions are welcome in the meantime!

---

### Post by sisco311 on 2010-12-08
Try to unmont it first:
```
sudo umount /media/disk
```

---

### Post by anewguy on 2010-12-08
As per the other thread,  *PLEASE* also try creating the CD from the ISO with wodim also.  As I mentioned in the other thread, it will help us to know if the problem you are encountering still continues or not.  If not, we know that the problem lies higher up in Brasero.  I'm also surprised that wodim wasn't already installed - I thought Brasero used it to do what you are trying in the other thread.

Good luck, and let us know how it goes!  And please, beyond the CD-RW erase, please try to create the CD from the ISO using wodim as well.

Dave ;)

---

### Post by Ahunt on 2010-12-09
Okay, let me try that unmount first. I'll provide a full report here as soon as I sort it out!

For anewguy: Just to clarify - in a previous installation I had of Lubuntu 10.10 I had tried XFburn and when it wouldn't blank CD-RWs I tried installing Brasero (which works fine blanking on two Ubuntu 10.04 PCs I have) but it just crashed on Lubuntu. I also tried installing K3B, but it still has that outstanding bug and won't blank CD-RWs.

I then rebuilt the PC with some new hardware, including a new CD/DVD reader/writer and hard drive and then installed Lubuntu 10.10 from scratch on it. XFburn works fine, except it won't blank a CD-RW. Rather than try reinstalling Brasero and K3B again, which didn't work last time, I thought I would try to see if I could simply blank from the command line instead and then use XFburn to do the writing task. I thought since this is really a new question (how to blank from the command line) that I would start a new thread, but ensure both threads are linked to each other.

Because when I tried to call up wodim from the command line it indicated it wasn't installed I have to assume that XFburn uses some other backend to burn CDs than Brasero does, but perhaps someone more knowledgeable that I am can explain that.

I should have this testing done shortly and will post results back here as soon as I can. Thank you all for your help and patience on this!

---

### Post by Ahunt on 2010-12-09
Okay things seem to be working. Here is what I ran and the results:

```
adam@d:~$ sudo umount /media/disk
[sudo] password for adam: 
adam@d:~$ wodim dev=/dev/cdrom blank=fast
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RAM GH22NP20'
Revision       : '2.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real BLANK mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
adam@d:~$
```

Even though the terminal returned "wodim: Operation not permitted", the CD was successfully blanked using this method.

Next I tried writing an ISO to the CD using wodim:


```
adam@d:~$ wodim dev=/dev/cdrom ~/ISOs/lubuntu-10.10.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RAM GH22NP20'
Revision       : '2.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Track 01: Total bytes read/written: 572012544/572012544 (279303 sectors).
adam@d:~$ 
```

I then ran the resulting CD-RW though the internal "Check disk for defects" check and it checked with no errors found.

On a hunch I then used 

```
sudo umount /media/disk
```

to unmount the CD-RW and then opened XFburn. Unlike in previous attempts to use XFburn to blank a disk, described in [the other thread on that problem]("http://ubuntuforums.org/showthread.php?p=10209045"), this did not immediately cause an XFburn crash and I was able to blank the disk using XFburn successfully. It looks like XFburn has one small bug in it - it should unmount the CD when it opens and it doesn't. Otherwise XFburn works fine.

I will add a report to that other thread as well closing both these issues.

I want to thank everyone who contributed here. As usual the Ubuntu Forums are an amazing source of information and everyone here is amazingly patient and polite with those of us who are still learning; it really does help make Ubuntu better!

---

### Post by Ahunt on 2010-12-09
Just for the record, [XFburn]("http://www.xfce.org/projects/xfburn"), which is the default CD burning application in XFCE and LXDE, is based on [libburnia libraries]("http://www.libburnia-project.org/"), instead of using wodim.

---

### Post by anewguy on 2010-12-09
Were you able to successfully boot the ISO disk?

Thank you SO MUCH for testing the ISO burning.  This would seem to indicate the problem IS in Brasero.  I really appreciate knowing that!

Dave ;)

---

### Post by Ahunt on 2010-12-10
Sorry I seem to be confusing everyone with my multiple threads about different PCs I am troubleshooting all at the same time.

Just to avoid confusion: the PC in this thread is a Dell Dimension 2400 with a combo CD/DVD reader/writer running Lubuntu 10.10 and currently only has Xfburn (default) and wodim (command line) installed for CD burning.

Prior to a reformat, as a result of installing a new bigger hard drive, this PC also had Lubuntu 10.10 on it with XFburn, K3B and Brasero. K3B worked okay but would not blank a CD-RW as per [the bug]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/581926") filed against it, Brasero just crashed and wouldn't do anything and Xfburn wouldn't blank a CD as it couldn't unmount the CD.

In the current installation wodim from the command line works fine and can both blank CD-RWs and burn ISOs that test serviceable. For Xfburn to blank a CD-RW I have to run:

```
sudo umount /media/disk
```

before opening Xfburn and then it works fine after that.

Does that answer your questions?

---

