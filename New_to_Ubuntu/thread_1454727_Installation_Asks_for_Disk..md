---
title: "Installation Asks for Disk."
date: 2010-04-15
forum: New to Ubuntu
---

### Post by The Titan on 2010-04-15
I am trying to install Ubuntu 9.10 AMD x64 on a friends computer. It is an AMD and it is a 64 bit processor. I have the almost identical computer, used the same disk and installed it perfectly. 

When the installer is in the "Installing Base System" portion it asks for the Ubuntu 9.10 Karmic Koala disk that is obviously already in the drive.

He is installing on a secondary IDE hard drive and only 1 CDROM drive is installed.

I searched around and couldn't find anything. Has anybody else had this issue?

Thank You,
Daniel

---

### Post by Crunchy the Headcrab on 2010-04-15
Not sure if this will help or not but it could be an incompatible cd-rom drive.  My laptop used to have installation issues until I upgraded the firmware.

You could try installing from a usb stick.  If you have a disk image (iso) you can use unetbootin to create a usb install disk if his motherboard supports booting from usb.
> 
sudo apt-get install unetbootin
unetbootin can be found under applications > system tools > unetbootin
or
applications > accessories > unetbootin

WARNING: Unetbootin will erase all the data on your usb stick and make it act like a bootable cd.  You can reformat it later and do whatever you want with it, but in  the meantime it will eliminate any data you have on the usb stick.

---

### Post by The Titan on 2010-04-15
I don't actually own a USB stick, but we tried a different cdrom drive. The one that I used to install on my computer and we had the same problem.

Thank you for your reply, but no dice.

Any other Suggestions?

---

