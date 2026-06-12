---
title: "Booting other programs from USB"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Mcalhoun on 2009-05-23
Ok, I hate to ask this but am completely stuck.  I have a program that needs to boot from a USB stick.  This is not an Ubuntu program but grub keeps blocking any attempt to boot to the usb stick and gives "error 25".  Even setting the bios to allow booting to the USB with no device attached to the usb gives this error. 

 I am running a dual boot Windows XP and Intrepid on a Dell Dimension E510.  I've already tried playing with everything I can find on the forums and other sites but everything seems to be geared towards booting Linux from a usb but that's not what I'm trying to do.

I hate to be a bother but don't even know what further info you'd need to be able to help me.  (God I hate to even type that)  

NotAccustomedToBeingTheNoob--Mike

---

### Post by akimatsu123 on 2009-05-23
> **Mcalhoun said:**
> I can find on the forums and other sites but everything seems to be geared towards booting Linux from a usb but that's not what I'm trying to do.

NotAccustomedToBeingTheNoob--Mike

Exactly what are you trying to do? Are you trying to boot something off a USB? For that to happen, the USB needs to be configured for that (bootable, active partition, bootloader, etc). 

To boot off a USB, you don't use Grub. You should interrupt ur bios at startup and choose boot from external media, then choose USB. Your system shouldn't load till grub.

If that's not what you are trying to do, please be more specific. What "program" is it? Typically "programs" run in an OS after boot, not independent of it, so I'm not exactly sure what u mean. If the above didn't help, please be more specific and maybe post the contents of your /boot/grub/menu.lst please so we can see whats wrong.

---

### Post by Mcalhoun on 2009-05-23
Sorry for being so vague, I did figure it out.  I have onboard usb ports in the rear of the tower and some in the front.  It seems if I plug into the ports in the rear it will boot fine, not so with the ones in the front.

Thanks for the response anyway.

The program I was trying to load was a not so respectable program and didn't want to mention it on this forum.

---

