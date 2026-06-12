---
title: "Installing an external drive"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by sum23 on 2009-08-19
I have a mini dell 9 with a Ubuntu OS, and I have bought a Rosewill external DVD drive so that i can install Windows XP. The DVD drive came with Nero 8, and the OS recognizes it and reads it but it only brings up files, I can't install the Nero 8 or anything that I've tried.  I am computer illiterate so, details would be great.... If anyone can help me I would be grateful!!

---

### Post by Schendje on 2009-08-19
Are you trying to open Nero on Ubuntu? Because I think it's a Windows-only program.

You can use Brasero to burn discs.

(Correct me if I didn't understand it :P)

---

### Post by LewRockwell on 2009-08-19
> **sum23 said:**
> I have a mini dell 9 with a Ubuntu OS, and I have bought a Rosewill external DVD drive so that i can install Windows XP. The DVD drive came with Nero 8, and the OS recognizes it and reads it but it only brings up files, I can't install the Nero 8 or anything that I've tried.  I am computer illiterate so, details would be great.... If anyone can help me I would be grateful!!

we're not sure exactly what the actual trouble-call is?

you've got a Dell netbook with Ubuntu on it(you might note the specifications in case someone has any special notes for you and your equipment)

you've got a Rosewell External DVD drive

just toss the Nero 8 aside and don't worry about it

we'll wait for some additional feedback before we go any further

.

---

### Post by sum23 on 2009-08-19
> **Schendje said:**
> Are you trying to open Nero on Ubuntu? Because I think it's a Windows-only program.

You can use Brasero to burn discs.

(Correct me if I didn't understand it :P)


Well, the external drive says its compatable with Linux, and when I put in a disc it picks up some files from the disc (don't ask me what they are) because when I click on them they bring up what looks like programming stuff, and that's if the icon opens.  

I think there is something I've not set up, turned on, or configured on my computer.  What I ultimately want is to install XP which I have purchased.  And I don't understand why the external drive either isn't being recognized or won't install anything.  This is my second drive.  I tried an LG, I think, before.......

I'm not really familiar with Ubuntu, I just expected when I plugged in the external that it would say something like Windows ususally does like "drive detected" or maybe the name of the drive, to let me know it's connected, but it only brings something up when I put a disc in the drive.....

---

### Post by sum23 on 2009-08-19
> **LewRockwell said:**
> we're not sure exactly what the actual trouble-call is?

you've got a Dell netbook with Ubuntu on it(you might note the specifications in case someone has any special notes for you and your equipment)

you've got a Rosewell External DVD drive

just toss the Nero 8 aside and don't worry about it

we'll wait for some additional feedback before we go any further

.

Well, the external drive says its compatable with Linux, and when I put in a disc it picks up some files from the disc (don't ask me what they are) because when I click on them they bring up what looks like programming stuff, and that's if the icon opens.  

I think there is something I've not set up, turned on, or configured on my computer.  What I ultimately want is to install XP which I have purchased.  And I don't understand why the external drive either isn't being recognized or won't install anything.  This is my second drive.  I tried an LG, I think, before.......

I'm not really familiar with Ubuntu, I just expected when I plugged in the external that it would say something like Windows ususally does like "drive detected" or maybe the name of the drive, to let me know it's connected, but it only brings something up when I put a disc in the drive.....

---

### Post by LewRockwell on 2009-08-19
let's do this:

place Ubuntu LiveCD in DVD drive and boot your system

if the LiveCD menu selections come up(try ubuntu without changing anything, install, memtest, boot from hard drive)

then your Dell netbook is booting from USB first(which is what you want for what you desire to do)

note: if you don't have a LiveCD then you can just put your Windows disk in to test(the windows menu would come up during a successful USB boot) Just don't go any further in the windows disk than the first menu or you might initiate the destruction of your current hard drive contents

.

---

### Post by LewRockwell on 2009-08-19
couple more questions:

did your Dell come with one or more disks(recovery/reinstall/etc)?

which version of Ubuntu are you currently using?

are you familiar with the method to enter your Dell's BIOS settings?
(usually this is accomplished by pressing F2 at start-up)

if your machine doesn't boot from the USB first then you can go into the BIOS settings and change the boot order so that it does

.

---

### Post by Aptana on 2009-08-19
To install Windows you need to put the disk in the drive and then turn on the computer, hopefully it will boot the computer from the Windows disk and you'll be able to install.

if it goes straight into Ubuntu when you do that then you need to change the boot device priority (basically tells the computer where to boot from). You can change this in the BIOS which can be accessed by pressing F2 or Delete as the computer turns on.

Put the DVD drive at the top of the priority list and reboot your system.

If it still doesn't work then there is a problem with the computer recognising the DVD drive. :)

---

