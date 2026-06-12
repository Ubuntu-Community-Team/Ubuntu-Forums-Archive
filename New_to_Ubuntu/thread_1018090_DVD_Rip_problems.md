---
title: "DVD Rip problems"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by bcondemi111 on 2008-12-21
Have many problems with DVDRIP. I have a firewire dvd player and is mounted and can read and play any dvd. When I use dvdrip to save the movie on my drive, get error messages that the dvd can't be read and to check my preference?
Checked debug and everything is installed.
what am I doing wrong?

BC

edit...

upon further investigation, it seems that acidrip nor dvdrip can see my dvd? I have it in an enclosure and works fine in windows. but in linux, it doesn't see it? I now changed to the usb connection instead of the firewire, and still problems.
maybe I need the path where the drive is?

anyone know what to do?

bc

---

### Post by Tatty on 2008-12-21
But you say that you can play movies in linux?  So linux itself must be able to see it, the problem must be with DVDRip or AcidRip.

Try changing the video source path in acidrip to /dev/scd0

---

### Post by bcondemi111 on 2008-12-21
Ok I meant Ubuntu(linux). Yes it sees it but does not mount the media(dvd movie).
Believe it or not, changing from a firewire cable/connector to the usb connection solved the problem?
It 'came alive' when I used the usb connector (from the enclosure). And yes the firewire cable itself works fine on another external drive.

Anyway, another question, when using dvdrip, and after you enter the title of the project, how come I have to manually type in the location of the dvd media?

by default, the location is /dev/scd0. However, after looking at my volume properties for the dvd, it said /media/cdrom0. I copied and pasted that into the source/location and voila! went to the next screen and read the title no prob!

Would love to have the default changed to /media/cdrom0 though...

thanks

BC

---

### Post by bgast1 on 2008-12-21
I don't know how helpful this will be, but I have an external hard drive that can be connected both firewire and USB. On some distros that I have tried, when my HD was connected via firewire it was not seen out of the box. But when I connected it USB all of my problems were solved. Do you have the option to connect it with a USB cable? It might help.

---

### Post by bcondemi111 on 2008-12-22
Yes, Only my usb connection works. I do have the option to use either firewire or usb.
When I used my firewire hard drive, it would not 'wake up' on power. Only once the os was fully loaded and ready I then could hear the drive spinning at a faster speed and essentially 'come alive'. I could never boot up a live cd (any distro) with a connected firewire drive.
This is perhaps why my firewire cdr doesn't seem to work. However usb does.

BC

---

