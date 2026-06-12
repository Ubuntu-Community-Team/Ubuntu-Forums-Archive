---
title: "Install x86 64bit from Live USB"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by pawap on 2011-03-03
Hi experts,

I'm trying to install the 64bit version of Ubuntu 10.10 on a laptop via Live USB, hardware specified below:

Make: Dell Latitude E6410
Processor: One Intel Core™ i7-640M (2.8Ghz, 4M cache,Dual Core)
Memory:  8GB(2x4GB)1333MHz DDR3 Dual Channel
Hard Drive: 500GB Serial ATA (7200RPM)
Screen: 14.1” WXGA+ LED Display (1440x900)

I've followed the simple instructions here:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Using Universal USB Installer on Windows 7 Professional 64bit to create my Live USB successfully. Upon boot, I'm presented with the boot menu. If I do nothing (and leave it to boot into Ubuntu) the screen goes black and I hear the Ubuntu 'log on jingle', but see nothing - the screen stays black. I've also tested this with the 32bit version of Ubuntu 10.10 and the same happens.

If you need any further relevant information please let me know. Thanks!

---

### Post by wojox on 2011-03-03
Try pressing F6 at the boot prompt and select "nomodeset"

---

### Post by pawap on 2011-03-03
Thanks for the very quick response. I think you've identified the problem correctly, but I'm still having trouble with what should be a simple solution.

Upon booting from the USB I'm presented with the following options:

Run Ubuntu from this USB
Install Ubuntu on a Hard Disk
Test Memory
Boot from first hard disk
Advanced options 
Help

Pressing F6 on either of the first 2 just results in a system beep. Am I doing something incorrectly?

---

### Post by pawap on 2011-03-03
Okay fixed this. :) At the menu I detailed above, pressed tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 

I'll edit my grub file once I've installed to disk. Thanks again for the direction - I've been a Fedora user since FC5 but have just decided to switch to Ubuntu, and it's already paying dividends in community support.

---

### Post by wojox on 2011-03-03
Good call on editing the boot line. :P

I forgot Live-USB is different then Live-CD. 

You must have a nvidia card? Fedora has never given me problems with my nvidia card. I just choose the basic video driver. Ubuntu should do something like that.

---

