---
title: "ubuntu frozen after plug in a flash memory"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by wy10002001 on 2011-06-22
Ubuntu does not recognize USB port. It is worse than that. After I plug a flash memory at USB port, the computer became frozen. So I had to turn off the power and shut it down. When I re-started the computer, it took a much longer time. I used the terminal and typed sudo lsusb, then computer was frozen again.

---

### Post by ajgreeny on 2011-06-22
Do you have any idea what is on the usb drive?  Could there be something that is causing the freeze in some way.

I have never had the problem with a usb drive but a CD I have with a windows installation program for Abbyy Finereader 5 OCR program always causes the machines I have tried to install it on with wine to freeze, and that is even before the disk has been read.  Note "machines";  not just one but two, a desktop and a laptop.  I have never found out what is going on, and did once manage to just read the CD, nothing more, but then it immediately froze the machine.  I don't have a windows machine to try it on, but I assume it could be an autorun prompt of some kind that is making this happen.

Very weird!

---

### Post by jtarin on 2011-06-22
What version of Ubuntu are you using? Can you give the specs on your computer?
What USB devices to you have plugged in?

---

### Post by tgalati4 on 2011-06-22
I've seen USB ports fail on both laptops and desktops.  It's not pretty.
Poor soldering or flexing of the board or simply shorting out by sticking keys in the slot (alcohol induced).

Boot the machine and open a terminal to full screen:

dmesg | tail -f

Now plug in your USB device and capture what comes on the screen.  Use a digital camera if you have to.

It's also good to have a fire extinguisher handy.

---

