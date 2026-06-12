---
title: "CD Drive not recognized?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by McNA5TY on 2009-06-04
Hi all I just installed Xubuntu (xfce 4.6) on a dell dimension 2300.  Everything seems to work fine except I can't find my CD-R Drive. When I put a CD in the drive, I go to Places and nothing shows up.

I've been searching forums all day and only came up with this command to type in terminal.

wodim -checkdrive

This is what came up.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-ROM DVD-115 '
Revision       : '1.14'
Device seems to be: Generic mmc2 DVD-ROM.
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

Now this is my DVD-Rom drive (obviously), but I installed Xubuntu from my CD-R drive which is my primary IDE in my BIOS (AFAIK).  Basically I need to be able to burn CD's with this system, so taking out the DVD-Rom wouldn't be a problem if that would fix my issue.

Any help is greatly appreciated.

---

### Post by HermanAB on 2009-06-05
I can feel your pain...
;)

The installation system uses a different kernel and device driver than the installed system, which explains the difference.  The problem is what to do about it.

I have found in the past that the ACPI system can interfere with CD drivers.  So if you are NOT running a laptop, then you can try to turn ACPI off at boot and see whether the CD starts to work.  Do not turn ACPI off on a laptop, because it will overheat.

Hope that helps!

---

