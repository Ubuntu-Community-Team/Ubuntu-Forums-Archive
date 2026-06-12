---
title: "Installing onto my laptops hard drive using my PC"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by n844 on 2009-09-24
Hi there,

I'll try and keep this simple.

I have a main computer with Ubutnu and Vista installed as a dual boot.

I have a laptop with a blank hard drive, a CD drive that doesnt work and can't boot from USB. Thus no way to install anything.

I take the laptop hard drive out of the laptop and connect it to my main pc using a IDE to USB cable, windows views it as an external hard drive.

I run the wubi installer and install to the laptop hard drive.

It doesnt run on the laptop as there is no boot manager.

How do I install a boot manager onto the laptop hard drive in this situation?

Thanks very much for your time, Louis.

---

### Post by LewRockwell on 2009-09-24
just use the LiveCD to install Ubuntu to the hard drive of your choice

.

---

### Post by halitech on 2009-09-24
WUBI installs it as a program inside windows so it probably added the boot info to your PCs boot loader instead of to the laptop drive. Disconnect (if you can) the internal drive in the PC, boot using the Live cd and install to the laptop hard drive.

---

### Post by staticextasy on 2009-09-24
I installed Jaunty on my laptop just recently inside of windows, it was pretty easy. I recommend using that feature.

---

### Post by halitech on 2009-09-24
> **n844 said:**
> 
I have a laptop with a blank hard drive, a CD drive that doesnt work and can't boot from USB. Thus no way to install anything.


> **staticextasy said:**
> I installed Jaunty on my laptop just recently inside of windows, it was pretty easy. I recommend using that feature.

would work except for the lack of windows on the laptop drive to run the wubi installer

---

### Post by Bartender on 2009-09-24
+1

wubi was the wrong choice.
wubi needs an existing Windows installation, with NTFS formatting etc. already in place, to function.

What you want to do is boot to a standard Ubuntu install CD, or the alt-install CD, go thru the first four steps, then when you get to the partitioning make sure that you install Ubuntu to the HDD that you've temporarily attached to your desktop PC.

I'd suggest unplugging the desktop PC's HDD or HDD's in order to avoid confusion caused by the Linux bootloader, GRUB.  Even if you're installing Ubuntu to a second or third HDD, the installer will look for an existing Windows HDD.  If it finds one, it will place a tiny bit of data in the Windows MBR.  That is _NOT_ what you want.  If you let the installer place GRUB Stage 1 on your Windows HDD, then unclip the laptop drive, the desktop PC won't be able to start up Windows and the laptop drive won't work either.  

You can stop the default bootloader installation and steer it where you want by following the little "Advanced" button at the last step of the installation process.  If you can figure out the options that are listed.

IMO it's much simpler to simply unplug all other HDD's so that the Ubuntu installer sees only the laptop drive.  Then there will be no questions about the bootloader.  The installer will put everything on the laptop drive.

---

### Post by staticextasy on 2009-09-24
> **halitech said:**
> would work except for the lack of windows on the laptop drive to run the wubi installer

True story :P

---

### Post by LewRockwell on 2009-09-24
> **halitech said:**
> WUBI installs it as a program inside windows so it probably added the boot info to your PCs boot loader instead of to the laptop drive. Disconnect (if you can) the internal drive in the PC, boot using the Live cd and install to the laptop hard drive.


> **staticextasy said:**
> I installed Jaunty on my laptop just recently inside of windows, it was pretty easy. I recommend using that feature.

OP wants a full, fresh install of Ubuntu on a hard drive

no wubi

no windoze

just smooth ubuntu

.

---

### Post by LewRockwell on 2009-09-24
talk about "post-splash"

lol

.

---

### Post by staticextasy on 2009-09-24
> **LewRockwell said:**
> OP wants a full, fresh install of Ubuntu on a hard drive

no wubi

no windoze

just smooth ubuntu

.

I got that now haha, i wasn't paying attention, I'm running on lack of sleep atm haha, sorry for my bad 2 cents :D.

---

