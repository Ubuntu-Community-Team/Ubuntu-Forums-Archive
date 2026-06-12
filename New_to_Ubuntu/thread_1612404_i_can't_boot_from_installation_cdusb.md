---
title: "i can't boot from installation cd/usb"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Kmunky on 2010-11-03
hi, i have just downloaded ubuntu 10.10 32bit, made a bootable cd and tried to boot from it but with no success. 

when i restart my computer with cd in the tray i can't get to the installation screen, it simply won't boot from my cd(like my cd is not bootable). Same thing using bootable usb(followed the steps provided on ubuntu.com)

i have changed boot order(cdrom first,hdd second) but same thing.

any ideas? thanks

---

### Post by yeats on 2010-11-03
> when i restart my computer with cd in the tray i can't get to the installation screen, it simply won't boot from my cd(like my cd is not bootable). Same thing using bootable usb(followed the steps provided on ubuntu.com)

So is it skipping the CD boot and going straight to your regular OS (assuming Windows) or is it giving you some kind of error without moving any further?

Assuming it's the latter and you have extra CDs, you might take these steps:

1. [Verify the image you downloaded]("https://help.ubuntu.com/community/HowToMD5SUM") if you haven't already.
2. burn a new CD and try again
3. if you are able to get the CD to boot, press a key when it starts to boot and select the "check disk for errors" option

You might also consider the [alternate CD]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate") if you're unable to boot into the regular one.

---

### Post by Kmunky on 2010-11-03
It's the first one, it simply skips the boot cd and goes straight to windows( windows 7).

---

### Post by Yougo on 2010-11-03
did you set up your bios to look for a bootable cd, before it boots from harddrive? depending on your machine, pressing CTRL+F12 at boot could also take you to a menu where you can choose to boot from cd.

just to be sure, you did burn image-to-disk, and not just put the *.iso file on a cd? silly mistake, but i managed to make that mistake back at 8:10 :redface::p

---

### Post by Hashiru on 2010-11-03
Hi,
 
I have several computers which don't support USB boot. I can however by using Plop boot manager.
 
Just try their instructions.
 
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)
 
It worked like a charm for me.
 
Good luck!

---

### Post by Kmunky on 2010-11-03
> **Hashiru said:**
> Hi,
 
I have several computers which don't support USB boot. I can however by using Plop boot manager.
 
Just try their instructions.
 
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)
 
It worked like a charm for me.
 
Good luck!

my bios has the option to boot from flash drive. 

> **Yougo said:**
> did you set up your bios to look for a bootable cd, before it boots from harddrive? depending on your machine, pressing CTRL+F12 at boot could also take you to a menu where you can choose to boot from cd.

just to be sure, you did burn image-to-disk, and not just put the *.iso file on a cd? silly mistake, but i managed to make that mistake back at 8:10 :redface::p


i have set boot order from bios(cd,hdd). i have no problem booting from other operating systems cd. I also checked my cd, it works fine under windows( i get that installation screen)

---

### Post by Yougo on 2010-11-03
is it possible to check the cd for errors from a wubi installation (like you can with a boot-from-cd)? even if the cd checksum is good, some files may be broken, preventing the cd from being bootable

other than that, and i'm out of ideas :-\

---

### Post by Hashiru on 2010-11-04
The reason why I posted Plop boot manager is that I could not start ubuntu from the cd. The cd worked at laptops though. Since it couldn't be the cd I tried a different approach.
I installed Plop boot manager on a cd and installed ubuntu from usb. A little bit of a work-a-round, but it worked.

I don't know if it will work in your situation, but if you run out of ideas, it might be worth a try.

---

### Post by alphaamanitin on 2010-11-04
I often find that bios on MOBO are faulty POS.  Even when I set boot order often it will not boot in the order I have set, this is why I have started just hitting F10 (boot options) for my MOBO.  Then I get a screen asking me which device to boot from and that works.  

In fact just last night I had a friend who couldn't get his computer to boot from a Windows 7 install DVD that was turned into an .iso and put on a bootable USB stick.  However, when he went to boot options and told it to boot from a USB, not trusting his changed boot order to work, it did.  

So, try that, I think it is worth a shot before more trouble shooting.

AlphaA

---

### Post by anewguy on 2010-11-04
Here's something simple to check -

(1) did you burn the CD as burning an ISO, or did you just copy the ISO to it?  If all you did was copy, it won't boot, you need to burn it as an ISO.

(2) the same holds true for USB - you can't just copy the file to it.  Use something like netbootln (spelling?) to create the bootable USB image.


Dave ;)

---

