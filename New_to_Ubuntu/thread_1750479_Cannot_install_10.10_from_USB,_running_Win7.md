---
title: "Cannot install 10.10 from USB, running Win7"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Katurday on 2011-05-05
I'd like to start with the fact that I'm utterly hopeless at computers but nonetheless have decided to make the switch to Ubuntu. My ASUS Eee PC 1201n is running Win7 currently, and somehow I managed to get the Ubuntu 10.10 installer onto a USB, yet when I turn the machine on with the USB in, and press ESC, it only displays booting into Windows option. :confused: 

I would REALLY appreciate some form of walk through because the guides I've been reading just confuse me. Assume complete computer lingo ignorance, please.

---

### Post by mikewhatever on 2011-05-06
It seems that your computer still boots from the hard drive, even with the USB stick plugged in. You'll have to find the way to access the BIOS to re-configure its boot order. Usually, you have to press a key to enter the BIOS setup,'Del' or f10, or f12.

---

### Post by Katurday on 2011-05-09
> **mikewhatever said:**
> It seems that your computer still boots from the hard drive, even with the USB stick plugged in. You'll have to find the way to access the BIOS to re-configure its boot order. Usually, you have to press a key to enter the BIOS setup,'Del' or f10, or f12.
I've gotten to the BIOS but I haven't a clue on how to re-configure the boot order.

---

### Post by lmarmisa on 2011-05-09
Press Escape several times just after the system boots in order to select the boot device.

Did you use any tool for preparing your Ubuntu Live USB?. I recommend UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Katurday on 2011-05-09
> **lmarmisa said:**
> Press Escape several times just after the system boots in order to select the boot device.

Did you use any tool for preparing your Ubuntu Live USB?. I recommend UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Pressing ESC once gets me to a menu that lets me choose Win7 (no other options) and pressing it many times simply auto-starts Win7. I used [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) and AFAIK, the usb is prepared (when I pop it in after Windows boots, its labeled as the Ubuntu installer.)

---

### Post by wilee-nilee on 2011-05-09
Make sure the thumb is loaded correctly ie unetbootin as suggested works. See this thread as it seems the actual usb port matters, post #2.
[http://ubuntuforums.org/showthread.php?t=1113396](http://ubuntuforums.org/showthread.php?t=1113396)

---

### Post by Katurday on 2011-05-12
> **wilee-nilee said:**
> Make sure the thumb is loaded correctly ie unetbootin as suggested works. See this thread as it seems the actual usb port matters, post #2.
[http://ubuntuforums.org/showthread.php?t=1113396](http://ubuntuforums.org/showthread.php?t=1113396)
Okay, update.
Wiped USB clean, did the procedure with unetbootin.
Went to BIOS, changed settings to boot from USB first.
Made sure USB is plugged into the RIGHT port. Attempted left as well.

No luck. Still boots in windows, doesn't even show the USB as an option. Thoroughly frustrated. I can't believe the "learning curve" struck before I even had/tried Ubuntu.

---

### Post by Quackers on 2011-05-12
Just something else to check.
Have you set the bios boot order so that USB flash drive boots first?
Sometimes (like with one of mine) the bios will recognise a USB flash drive as a USB Hard drive.
Try setting the USB HDD as first boot device and see what happens.
If neither settings show any life it may be that the USB is not bootable for some reason.

---

### Post by Katurday on 2011-05-13
> **Quackers said:**
> Just something else to check.
Have you set the bios boot order so that USB flash drive boots first?
Sometimes (like with one of mine) the bios will recognise a USB flash drive as a USB Hard drive.
Try setting the USB HDD as first boot device and see what happens.
If neither settings show any life it may be that the USB is not bootable for some reason.
There's pretty much only a Hard Disk, a CD, and a usb flash option. I'm not even sure what the CD is for? One last go at it before I consider switching USBs.

---

### Post by Quackers on 2011-05-13
It's possible that there is a setting in your bios to enable external devices. If this setting is enabled other options may show up.

---

### Post by hansolo4949 on 2011-05-13
You may have to boot using a cd. Some older computers cannot boot from a USB device, which is the caveat of using a flash drive to install Ubuntu. I have a six year old laptop (older, actually) which I cannot use to boot from a USB drive. If you do not have a cd drive in the netbook, you can either update the bios, and hope for the best, or install it from within windows, using wubi, which is probably best for newer users, since it keeps windows on the computer,and launches Linux as if it is a program. If that is not the case, please correct me, I am a little rusty, since I really have not done anything like that for a while.

---

### Post by Katurday on 2011-05-13
MISSION ACCOMPLISHED!

Thanks everyone, holy crap it was mostly my stupidity holding me back. I had an SD card plugged in since FOREVER ago, and it affected boot order.

So steps for ASUS 1201n are as follows:

F2 when booting multiple times. Leads to BIOS. Go left to Boot Settings, change Boot order to USB. Re-boot and it SHOULD show the USB. Thanks for the suggestion of Unebootin. Everything is running perfectly now.

---

### Post by Quackers on 2011-05-13
Aha! Good news :-)

---

### Post by astex on 2011-05-13
Have you considered installing through wubi.exe within Windows?  It runs like any other Windows program and installs Ubuntu onto its own portion of the hard disk.

---

### Post by hansolo4949 on 2011-05-13
Good to hear:)

---

