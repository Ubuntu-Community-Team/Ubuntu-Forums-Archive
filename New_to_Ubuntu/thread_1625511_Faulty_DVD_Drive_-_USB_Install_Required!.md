---
title: "Faulty DVD Drive - USB Install Required!"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by chome4 on 2010-11-19
Is there a way to burn an ISO file onto a USB stick? My DVD drive's faulty and I need to upgrade Ubuntu. I seem to stumble across lots of reference to running Ubuntu from a USB drive but not much about actually installing it.

Hope someone can help.

Thanks in advance.

---

### Post by DanaLou on 2010-11-19
I found this:

[http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html)

---

### Post by Hippytaff on 2010-11-19
there is - try unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
Edit -> sorry, did you mean persistente usb?
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by chome4 on 2010-11-19
Thanks. I'll make a start tonight!

---

### Post by philinux on 2010-11-19
System Admin> Startup Disk Creator.

Simples.

---

### Post by Hippytaff on 2010-11-19
> **philinux said:**
> System Admin> Startup Disk Creator.
 
Simples.
 
And that :-s :-)

---

### Post by chome4 on 2010-11-19
Story so far:

Using: System Admin> Startup Disk Creator

I reboot on another machine with working DVD drive and get:

boot:

I hit the return key and get:

Could not find kernel image: linux

The (test) machine is in good working order and works OK with booting with the DVD.

---

### Post by IkeFalson on 2010-11-19
I'm not sure what you're actually trying to do here, why does it matter if the test machine has a working DVD player if you are booting from a USB?

Anyway I recently upgraded from an older version to a new one using a USB stick.  Plugged it in while the old version was running and made a USB start up disc as you already have seen how to.  I had some problems with it failing to install properly to the USB though (it seemed to not unmount).  But there is a way you can do it in Windows if you can dual boot.

If you have the option to use Windoze it might be worth a try, just go to the Ubuntu website and it has instructions on how to make a USB startup disc from Windoze.

And remember to adjust the boot order from the BIOS - that stumped me for a while, but I'm totally new to all this and that's my excuse and I'm sticking to it...

Ike

---

### Post by chome4 on 2010-11-19
My machine has a faulty DVD drive and I'm using a neighbours machine to make the USB boot device.

---

