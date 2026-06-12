---
title: "Picking up Rs232 output in linux"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by ScaryCat on 2009-04-08
Hi, I have a device connected over RS232 to my computer and I wanted to know if there was a simple C or C++ program that could be constructed to read from this device and output the values it is sending.

It sends a validation byte and two information bytes at a Baud rate of 9600. Also it has one stop bit.

All I need something that displays some or all of the information that the device sends.

Any help would be appreciated.

Failing this ANYTHING that can help me just display some sort of output from this device in terminal would be great.

Thanks in advance.

---

### Post by MrWES on 2009-04-08
> **ScaryCat said:**
> Hi, I have a device connected over RS232 to my computer and I wanted to know if there was a simple C or C++ program that could be constructed to read from this device and output the values it is sending.

It sends a validation byte and two information bytes at a Baud rate of 9600. Also it has one stop bit.

All I need something that displays some or all of the information that the device sends.

Any help would be appreciated.

Failing this ANYTHING that can help me just display some sort of output from this device in terminal would be great.

Thanks in advance.

Try this document:

[http://www.mm.helsinki.fi/~mpastell/serial.pdf]("http://www.mm.helsinki.fi/~mpastell/serial.pdf")

Here's another thread:

[http://ubuntuforums.org/showthread.php?p=6953401]("http://ubuntuforums.org/showthread.php?p=6953401")

I'd be interested in any success you might have. I currently run 4 laptops gathering SPC data via RS232, but of course they are running Windows XP.

Thanks,
Bill

---

