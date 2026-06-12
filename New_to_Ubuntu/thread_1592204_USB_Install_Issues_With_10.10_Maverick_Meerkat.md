---
title: "USB Install Issues With 10.10 Maverick Meerkat"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by spikoley on 2010-10-10
I am trying to install Maverick Meerkat by USB.

When I use the USB Startup Disk Creator (from Karmic) I run into a known bug.

```
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu4) built-in shell (ash)
Enter 'help for a list of built-in command

```

The work around for that bug is to use UNetbootin.  When I do that I get the error message:

```
Unknown keyword in configuration file.
```

Any ideas on how to fix this?


-----------------------------
The solution is in [post #9]("http://ubuntuforums.org/showpost.php?p=9952171&postcount=9")

---

### Post by drpjkurian on 2010-10-10
Hi
Try this [link]("http://www.khattam.info/solved-syslinux-unknown-keyword-in-configuration-file-2010-09-01.html"). It may help you..

---

### Post by trentscott on 2010-10-10
Had the same issue here using a SanDisk Cruzer USB drive -- will use Unetbootin and report on success/failure.

---

### Post by spikoley on 2010-10-10
I ended up burning it to CD.  If somebody can confirm a solution I will mark this thread as resolved.

---

### Post by trentscott on 2010-10-10
I tried using Unetbootin and received a config error message. Unfortunately, I have a netbook (unable to use CD) and have NOT been able to successfully install 10.10 yet.

Any other solutions?

---

### Post by Hippytaff on 2010-10-10
me too

---

### Post by JackNocturne on 2010-10-10
> **spikoley said:**
> I ended up burning it to CD.  If somebody can confirm a solution I will mark this thread as resolved.


Use **USB-**creator( sometimes called Start-up disk creator)

and proceed with

[http://ubuntuforums.org/showthread.php?p=9948530#post9948530](http://ubuntuforums.org/showthread.php?p=9948530#post9948530)

---

### Post by trentscott on 2010-10-10
Finally we've fixed it! Here's the solution:

[http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/](http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/)

(Credits to JackNocturne)

---

### Post by mabtifro2 on 2010-10-11
> **trentscott said:**
> Finally we've fixed it! Here's the solution:

[http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/](http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/)

(Credits to JackNocturne)

just for the record, the instructions for the above link are as follows:

> 
Using GParted to Format a USB Stick »
Fixing USB Install Issues with Ubuntu 10.10 Maverick Meerkat
Published on October 7, 2010 in Ubuntu. 2 Comments Tags: bootlogo, fix, gfxboot, maverick meerkat, ubuntu, ui, unknown keyword in configuration file.

This morning, I attempted to install Ubuntu 10.10 Maverick Meerkat from a USB drive but received an error message to my disdain. After using the USB Startup Disk Creator to create a bootable USB installer, I rebooted only to be confronted with the following fatal error message: “Unknown keyword in configuration file”. Here’s a fix for it (thanks to JackNocturne):

NOTE: This has only been tested and reported as working on the 32-bit version of Ubuntu 10.10. Compatibility issues have been reported with the 64-bit version.

   1. Using the USB Startup Disk Creator, make a bootable USB disk with the latest Ubuntu 10.10 .ISO.
   2. Once the process is complete, browse to the root directory of the USB disk, click on the /syslinux folder, and open the file entitled syslinux.cfg.
   3. Using a text/code editor, find the line:
      ui gfxboot bootlogo
   4. Change it to:
      gfxboot bootlogo
   5. Save the file and reboot to test — it should work now.


---

### Post by jaycee23 on 2010-10-11
Thanks for this solution

---

### Post by spikoley on 2010-10-11
I marked this thread as Solved since it looks like trentscott solution worked.

---

### Post by bcfrisbee on 2010-10-13
I spent 3 days searching the internets for a nOOb solution- here it is:

**Just type "help" on the BOOT prompt, and when you get the help menu, just hit enter. The system will now boot!**

I couldn't believe how simple this was!

---

### Post by trentscott on 2010-10-13
> **bcfrisbee said:**
> I spent 3 days searching the internets for a nOOb solution- here it is:

**Just type "help" on the BOOT prompt, and when you get the help menu, just hit enter. The system will now boot!**

I couldn't believe how simple this was!

:lolflag:

---

### Post by catrincm on 2010-12-26
I had the same problem (not recognising "gfxboot") whilst booting jolicloud from a netbook. This solution also worked for me, although I'd like to know why...

edit: although this seemed to work (it allowed me to get jolicloud up) the disc was still corrupted in that it came up with errors when I tried to install it. Problem was solved by using the disc creator from jolicloud instead of ubuntu's startup disc creator.

> **bcfrisbee said:**
> I spent 3 days searching the internets for a nOOb solution- here it is:

**Just type "help" on the BOOT prompt, and when you get the help menu, just hit enter. The system will now boot!**

I couldn't believe how simple this was!

---

### Post by jimmy the saint on 2011-01-01
And 3 months later Canonical can't fix a critical error in their installation media.

Come on.

---

### Post by kulkarni.ankur on 2011-01-02
I am unable to edit the syslinux.cfg file. What editor did you use? I got bizarre looking symbols when I tried gedit. Same with vim, ooffice. Someone please help!

---

### Post by spikoley on 2011-01-04
> **kulkarni.ankur said:**
> I am unable to edit the syslinux.cfg file. What editor did you use? I got bizarre looking symbols when I tried gedit. Same with vim, ooffice. Someone please help!

I think I used Nano.

---

### Post by richardh9936 on 2011-01-15
... January 2011 - still the same issues...

---

