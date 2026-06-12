---
title: "Wondering if this is possible"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by dmgash on 2009-02-08
Hello all, im new to the whole linux thing but i wanna try it out so here my question, im at college and have a laptop that currently has vista now i don't wanna go cold turkey and wipe my hard drive and fresh instal ubuntu and i also don't wanna partition the internal hardrive cause of size issues so here is my question;

I have already installed ubuntu on this computer with an USB hardrive 300 gig and i ran into some issues with GRUB bootloader, so that i could not turn my computer on and boot an OS unless i had the external plugged in, so is there any way that i could set it up so that i can load Ubuntu when i have the external hard disk plugged in and then load vista when it is unplugged i know my BIOS the boot priotity can be set up for that i was just wouldnt know if it worked i tried everything last time wanted to see if anyone more knowledgable in the area could help me....

I hope i have been clear enough and im sorry also it seems my post has turned into a block of text

Thanks in advance best regards

---

### Post by bgates on 2009-02-08
You might try, booting into Vista and installing EasyBCD from here: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Then the bootloader will be controlled by Vista and you should be able to boot to either OS whether the USB drive is plugged in or not, after you set it up.

---

### Post by dmgash on 2009-02-08
so....i wouldn't install the GRUB bootloader at all then, so i would boot Ubuntu thru vista and not the BIOS, im just trying to get a grasp on how it works, thanks also for the speedy response! :)

---

### Post by bgates on 2009-02-08
Grub would be there on your Ubuntu installation (or sometimes not, seeing as it's a removable drive) but not used.  The bootloader that is used would be EasyBCD in Vista, on Vista's partition and all.  You would not have to boot Vista to get to Ubuntu or anything like that, Vista would simply control the bootloader instead of Ubuntu controlling it, which in this case would be good since Ubuntu might not always be present.

---

### Post by dmgash on 2009-02-08
Ok thanks! i will try this tomorrow

---

