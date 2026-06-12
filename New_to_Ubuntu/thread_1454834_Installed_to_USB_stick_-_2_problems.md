---
title: "Installed to USB stick - 2 problems?"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by anewguy on 2010-04-15
Well, I downloaded beta 2 of 10.04 and did an install to a 4gb USB stick.  That part seemed to go fine.

Next, I tried to boot from USB (my BIOS doesn't have that setting, just "from other boot devices" as an option, which is what I tried, with the IDE controller off), it never booted as it never looked at the USB stick.  Does anyone out there know if it is even possible to boot from USB on a MSI K8T-Neo board?

Also, when I gave up and set the BIOS back to my normal boot order, I got a grub error about some long set of numbers device not found.  I had to boot from the LiveCD and redo grub from it before I could boot again.  I have a couple of questions on that:

- what the heck happened?

- I've seen some references to the long string of numbers for devices and always just ignored them in the past.  I guess the time has come for me to get past the "mystery" and learn what those device numbers are - where they come from, what they are used for, etc..  Can anyone point me to some good documentation on that?

Thanks in advance!

Dave ;)

---

### Post by Paqman on 2010-04-15
> **anewguy said:**
> Does anyone out there know if it is even possible to boot from USB on a MSI K8T-Neo board?


Google might shed some light. But I think you've got the right idea, some boards just don't like to boot from USB.

> 
Also, when I gave up and set the BIOS back to my normal boot order, I got a grub error about some long set of numbers device not found.  I had to boot from the LiveCD and redo grub from it before I could boot again.  I have a couple of questions on that:

- what the heck happened?

- I've seen some references to the long string of numbers for devices and always just ignored them in the past.  I guess the time has come for me to get past the "mystery" and learn what those device numbers are - where they come from, what they are used for, etc..  Can anyone point me to some good documentation on that?


They're [UUID]("http://en.wikipedia.org/wiki/Uuid")s. What I suspect may have been the problem is turning your storage controller off and on. I have no idea what actually generate the UUIDs, but something has obviously reset them.

Bascially they're just a way for your system to identify your drives. You can get the system to spit out a list of the UUIDs with this command:
```
sudo blkid
```
You don't need to know too much about them really.

---

### Post by mcduck on 2010-04-15
For the first problem, I don't know if there's any way to add support for booting from USB to your BIOS. Try checking if there's a BIOS update available for you...

What comes to the "long set of numbers", that's the UUID (Universally Unique Identifier), which is given for each partition when it's created (or formatted) and is used to detect partitions on your hard drive and different devices. The reason why you get such error complaining about device not found is that when you installed Ubuntu to your USB drive you installed part of the Grub bootloader into your computer's hard drive, and now that part is loaded on boot and tries to look for the USB drive...

In the last stage of the installer you'll see an "Advanced"-button, clicking that allows you to define where Grub should be installed. If you want to install Ubuntu on a removable drive you should tell the installer to put Grub on that drive as well, instead of putting it into your hard drive.

---

### Post by Paqman on 2010-04-15
> **mcduck said:**
> The reason why you get such error complaining about device not found is that when you installed Ubuntu to your USB drive you installed part of the Grub bootloader into your computer's hard drive, and now that part is loaded on boot and tries to look for the USB drive...


Actually, that makes a whole lot more sense than the waffle I posted.

---

### Post by anewguy on 2010-04-15
Aha....so it changed the existing grub stuff in the mbr on my hard drive (I had/have Windows and Ubuntu 9.10 already there) to point to the USB device for the grub2 config.  Now that makes sense - I thought it would just update the grub2 config on my hard drive to include the USB stick, but didn't think about the idea that since I was installing to the USB stick it would by default point the hard drive mbr *TO* the USB stick.

Thanks!

Dave ;)

---

