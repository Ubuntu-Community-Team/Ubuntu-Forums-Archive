---
title: "Problem Starting Ubuntu on my PC"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by cubeofmoon on 2009-01-13
A few days ago, after hearing lots of good things about Ubuntu and Linux in general, I figured I'd give it a try. I installed it through Wubi so I could easily uninstall it if I didn't like it, and I am pretty sure the installation on that front went ok. The problem I am having is that when I try to boot Ubuntu through the OS selection screen that appears when I start my computer, I cannot use the OS. I see a what I think is a loading screen, with "Ubuntu" and a loading bar, but after that is done loading my screen goes black and displays this error:

"Out of Scan Range
44.6KHz/55Hz"

I tried uninstalling and reinstalling version 8.10 to see if that would help, but the same problem occurred.

System Specifications: (No idea what info you need so I'll supply more than is likely necessary :P)
2 Gb RAM
Windows Vista 32-Bit 
Processor: AMD Atholon 64 X2 Dual Processor 5000+ 2.6Ghz
Video Card: NVIDIA GeForce 6150SE nForce 430
Monitor: Sony SDM X52
Ubuntu Version: 8.10 I think?

Thank you for any help in advance. :)

---

### Post by 73ckn797 on 2009-01-13
The video resolution is out of range.

You may have to boot in recovery mode and select fixing xclient script, if I am not mistaken. That will allow a fix so you can boot into a default resolution. From there you can get the correct driver. If you are able to see the recommended driver, use that.

It will be a restricted driver for the video. Do not set resolution to max initially and see what happens. 

You will have to either set display for extra effects via System/Applications/Appearance. That will prompt you to use the video driver. If the driver is not listed you may want to run System/Administration/Update Manager.

There are probably other, better solutions. You may want to resubmit a new post with a more descriptive title such as: "Video resolution problem on boot up in 8.10".

---

### Post by Famicommander on 2009-01-13
After the system loads up? You may be able to get into the command and force it to boot VESA.

---

