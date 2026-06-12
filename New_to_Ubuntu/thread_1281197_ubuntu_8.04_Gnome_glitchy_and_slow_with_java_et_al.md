---
title: "ubuntu 8.04 Gnome glitchy and slow with java et al"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by lupulin on 2009-10-03
I just switched to Ubuntu a couple of weeks ago with no linux background so I'm a total newb. Forgive me if this sort of thing has been discussed. My version (8.04) seems to be very slow and/or glitchy with java applications (pandora especially) and has even had some problems playing audio from CD's. I'm wondering if these sort of problems might be fixed by a simple upgrade. Also it sounds like the newest version of ubuntu is coming out soon. should I wait for this, or just get something stable now (if this is my issue)?

If this isn't my best solution I'd love to hear any input.

thanks.

---

### Post by starcannon on 2009-10-03
Did you run the **Hardware Drivers** utility yet? 
If no, it is located under:
System>Administration>Hardware Drivers
enable the items listed there, give the password you log in with, wait for download and install, reboot if directed.
In case there are problems, before reboot please attach the following file, it can be obtained by:
Applications>Accessories>Terminal
type the following into the Terminal:
```
sudo lshw > ~/Desktop/hardware.doc
```
Please attach the hardware.doc file that will be located on your desktop to this thread.

GL and HF

---

### Post by lupulin on 2009-10-03
Thanks.
When I run the Hardware Drivers utility it says "no proprietary drivers in use"

I attached the hardware.doc as well.

---

### Post by Paddy Landau on 2009-10-03
> **lupulin said:**
> Also it sounds like the newest version of ubuntu is coming out soon. should I wait for this, or just get something stable now (if this is my issue)?
Wait for the next stable release, which will be (probably) at the end of this month.

---

