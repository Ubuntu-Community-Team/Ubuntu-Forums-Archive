---
title: "Download and install Microtek scanner driver"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by harry003 on 2010-04-04
How and from where can I download and install a driver for a Microtek 3840 scanner?

I am a newbie and all the info says something to the effect that "it should just automatically load and work" which of course is not likely.

Perhaps I am asking the question wrongly, coming from the Windows world, loading and installing a driver is what you do to make a piece of hardware work, whatever the Ubuntu equivalent of that process is what I am looking for.

Specifically I have a Microtek 3840 that connects via USB.

I am running Lucid in a Sun VirtualBox under XP.

Asus M2N-E, Athlon 64x2, 4GB ram, 8600GTS graphics, 500GB SATA, ethernet DSL

---

### Post by HereInOz on 2010-04-04
To my knowledge, Microtek has not released Linux drivers for their scanners, and up to now, no one has written one.  I have a Microtek Scanmaster 4600 and I have to run it in a WinXP virtual machine on my Ubuntu box to get it working.

This is a bit sad, as it really slows down the scanner speed, but it is the best I can do.  Also, I can't get it working in Windows 7 either, but then I haven't tried real hard.

---

### Post by Bachstelze on 2010-04-04
The 3840 is supported by SANE, so yes, it should work automatically.

---

### Post by harry003 on 2010-04-04
I installed SANE via System, and it seemed to add Gimp to my programs, but failed to address the scanner issue.

Does it need to be instructed to look for the scanner?

Thank you!

---

### Post by anewguy on 2010-04-04
And, as per my reply to your 2nd post about this same problem, VirtualBox doesn't support USB devices unless you download and install the non-open source (but still free) version from Sun (or maybe they call themselves Oracle now).  Once you have that, then you need to create filters for the devices to work in VirtualBox.

Dave ;)

---

### Post by Bachstelze on 2010-04-04
No. When you start a scanning app like XSane, it should use your scanner automatically since it's the only scanner attached.

---

### Post by harry003 on 2010-04-04
Thank you. I appear to be moving in the right direction, but no happiness yet.

First, I have been using the latest VirtualBox which I downloaded directly from Sun/Oracle just about 3 days ago.

I installed SANE, then realized that I also needed XSane, so I downloaded it as well. Still, it looks for a scanner but tells me that there is no scanner connected.

Is this related to the USB problem, and what is a "filter" I cannot seem to find that anywhere? 

My Ubuntu book index lists "filter" only as something having to do with photo editing.

Referring to a book is preferable to pestering other people. Is there a comprehensive and understandable Ubuntu reference book out there?

---

### Post by 3rdalbum on 2010-04-04
> **harry003 said:**
> 

My Ubuntu book index lists "filter" only as something having to do with photo editing.

Referring to a book is preferable to pestering other people. Is there a comprehensive and understandable Ubuntu reference book out there?

The Virtualbox documentation will tell you how to get USB devices to be seen within the guest operating system. It's available under "End-user docs" on the Virtualbox website.

Note: Making a USB device available in the guest OS will temporarily stop it from being used in the host OS, so don't try to add your keyboard and mouse to the guest (they are already handled anyway).

---

### Post by anewguy on 2010-04-05
> **harry003 said:**
> Thank you. I appear to be moving in the right direction, but no happiness yet.

First, I have been using the latest VirtualBox which I downloaded directly from Sun/Oracle just about 3 days ago.

I installed SANE, then realized that I also needed XSane, so I downloaded it as well. Still, it looks for a scanner but tells me that there is no scanner connected.

Is this related to the USB problem, and what is a "filter" I cannot seem to find that anywhere? 

My Ubuntu book index lists "filter" only as something having to do with photo editing.

Referring to a book is preferable to pestering other people. Is there a comprehensive and understandable Ubuntu reference book out there?

Again, make sure the VirtualBox you downloaded is not the open source version (not sure, but I think the term PUEL came in there somewhere).  Sun used to still have both version available on their site, so just because you downloaded the newest doesn't mean it is neccessarily the version with USB support.

Dave ;)

---

