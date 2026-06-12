---
title: "grub problems"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by brianhillman on 2009-07-20
ok i recently took my laptop hard drive and installed xbuntu on it via usb adapter( the computer its self has no floppy or cd drive) and then took it off the usb adapter and went to put it back once i did i went to boot it and it said "no os found" and so i booted my desktop to ask the ? and got grub error 21 then i discovered i could only boot the desktop while the laptops hard drive was attached.is there a way to get it so the desktop ( which has win 7 and ubuntu ) and the laptop ( has latest xbuntu) to work separately?

---

### Post by bandgeek on 2009-07-20
Having a hard time understanding you did you install Xubuntu to the Laptop or the USB harddrive?

---

### Post by brianhillman on 2009-07-20
i installed it onto the laptop hard drive but in order to do that i had to open the laptop take the hard drive out and i then used a cable to connect it to my desktop via usb

---

### Post by CaptainMark on 2009-07-20
so the laptop hdd was attached to your desktop when you installed, sounds like a similar problem to what i had the other day. Try removing your desktops hdd before attaching the laptop hdd and try the process again, failing that you would have better luck attaching a usb-cd drive to the laptop for installing.  it sounds like its installed the grub loader files for the laptop on the the desktop hdd. 
Your other option is to repair the grub on the both systems, just google 'ubuntu repair grub'

---

### Post by brianhillman on 2009-07-20
thanks trying that now

---

### Post by jeppewinther on 2009-07-20
Sounds to me like Grub can't quite work out where you stuck the OS. Probably wondering why Disc2 is Disc1 all of a sudden, and where the hell did Disc2 go?

So, either try again with just the Laptop drive plugged in, or tell Grub whats what :)

---

