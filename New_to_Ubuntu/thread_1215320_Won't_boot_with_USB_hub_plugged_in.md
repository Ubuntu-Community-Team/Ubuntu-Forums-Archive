---
title: "Won't boot with USB hub plugged in"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Sweaty Elvis on 2009-07-17
Hi all,

I just got done building a computer for the first time, have installed Ubuntu for the first time, and now I'm posting in this forum for the first time.  What a great week it's been!

I have tried searching the forum and can't find an answer to my question.

I have a cheap little card reader/USB hub, a Hummingbird model HCRH2.  It can be seen here[U]: [http://www.lagoom.com/584809/hummingbird-combo-card-reader-and.html](http://www.lagoom.com/584809/hummingbird-combo-card-reader-and.html)
[/U] 
Because of the layout of my work area I want to keep my mouse plugged into this thing.  But Ubuntu will not boot with the hub plugged in!  It stalls after it says "Starting up."  

To boot the computer, I have to unplug the USB hub and plug it back in after reaching the login screen.  This is really annoying.

Any help would be appreciated!

---

### Post by Java Geek on 2009-07-17
Boot into your BIOS when you computer boots up and disable bootup from USB devices.

---

### Post by nhasian on 2009-07-17
see if there is a newer firmware for you bios.  also in your bios there is a boot sequence that you can change.  make sure that HD, SATA or SCSI comes before any USB, USB-Floppy, or USB-HDD lines.  then you shouldnt have any problems.

---

### Post by Sweaty Elvis on 2009-07-17
Thanks for the suggestions.

I went into my BIOS and there is no USB-related stuff anywhere in my boot sequence (see first attached picture).  In fact, the only choices I have for booting are floppy, optical, and hard drives.  Possibly my BIOS doesn't even support USB booting?

How do I go about checking for BIOS updates?  Is updating risky?  My second attached picture has some version information.

Edit: I have done some searching for BIOS update information and this water gets deep very fast.  I'm really a noob with this stuff. 

This is my motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138143](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138143)
This is my CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103471](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103471)

I know this may not really be an Ubuntu issue.  Sorry.

Thanks again for the help!

---

