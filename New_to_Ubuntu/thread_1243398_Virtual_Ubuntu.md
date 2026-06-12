---
title: "Virtual Ubuntu"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by RichardCL on 2009-08-18
Dear Forum,

I travel a lot and need to access my emails from friendly computers that I can have access too. Many of my colegues use either webmail or Outlook with a .pst file on USB key.

I'm new to Ubuntu and using that as my main system at home but I'm thinking that there may be a better solution.

I want to install Ubuntu to a USB key or USB HDD with Gnome and Evolution. Then configure it to access my IMAP and POP3 mails. I then expect that I can boot any system from the USB and use it as if it where my own without touching the native HDD.

I guess I need a simple install without detecting my hardware (no NVIDA drivers etc).

Is there also a way that I can then run that from within a system rather than rebooting? For example, I'd run the Ubuntu from stick from within Windows as a window. This would be useful on systems that don't allow USB booting.

TIA


Rich

---

### Post by LowSky on 2009-08-18
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Hospadar on 2009-08-18
you might be able to run virtualbox off a usb stick inside of windows, but it seems like that would be so slow and difficult you might just as well use windows.

Or get one of those usb sticks that you can run [windows] programs off of and just install thunderbird to it.  Not that I don't think you should use linux, but running a virtual ubuntu off a flash drive would be hella-slow and a total pain just to read some email that you could read just as easy natively in windows.

---

### Post by howefield on 2009-08-18
> **Hospadar said:**
> ...Not that I don't think you should use linux, but running a virtual ubuntu off a flash drive would be hella-slow and a total pain....

Have you actually tried it ? (Ubuntu installed to usb - not virtual)

It might be surprisingly good. Works well when I use it.

System > Administration > USB Startup Disk Creator

---

### Post by Penguin Guy on 2009-08-18
You can only run an operating system inside another operating system with Virtualbox (or something that does the same job). So if you were to do this you would need to include a copy of Virtualbox for Windows on the USB drive as well as Ubuntu. It would be a lot, lot easier to just install Thunderbird to the USB drive instead.

---

### Post by RichardCL on 2009-08-25
It seems that neither option is going to work.

I originally wanted to run Ubuntu as a "program" from within Windows. A mentioned here though, that requires install/change of the host system. It also requires me to have the exact version of Virtual box for the host system.

I also looked at the possibility of moving my home email system to an OS with email client on my USB disk. That would boot as USB while away as required but the problem is that Virtual box won't let me boot from a USB device yet. Looks like there will be a solution soon.

In the meantime, I'm going to have to make do with a bootable USB harddrive for the road and regularly back-up my mail settings to that.

---

