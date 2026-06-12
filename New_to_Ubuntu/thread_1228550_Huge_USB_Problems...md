---
title: "Huge USB Problems.."
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Toui on 2009-08-01
Hey Guys, 
So I'm fairly new to Ubuntu, I know very little, 
so I guess thats why I'm in this section.

Anyways, I really need some guidance with USB permissions and ownership.
I have a 2.0 GB mini SD card that im trying to load files on but I cannot 
delete the trash...

So i was reading a few tutorials and then made things even worse 
imputing commands I really didnt fully take the time to understand.

So heres my issue.

Right now, I cannot mount / unmount the drive
sdb1 - 2.0 

Its registered as user root, and obviously I'm under my own
user name..

so where do I start?

Secondly would be how to enable permissions on the drive so I can
delete the .1000trash folder (named something close to that)

Thanks in advance

Toui

---

### Post by jonathanysp on 2009-08-01
im not exactly sure if this is the best way but the easiest is just to format your USB drive with gparted (get it at add/remove). Format it to FAT32 or smth and afterwards it should be ok. For the .trash folder...its something that comes with nautilus when you delete things in external drives. i havent found a way to stop that but you can try SHIFT+DELETE files, this will completely remove the file instead of sending it to the trash first.

---

### Post by Toui on 2009-08-01
Yeah, I actually thought about this method aswell, 
but for some reason my flash drive wont display in the devices
list in the Partition editor screen.

---

### Post by Toui on 2009-08-01
> **Toui said:**
> Yeah, I actually thought about this method aswell, 
but for some reason my flash drive wont display in the devices
list in the Partition editor screen.

Not sure what changed, I re-logged the user
and the USB is now visible in the gparted.

I'll format, thanks for the help man... I feel pretty foolish for 
such an easy fix.. 

toui

---

### Post by Toui on 2009-08-01
I'm having issues formating the drive itself now, 
I've tried all the formats available, and messed with all the settings, 
but i continue to get the same error.


IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.

I attached a screen shot to show the details.


Any advice?

---

### Post by Toui on 2009-08-01
> **Toui said:**
> I'm having issues formating the drive itself now, 
I've tried all the formats available, and messed with all the settings, 
but i continue to get the same error.


IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.

I attached a screen shot to show the details.


Any advice?

Restarted, tried random things...
Long story short, I formatted it and it works.

thanks dude.

---

