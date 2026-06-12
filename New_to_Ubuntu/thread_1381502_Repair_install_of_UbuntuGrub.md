---
title: "Repair install of Ubuntu/Grub?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Devilham on 2010-01-14
Long story short, I had to run fixboot and fixmbr on my dual boot XP/Ubuntu machine (each on their own hard drive), and that had the intended effect or repairing my XP bootloader, but it removed GRUB.  Is there a repair install that I can run, or something quicker than a full re-install of Ubuntu?  I will take my answer off the air (snicker).

---

### Post by tom.swartz07 on 2010-01-14
> **Devilham said:**
> Long story short, I had to run fixboot and fixmbr on my dual boot XP/Ubuntu machine (each on their own hard drive), and that had the intended effect or repairing my XP bootloader, but it removed GRUB.  Is there a repair install that I can run, or something quicker than a full re-install of Ubuntu?  I will take my answer off the air (snicker).

Follow the link in my signature. Post back if you have any questions.

Its fairly straightforward.

Hope this helps!

---

### Post by Devilham on 2010-01-15
Ended up doing the re-install anyways, and when finished GRUB again did not recognize that Windows was installed on the other HD.  I have done a few things suggested to get GRUB to see it, but no dice.  I think part of the problem is that when I am in Ubuntu, that drive (the XP one) has issues mounting.  I get an error 13, and it suggests that I run fdisk, which I did last night (took FOREVER).  Odd thing is, is that every once in a great while, the drive WILL mount, weird huh?  Anyways, does GRUB need to be the bootloader, if I repair the XP bootloader, and then edit the boot.ini to include Ubuntu, would that be kosher?

---

### Post by rahulkumarc on 2010-01-15
Devilham - Adding ubuntu to boot via windows boot.ini is also possible and an option.

please see this post > [http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

it requires you to boot via the liveboot cd and get a copy of the first 512 bytes of your ubuntu hard disk[I would suggest on a usb pen drive] then coping it on c: and haveboot.ini point to it.

Its pretty simple and straight forward, I did use this long back, but I have not needed to use this often.

---

### Post by Devilham on 2010-01-15
Nice, can't wait to get home and try that!   This has been very frustrating, and I really want to get in there and use and learn Ubuntu, I wiped my Vista off that partition to do just that...what a horrible OS that was, just when I thought ME was the pinnacle of awful, along came Vista!

---

