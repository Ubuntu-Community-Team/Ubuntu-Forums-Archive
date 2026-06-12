---
title: "Boot-up hassles"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by jermza on 2011-01-23
Not sure if this is an Ubuntu problem, but anyway.

When I shut down Ubuntu, I had forgotten to remove a flash drive.  When I booted up my PC, the black screen prompted me to change boot-up drives (or something like that).  I remembered that I'd left in a flash drive, so I pulled it out and pushed the reset button.

Problem is that the boot-up screen prompt appeared again, so I reset again, and the same thing happened again.

I'm not a techie, so I wasn't sure what to do, so I pushed the button combo that took me to the bios settings (is that the right phrase?).  I then found an option to change the boot-up drive and selected my primary hard drive.

That worked.

However, whenever I boot up my PC, I get the same screen and have to change the drive.

What am I doing wrong and how do I fix this?

---

### Post by Sleven7 on 2011-01-24
The bootup screen that you are referring to, does it give you the choice between different operating systems?  i.e.

Ubuntu on sda?
Windows on sda1?

Where you have to chose what system to boot?

If not describe the screen and the choices.

---

### Post by jermza on 2011-01-24
No, I only run Ubuntu.

However, I managed to fix it.  I pressed Delete and managed to change the hard drives and their priorities.

What confuses me is why this happened after I forgot to unplug a flash drive.  (The boot-up swapped around the boot-up drives, which is why I thought it might be related to Ubuntu.)

---

### Post by Bucky Ball on 2011-01-24
When you pulled out the USB drive it would have probably left it open meaning that the system didn't close it therefore thought it was still there. Possibly ...

---

