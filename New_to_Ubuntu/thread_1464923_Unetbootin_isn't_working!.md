---
title: "Unetbootin isn't working!"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by stargatefan on 2010-04-28
I created a live USB using UnetBootin, but when I try go to the boot screen and select USB it brings me to a menu with the options Default, Help, and OEM install. at the bottom there is a countdown that says automatic boot in 10, and it goes all the way down and starts over. I have tried every option but nothing happens...


Thanks

---

### Post by Naitsirhc Hsem on 2010-04-28
Unetbootin is very unreliable in my experience.  I would try using System > Administrator > USB Startup Disk Creator.  What OS are you trying to run?

---

### Post by snowpine on 2010-04-28
+1; usb-creator is the recommended method. :)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by wausaubill on 2010-04-28
I just stumbled on this one, so I hope you won't mind if I hijack it a bit.  I have an older computer that I have installed Ubuntu on, which works OK, but I was still wondering if a lighter distro might be better.  To that end, I have been trying a few Live CDs to test things out.

I was thinking of using Unetbootin as a way to stop burning so many CDs.  The machine won't actually boot from a flash drive (too old for that) but it looked like Unetbootin would allow me to try different distros without so much plastic going to waste.

Is there another way to use a live CD ISO on Ubuntu to try out other systems without burning CDs?

Any help would be most appreciated!

Thanks!

Bill

---

### Post by snowpine on 2010-04-28
> **wausaubill said:**
> I was thinking of using Unetbootin as a way to stop burning so many CDs.  The machine won't actually boot from a flash drive (too old for that) but it looked like Unetbootin would allow me to try different distros without so much plastic going to waste.

Is there another way to use a live CD ISO on Ubuntu to try out other systems without burning CDs?

I do not really recommend Unetbootin as mentioned above :) but if you want to experiment with it, Unetbootin has 2 modes: USB and Hard Drive. The Hard Drive method allows you to boot from an ISO on your hard drive by adding a few lines to your GRUB. I've found this method to be hit-or-miss, so always back up your GRUB first, don't do this on your only computer on a day you need to get work done, and if reinstalling GRUB makes you nervous, just burn a CD instead. ;)

May I highly recommend VirtualBox? It lets you try out distros on a virtual machine that runs inside Ubuntu like an application. Bypasses the CD/Unetbootin issue altogether.

---

### Post by wausaubill on 2010-04-29
Yes, I have considered virtual box, however the issue for me would be the fact that the computer in question has about 300Megs of memory and what I am pretty sure is a sloooow CPU.  So, I think it would be difficult to give everything the resources they need to run and give the distros a fair trial.  I may have to break down and spend the $13 to get a new pile of CD-Rs. :-)

Thanks!

Bill

---

### Post by waynefoutz on 2010-04-29
I use unetbootin, but it only seems to work about half the time, especially when you are using an .iso that isn't on the drop down list that unetbootin downloads the iso itself. I've found burning cds on a rewriteable cd a better option for me.

---

### Post by snowpine on 2010-04-29
> **wausaubill said:**
> Yes, I have considered virtual box, however the issue for me would be the fact that the computer in question has about 300Megs of memory and what I am pretty sure is a sloooow CPU.  So, I think it would be difficult to give everything the resources they need to run and give the distros a fair trial.  I may have to break down and spend the $13 to get a new pile of CD-Rs. :-)

Thanks!

Bill

If you start a new thread like "Help me choose a distro for my old slow computer" I guarantee you will get lots of advice... it is a popular topic around here. :)

---

### Post by wausaubill on 2010-04-29
Thanks, SnowPine.  I am sure there are lots of opinions, there are certainly tons of distros to try.  In my travels I found a guy who is selling USB drives with something like 160 LiveCD isos already on it.  Seems a bit excessive, but could be fun.

Thanks!

---

