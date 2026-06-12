---
title: "New User: Lots of Message Errors and no Pendrive Installation"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by SlowDemiseOfWindows on 2011-01-22
Hi all,

So, I'm trying to install Ubuntu on my new Acer Netbook. The specs are:
Aspire One D255
Intel Atom N450 Processor
Windows 7 OS

Here's what's happened:
I downloaded both the pendrive formatter and the Ubuntu Desktop 10.10 itself. I checked the box to reformat the pendrive with installation, but this didn't happen. Ubuntu does register as being on the drive now. When I click on Wubi, I get the prompt to run, but I get the error message "There is no disk in the drive. Please insert a disk into the drive /Device/Harddisk1/DR4." 

Simultaneously though, the prompt screen for installation appears with the options, "demo and full installation," "Install inside Windows," and "Learn More."  I click on the first and tell it I'll reboot later, and again, nothing happens.

I tried to boot manually going in through the Bios Screen and changed the order of the drives, putting the USB HDD first. Rather than Ubuntu booting, I get in the command screen the error message 

"Boot error message: SYSLINUX 4.02 2010-07-21 EDD Copyright 1994-2010 H. Peter Anvin et al
Could not find kernel image: vesamenu.c32"

I've done everything I'm supposed to do here, and it's still not working. Help!

Thanks much!

---

### Post by andymorton on 2011-01-22
> **SlowDemiseOfWindows said:**
> Hi all,

So, I'm trying to install Ubuntu on my new Acer Netbook. The specs are:
Aspire One D255
Intel Atom N450 Processor
Windows 7 OS

Here's what's happened:
I downloaded both the pendrive formatter and the Ubuntu Desktop 10.10 itself. I checked the box to reformat the pendrive with installation, but this didn't happen. Ubuntu does register as being on the drive now. When I click on Wubi, I get the prompt to run, but I get the error message "There is no disk in the drive. Please insert a disk into the drive /Device/Harddisk1/DR4." 

Simultaneously though, the prompt screen for installation appears with the options, "demo and full installation," "Install inside Windows," and "Learn More."  I click on the first and tell it I'll reboot later, and again, nothing happens.

I tried to boot manually going in through the Bios Screen and changed the order of the drives, putting the USB HDD first. Rather than Ubuntu booting, I get in the command screen the error message 

"Boot error message: SYSLINUX 4.02 2010-07-21 EDD Copyright 1994-2010 H. Peter Anvin et al
Could not find kernel image: vesamenu.c32"

I've done everything I'm supposed to do here, and it's still not working. Help!

Thanks much!

It might be best to burn Ubuntu to the pendrive using Unetbootin.[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

andy

---

### Post by SlowDemiseOfWindows on 2011-01-23
Thanks Andy,

Am trying that now. Any chance that the MacAfee anti-virus software that came loaded on my netbook might be interfering? Just thought of that now.

Anna

---

### Post by SlowDemiseOfWindows on 2011-01-23
Hi again,

You know, I have to say, Ubuntu has really given me a chance to work on developing more patience...

Still not working.

Trying to install to the main drive, forget the flash drive, I get this error message. 

Unetbootin - Universal Netboot Installer - [http://unetbootin.sorceforge.net](http://unetbootin.sorceforge.net) has stopped working 

"sevnz.exe No Disk

There is no disk in the drive. Please insert a disk into drive /Device/Darddisk2/DR2"

This is the more complete detail 

Problem signature:
  Problem Event Name:    APPCRASH
  Application Name:    unetbootin-windows-494(2).exe
  Application Version:    1.1.1.1
  Application Timestamp:    4cb260ec
  Fault Module Name:    unetbootin-windows-494(2).exe
  Fault Module Version:    1.1.1.1
  Fault Module Timestamp:    4cb260ec
  Exception Code:    c0000005
  Exception Offset:    008bca91
  OS Version:    6.1.7600.2.0.0.768.11
  Locale ID:    1033
  Additional Information 1:    0a9e
  Additional Information 2:    0a9e372d3b4ad19135b953a78882e789
  Additional Information 3:    0a9e
  Additional Information 4:    0a9e372d3b4ad19135b953a78882e789

Let's keep trying!

Anna

---

### Post by SlowDemiseOfWindows on 2011-01-23
Success!!! Finally!

Now, if someone could help me get my virgin mobile wireless to work with Ubuntu...

Anna

---

