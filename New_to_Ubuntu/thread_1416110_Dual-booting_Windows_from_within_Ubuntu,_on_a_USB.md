---
title: "Dual-booting Windows from within Ubuntu, on a USB"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by Ayyas on 2010-02-25
Hey everbody, new to the forum and i have a beginner question question.

So i'm attempting to dual boot Windows 7 with Ubuntu. Due to extenuating circumstances, I had to install Ubuntu first instead of the other way around. Normally i would just use the Windows boot CD and everything is fine and dandy, unfortunately my optical drive is broken (it's not an Ubuntu driver issue, the actual drive is broken) so i've been using USB's and .ISO's to install programs and OS's. 

The problem being i can't figure out how to install the Windows 7 on the USB from within Ubuntu, all the tutorials i've come across either describe it from within Windows which has a completely different architecture. 


I'm running 9.10 on a Compaq Presario F756NR
BTW, i'm not worried about having to do a clean install, that would be ok, i've got my files i need backed up. 

Any help is greatly appreciated

-Ayyas

---

### Post by spiky001 on 2010-02-25
can you do a usb install of win7 then install karmic? win7 is installable from usb

---

### Post by wilee-nilee on 2010-02-25
If you have at least 2 gigs of ram you can install the W7 iso in a Virtual machine, will run clunky though probably. Or go to a windows computer with administrative access and download this W7/DVD usb loader, it is the only one I know that can load a legal copy to a thumb.
[http://wudt.codeplex.com/](http://wudt.codeplex.com/)
This is a link to a site, it is the same one you can get at the MS store if you want to go there for it.

The is a MS USB loader and will inspect your ISO for a genuine copy seal of approval. ;)

---

### Post by Ayyas on 2010-02-25
Thanks for the advice on the virtual machine.
I'm currently running VirtualBox, the problem is that i can't get it to recognize the jump-drive though.

---

### Post by lavinog on 2010-02-25
Is this a desktop?
I would find an optical drive that works, or find a working windows machine to setup the usb drive...how much is your time worth?

---

### Post by Jeff Anthony on 2010-02-25
VirtualBox doesn't allow you to access USB, at least the free version doesn't. If you're trying to get W7 into a VM then just mount the .iso, skip using the USB drive. If it's already on the thumb drive just copy it over to your public folder. I have a good walkthrough for XP/Karmic seamless mode at the site in my signature. What are you intending to do with the Windows?

---

### Post by lavinog on 2010-02-25
> **Jeff Anthony said:**
> VirtualBox doesn't allow you to access USB, at least the free version doesn't. If you're trying to get W7 into a VM then just mount the .iso, skip using the USB drive. If it's already on the thumb drive just copy it over to your public folder. I have a good walkthrough for XP/Karmic seamless mode at the site in my signature. What are you intending to do with the Windows?

I don't think the OP wants to install windows in a vm, they were doing it just to create the usb windows installer for windows 7 because their optical drive is borked.

---

### Post by Ayyas on 2010-02-25
That is correct Lavinog.

Anyway, it looks like i'll have to wait until i can use someone else's windows machine which isn't that big of a deal since i was only going to use the partition for games.

Thanks for the input everyone, it doesn't look like there's anything else i can do but wait, at least i know what the situation is right now. 

Though if anyone has anything else, speak up :D

---

