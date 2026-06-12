---
title: "bootup - USB? Possible?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by mal_conductor on 2010-01-04
Is it possible to make a boot up USB?

I want to set up ubuntu and make a USB key that I can boot up from.

I can boot up from the CD, but I cannot add applications to the CD.  Can I add applications and make a USB key to boot from?

---

### Post by gabo.cr on 2010-01-04
Yes you can.
With the Live CD you can make it.
Under System > Administration > USB Start up Disk Creator.

---

### Post by tom.swartz07 on 2010-01-04
> **mal_conductor said:**
> Is it possible to make a boot up USB?

I want to set up ubuntu and make a USB key that I can boot up from.

I can boot up from the CD, but I cannot add applications to the CD.  Can I add applications and make a USB key to boot from?

Heck yes you can!

The only condition about using a LiveUSB is the fact that your computer *might* not support it.
Check your bios options- When you first turn on your computer, you should see some key combinations flash on the top or bottom corners of the screen, some computers its F12, others its ESC, still more use F10. Once you get in, just verify that you could boot to usb.


I've had lots of success with a program called 'UNetBootin', available in the software center. If you want to make it persistent, there should be some options you could tweak there to make it save any changes you make. Alternatively, you could head over to [www.pendrivelinux.com](www.pendrivelinux.com) and check out their guides- they have some really good how-to's there. Just look for articles talking about casper and casper-rw files- those are the files you need to save your data on the USB.


Hope this helps!

---

### Post by gabo.cr on 2010-01-04
Making it persistent is very important. That will allow you so safe data.

---

### Post by lkraemer on 2010-01-04
Here are three ways to get an older computer to boot from floppy to
a USB Flash device when the BIOS doesn't support it.

[http://linuxgazette.net/116/okopnik1.html](http://linuxgazette.net/116/okopnik1.html)
This script was originally for Knoppix ver 3.7, and I have successfully used it to build a floppy image (using DSL 3.4) with Ubuntu 8.04.3 that
boots to a USB Flash drive with DSL ver 4.4.10 installed by UNETBOOTIN.  I haven't tried using DSL ver 4.4.10 to build the floppy image yet.
Ref: DSL Forum for posting in USB Boot section.

[http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)
This site has several versions for various distros.

[http://www.plop.at/en/bootmanager.html#noinstall](http://www.plop.at/en/bootmanager.html#noinstall)
This boot floppy image also works when the BIOS does not allow for booting
from USB Flash.  Works good on my old Compaq Presario 1672 AMD K6-2 350MHZ

lk

---

### Post by LuisGMarine on 2010-01-04
+1 for Unetbootin.  I have used it in the past many times to install Ubuntu.

---

### Post by networm1230 on 2010-01-05
Yes it is vary Possible to install linux on USB. I am runing off USB right now
I am runing ubuntu 8.04 on USB to install it at is vary easy to do here is how.

1. gat a USB 2 or 4 gig. 4gig up are batter more space to install other apps

2. back up all data from USB to you hard Drive 

Warning: you must dleat every thing from USB drive including the "partition" 
you can use gparted to do this or lat linux do it for you when ask

3. plug in a USB to your pc restart your pc and enter your computers "Bios"
when in the bios go to boot priority and make you optic drive boot first than save chages

warning not all Bios are the same and to enter tham are different depanding on your motherboard

4 encert the live cd. when booting from live cd chose you langueg. than whan ask what to do chose to install not test it

Warning: installing linux on USB taks a Vary log time it toke me some 3 to 4 hours to install linux ubuntu 8.04 without updates. Note! you can get update and install your oun apps from add/remove. that is why I say more space is batter

5. when ask where to install or make a "partition" chose your USB Drive to install it in. when installing do not do anything just lat it install

Warning: Installing linux on USB taks a Vary log time 

6. When install is compleat it will ask you to restart your PC do so when ask it will ask you to remove your cd do so and restart with your USB plug in now you should have linux in your USB drive "compleat"

now you have a portable linux os

---

### Post by wilee-nilee on 2010-01-05
You can also do a full install on a Thumb 8 gigs or more would be best, it is done with live CD like normal but making sure the install and boot record is pointed at the thumb.

---

