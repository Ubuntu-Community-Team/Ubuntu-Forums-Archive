---
title: "[SOLVED] Question about installing ubuntu in another hard drive"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by J03y on 2008-12-30
Hello, I recently bought a new usb hard drive in which I want to install Ubuntu. My computer already came with Windows Vista installed but I was wondering if GRUB was going to take over when my computer started even if its going to be installed in another hard drive.

---

### Post by harshpkaria on 2008-12-30
So, you want grub to take control over your PC or not?
To solve your problem (which needs further clarification) I suggest you Wubi...
Wubi works as follows..
>>Installs Ubuntu on any partition you want. Even on the same as Vista (C drive)
>>On start up you have a dual boot up, to select your OS.
>>If not satisfied with ubuntu (Which I bet, u will never be dissatisfied) u can just delete wubi from Add/Remove Programs from your Vistas control panel, and u are back to square one.

Enjoy..

---

### Post by eBoxNet on 2008-12-30
> **J03y said:**
> Hello, I recently bought a new usb hard drive in which I want to install Ubuntu. My computer already came with Windows Vista installed but I was wondering if GRUB was going to take over when my computer started even if its going to be installed in another hard drive.

if you try to install ubuntu on your computer you will get a dual boot machine - grub will load and ask if you need to boot vista or ubuntu.

its better for you i think to unplug your hdds and then install ubuntu on your usb hdd.

with that way the only disk that ubuntu will effect will be your usb one.

---

### Post by J03y on 2008-12-30
> **harshpkaria said:**
> So, you want grub to take control over your PC or not?
To solve your problem (which needs further clarification) I suggest you Wubi...
Wubi works as follows..
>>Installs Ubuntu on any partition you want. Even on the same as Vista (C drive)
>>On start up you have a dual boot up, to select your OS.
>>If not satisfied with ubuntu (Which I bet, u will never be dissatisfied) u can just delete wubi from Add/Remove Programs from your Vistas control panel, and u are back to square one.

Enjoy..No I don't want GRUB to take control and I already tried Wubi but it didn't work out.

---

### Post by .Maleficus. on 2008-12-30
As long as you install GRUB on the MBR, you should be fine, eg, on the Vista partition.  You might also consider changing your menu.lst to boot by UUID.  UUID is a universal identifier for each component of your system, so even if the external hard drives letter changes (goes for /dev/sda to /dev/sdb) it will boot to the correct device.  To find the UUIDs, simply run 'ls -l /dev/disk/by-uuid'.


Edit:  So, you don't want GRUB to start?  Are you just planning on plugging the drive in when you want to boot to Ubuntu then?  If that's the case, just install GRUB on the external and set your BIOS boot order to boot from USB and then the first hard drive, only plugging the external in when you want to boot Ubuntu.

---

### Post by Bucky Ball on 2008-12-30
Install grub on the external USB drive when you are asked where you would like it, not on the MBR. Then it will bootstrap that (Windoze MBR) to the menu without effecting the setup on your current Windoze partition. :)

.Maleficus: OP doesn't want to effect the windoze partition. Only when USB drive plugged in is the option to boot to Ubuntu. Unless I am misunderstanding.

---

### Post by J03y on 2008-12-30
> **.Maleficus. said:**
> As long as you install GRUB on the MBR, you should be fine, eg, on the Vista partition.  You might also consider changing your menu.lst to boot by UUID.  UUID is a universal identifier for each component of your system, so even if the external hard drives letter changes (goes for /dev/sda to /dev/sdb) it will boot to the correct device.  To find the UUIDs, simply run 'ls -l /dev/disk/by-uuid'.Actually I was just planning on going into my BIOS and selecting the usb hard drive to boot into Ubuntu without GRUB taking over anything. So when I decide to use Vista it could just boot into Vista automatically w/o GRUB popping up.

---

### Post by J03y on 2008-12-30
> **.Maleficus. said:**
> As long as you install GRUB on the MBR, you should be fine, eg, on the Vista partition.  You might also consider changing your menu.lst to boot by UUID.  UUID is a universal identifier for each component of your system, so even if the external hard drives letter changes (goes for /dev/sda to /dev/sdb) it will boot to the correct device.  To find the UUIDs, simply run 'ls -l /dev/disk/by-uuid'.


Edit:  So, you don't want GRUB to start?  Are you just planning on plugging the drive in when you want to boot to Ubuntu then?  If that's the case, just install GRUB on the external and set your BIOS boot order to boot from USB and then the first hard drive, only plugging the external in when you want to boot Ubuntu.Yes, exactly. So if I just install Ubuntu in my external drive then GRUB wont take over my PC, only when I plug in my usb drive?

---

### Post by .Maleficus. on 2008-12-30
> **J03y said:**
> Actually I was just planning on going into my BIOS and selecting the usb hard drive to boot into Ubuntu without GRUB taking over anything. So when I decide to use Vista it could just boot into Vista automatically w/o GRUB popping up.
If that's the case, all you would need to do is install GRUB to the external drive and it shouldn't affect any of your Windows install.  After you select the USB drive to boot from, you'll still see GRUB but with only Ubuntu entries.

---

### Post by Bucky Ball on 2008-12-30
:confused: That's what I just said.

---

### Post by mikewhatever on 2008-12-30
> **J03y said:**
> Actually I was just planning on going into my BIOS and selecting the usb hard drive to boot into Ubuntu without GRUB taking over anything.

Grub is Ubuntu's boot loader and needs to be installed, unless you have other means of loading OSs. It's important not to put it on the Vista HDD's MBR because if you do, Vista will not boot without the external HDD plugged in. If possible, it may be wise to disconnect the internal HDD to avoid confusion. If that's not possible, check out the guide [http://psychocats.net/ubuntu/dualboot](http://psychocats.net/ubuntu/dualboot). This step is particularly important -> [http://psychocats.net/ubuntu/images/dualboot14.png](http://psychocats.net/ubuntu/images/dualboot14.png). You'd have to use the Advanced button and specify where to put GRUB. The default location is usually hd0, which is not good for you. Change it to hd1.

---

### Post by Bucky Ball on 2008-12-30
> **.Maleficus. said:**
> If that's the case, all you would need to do is install GRUB to the external drive and it shouldn't affect any of your Windows install.  After you select the USB drive to boot from, you'll still see GRUB but with only Ubuntu entries.

That's what I just said. :confused:

I would advise you to allow grub to find the Windoze install and allow it to bootstrap that so you have a choice of OS from the grub menu. You will save yourself a whole lot of screwing around with going in and out of the bios, but then, that is a weird setup. I don't suppose you have any choice because if you did what I am suggesting, windows wouldn't boot without the USB drive!

Anyhow, good luck.

---

### Post by J03y on 2008-12-30
> **Bucky Ball said:**
> :confused: That's what I just said.Lol, thx, :D

---

### Post by Bucky Ball on 2008-12-30
[QUOTE=Bucky Ball]Install grub on the external USB drive when you are asked where you would like it, not on the MBR. Then it will bootstrap that (Windoze MBR) to the menu without effecting the setup on your current Windoze partition. :smile:

.Maleficus: OP doesn't want to effect the windoze partition. Only when USB drive plugged in is the option to boot to Ubuntu. Unless I am misunderstanding.[/QUOTE]

:)

---

