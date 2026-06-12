---
title: "Need a little help installing Ubuntu on external USB drive"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by sarc on 2010-09-13
Hello:

I have a brand new HP ProBook 6555b with Vista, I use it for work and I must be 100% sure I do not do ANYTHING at all to my notebook internal hard disk - no changes to MBR, Vista loader etc.

Could someone confirm that this method will allow me to boot Ubuntu 10.4 without making ANY changes to my hd0 (notebook internal hard disk) AS LONG AS I CLICK ADVANCED AND TELL THE INSTALLER TO INSTALL GRUB IN THE USB HARD DISK?

p.s. I have experience with installing Ubuntu and manual partition setting.

Thanks!!!


Quote:
Originally Posted by beew  
You just do it in the same way that you would for an internal hard drive. 

Boot from a live usb (or a live CD) and insert the external drive. Then click install Ubuntu 10.04 on the desktop and go through the usual installation steps, but at step 4(?) click install manually and 
choose your external drive to install Ubuntu to.

Be sure about the name of the external drive so you don't wipe out your internal drive. In the final step choose "advanced" and install the boot loader in your external drive and click install and wait. That's it. 

You don't need to edit anything like they say in the Ubuntu Geek link. I tried that on a 40G hard drive which I removed from an old laptop and use as an external drive as well as a 8 G pendrive. Both work flawlessly.

P.S. According to this link you don't need to set aside 30G for ntfs (or FAT32). It says there is a utility for Windows to read ext3 format. I haven't tried that out though.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I assume that you want the 30 ntfs just so that Windows can assess files in it, since I don't think it is possible to install and run Windows on an external drive.

---

### Post by amjjawad on 2010-09-13
With Windows, you can't but I'm not sure whether you can do it with Ubuntu or not?

I might try that option and see if it does work!

---

### Post by Radioman991 on 2010-09-13
If you REALLY want to be certain you don't bork the internal drive, pop it out of the laptop, boot the Ubuntu CD, and have the USB drive plugged in.  Did this with my former employer's IBM Thinkpad.  As long as you can set BIOS to boot to your USB drive, you are golden afterwards.

---

### Post by beew on 2010-09-13
I can confirm that it works. :)

Radioman is correct that some people remove their internal drives first just to be ultrasafe, but I didn't do it. Just make sure you don't mix up the internal and external drives and that's it.

---

### Post by sarc on 2010-09-13
Thanks guys!):p

---

### Post by C.S.Cameron on 2010-09-13
I suggest unplugging the internal HDD not just to be safer but also to get a cleaner grub.cfg file, (without a menuentry for the internal HDD).

---

### Post by amjjawad on 2010-09-13
> **C.S.Cameron said:**
> I suggest unplugging the internal HDD not just to be safer but also to get a cleaner grub.cfg file, (without a menuentry for the internal HDD).

He has a laptop and it's not his personal laptop so that won't be a great idea ;)

The best options as the guys said is to use the Live CD (for testing) and an External HD. Set your BIOS to boot first from your USB-Stick then your External HD and DISABLE the other options.
Go to BIOS First Page and DISABLE your HDD (the internal one).
Save BIOS settings and reboot.

There you go!

I had a serious problem with my machine and I'm writing here while I'm booting from my USB-Stick without any installation at all.
I'm attaching only my USB-Stick and an External HD but I can't try it now.

Beew, I'll try that soon and hope it works ;) I can't try it now though!

---

