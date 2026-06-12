---
title: "VirtualBox - how do I get the add-ons for 64-bit?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by anewguy on 2009-10-24
I'm running 64bit Ubuntu, and installed the VirtualBox software from their site for 64bit installations.  I can't remember the exact name now, but the additions (letting cursor move across all windows, display driver, etc.) won't install - says my configuration is not supported.  I have an old Win98SE virtual machine running as a guest and wanted to install my scanner and printer software in it to do some technical work, but they won't install because the screen doesn't go to the needed color depth.  When I ran this on my old system I was running 32-bit ubuntu and 32-bit virtualbox, and the additions did install then.  I know it is because of it being the 64bit version, but does anyone know of anyway to get the vboxaddons in the 64bit version of VirtualBox?

Thanks in advance!

Dave :)

---

### Post by Paqman on 2009-10-25
> **anewguy said:**
> I know it is because of it being the 64bit version

I'd say it's more likely because of the Win98 guest. You might want to check that Vbox additions supports Win98.

---

### Post by NCLI on 2009-10-25
There is no 64-bit support in Windows 98, so installing the 32-bit guest additions would be the right choice, if Guest Additions supported Windows 98, which I'm fairly certain it doesn't.

---

### Post by anewguy on 2009-10-25
I've had guest additions installed in the past with Win98, but that was also on a 32-bit machine.  You are both thinking the way I am - 64-bit VirtualBox wants to install 64-bit additions but can't because of Win98.

So, considering the VirtualBox download page from Sun says that if you are running a 64-bit Linux OS you *must* download the 64-bit VirtualBox, and I REALLY don't want to re-install Ubuntu to get 32-bit (at least not until I perhaps get 9.10 - might do a clean install them just to get the new file system, etc., and I suppose I could go with 32-bit then), I guess I'm stuck for now.  Oh well.

Can someone with a little more experience between the 2 please tell me if there is any noticeable performance difference between running 32-bit Ubuntu on a 64-bit processor versus running 64-bit Ubuntu on a 64-bit processor?

Thanks for the help!

Dave :)

---

### Post by Paqman on 2009-10-25
When you go to install the additions it should mount a disk image. IIRC that disk image contains both 32-bit and 64-bit guest additions. Just run the 32-bit one instead of the 64-bit.

---

### Post by doorknob60 on 2009-10-25
I'll tell you now, it DOES NOT MATTER whether you are using 64 bit or 32 bit Ubuntu, since Ubuntu is the host. What matters is the guest (Windows 98), and if the Windows Vbox addons don't work on 98 (I think they work on 2000+), then installing a different version of Ubuntu won't make any difference. Maybe try using Windows 2000 or XP instead of 98?

---

### Post by anewguy on 2009-10-26
Yeah, I'd try another version of Windows, but I dumped Windows quite a while ago and out of all the versions of Windows I did have, I only found an old CD for Windows 98 - I guess I passed the others along as I sold systems.  For what I want it for, it's not worth spending the money on another copy of Windows I won't use - oh well, but thanks for the ideas!

BTW - all I wanted to do was get my scanner working so I could trace USB in Ubuntu and see what the Windows version of the software sends when it turns off the scanner lamp, since in Linux my scanner lamp is not being turned off.  I've used the libusb development "stuff" before, so as long as I could see the conversation I would be able to go from there.

Dave :)

---

