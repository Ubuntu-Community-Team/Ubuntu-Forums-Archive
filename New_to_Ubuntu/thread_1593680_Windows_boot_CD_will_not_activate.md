---
title: "Windows boot CD will not activate"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by eponymous_anonymous on 2010-10-11
Hi. I'm trying to get an older tower PC to dual boot with Windows XP and Ubuntu 10.04, but I think I'm going about this in the wrong way. I've just installed Ubuntu and when I try to start my Windows boot CD it starts out with the " Press any key to boot from CD" message and does not recognize any keys I press at that time, it simply moves on into the Ubuntu startup process.
Anybody have ideas on:
A) Removing Ubuntu from the drive entirely so as to let Windows install unimpeded
or
B) What I can do to get the Windows boot CD to recognize the keystrokes and let me begin the installation process


Thanks a lot,

---

### Post by Hippytaff on 2010-10-11
If you want to dual boot it is probably best to have windows installed first...and then set up ubuntu with gparted (on the live cd) to be the secondary os (in my experience.) or use Wubi which means that ubuntu is kind of inside windows. :-)

---

### Post by 23dornot23d on 2010-10-11
Sounds like a problem with the Windows Boot CD ..... 

When you boot from a CD ..... that is the only thing that is used is the CD from a clean boot.

( Have you set the BIOS to boot from CD or selected CD as your boot option ..... is the Windows CD a bootable CD  ? just checking )

______________________________________________________________________ 

Ubuntu is not accessed at this point it sits on the Hard Drive but is not accessed ....

So I would just make sure that the XP disk is not damaged or scratched ......

---

### Post by amjjawad on 2010-10-11
Couldn't agree more with what the other guys said :)

---

### Post by coffeecat on 2010-10-11
> **eponymous_anonymous said:**
> Press any key to boot from CD" message and does not recognize any keys I press at that time, it simply moves on into the Ubuntu startup process.

It sounds as though you have enabled booting from CD in the BIOS but that you haven't enabled BIOS USB support and that you are using a USB keyboard. If so, enable USB in the BIOS (sometimes referred to as legacy USB for some obscure reason) and/or use a PS2 keyboard.

---

