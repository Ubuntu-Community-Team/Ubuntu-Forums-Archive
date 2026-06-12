---
title: "How to create a live CD with static IP &amp; needed printer?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by ubuntu1sttimer on 2010-10-20
Looking for information on how to create a live Ubuntu 10.10 CD that comes up configured with a fixed IP address and is set up to work with a Samsung ML-2010 printer. 

Any instructions on how to create it or where I can find instructions that someone that has limited command line experience can follow.

---

### Post by trikster_x on 2010-10-21
[http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/")

This should be a good starting point.  Unfortunately they are both windows programs.  I couldn't really find any way to make a persistent live usb using ubuntu, which is what you need for what you are doing.  I have looked into building a live cd from scratch, and it is completely not worth the effort when tools like the above exist and are free.

---

### Post by baddnady23 on 2010-10-21
Check out remastersys... I think that it might be able to do this, although I'm not sure about the static IP, but I think it would be worth looking into.

[http://www.geekconnection.org/remastersys/]("http://www.geekconnection.org/remastersys/")

---

### Post by coffeecat on 2010-10-21
> **trikster_x said:**
> I couldn't really find any way to make a persistent live usb using ubuntu, which is what you need for what you are doing.

Just use System > Administration > Startup Disk Creator. This creates a live USB with persistence if you select the "stored in reserved space" option. It will store network-manager settings for wireless so it *should* store NM settings for a fixed IP address, although I haven't tried this. It should also remember the printer settings as it remembers every other setting I've tried when I used it.

---

### Post by ubuntu1sttimer on 2010-10-21
Thanks for the good ideas. Was not aware of being able to use windows to create a live disk or stick for Linux. Not my first choice, using windows to make a Linux disk but then, if it works that is what I need. Also had not noticed the System/Admin/Start up thing before. They keep adding things. Will have to look over these options.

Can't try these this evening but will tomorrow and advise back on how it worked.

---

### Post by beew on 2010-10-21
> **coffeecat said:**
> Just use System > Administration > Startup Disk Creator. This creates a live USB with persistence if you select the "stored in reserved space" option. It will store network-manager settings for wireless so it *should* store NM settings for a fixed IP address, although I haven't tried this. It should also remember the printer settings as it remembers every other setting I've tried when I used it.

Definitely works, I have done it many times. I wonder why that is not more widely advertised or known so that many people think that the only way to make live usb in Ubuntu is unetbootin(no persistence) and if they need persistence they would have to go to Windows. You will definitely get that impression from pendrivelinux.com as almost all its tutorials are Windows only.

The only problem with startup disk creator is that it only creates  Ubuntu live usbd. If you want to make live usb for other distros (with persistence) in Ubuntu multiboot is a great tool (it does more)

[http://www.webupd8.org/2010/03/how-to-create-multiboot-liveusb-using.html](http://www.webupd8.org/2010/03/how-to-create-multiboot-liveusb-using.html)

---

### Post by trikster_x on 2010-10-22
I was wondering the same thing when I was searching for the persistent live usb tool the other day.  Every piece of Ubuntu documentation I read never mentioned a persistence option on the usb creator.  There was only a passing notation in the official docs about an older version that had a bug when creating a persistent live usb, but had no instructions on how to make a live usb persistent.  That's why I had assumed only the windows live usb software had the capability.  I guess the devs assume that if you are using Ubuntu, you won't really have a reason to create a persistent device, so it is not worth mentioning you can.

---

### Post by ubuntu1sttimer on 2010-10-25
Tried out the System / Admin / Startup Disk Creator USB maker. Made what appears to be a usb version of the live CD. Was looking for a version that does not include an install option. Also, was unable to get a static address to work. Will have to work on it some more.

What I am after is a USB version of Ubuntu that web serfs and prints with maybe email. Nothing else is needed. Just a lean and mean version that allows for access to the net for purchases and such but leaves no information on the computer hard drive or on the USB.  

Will have to keep working on it. Seems like someone must already have it but so far have not found it.

---

### Post by trikster_x on 2010-10-26
so you basically want a minimal distro capable of private web browsing, print service and nothing else?  That may be a bit harder to come by than you think.  You are kinda going into the custom kernel territory looking for something like that.  Best bet is to learn how to make a custom live cd based on Ubuntu, strip it down to just the stuff you want and install it to a thumb drive.  Maybe Lubuntu would work for you?

---

