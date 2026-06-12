---
title: "dapper grub configuration"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by ifonlyiknew on 2010-06-11
I am trying to install Lucid. I have prepared a bootable USB but dapper wont boot on it, it is just ignoring it.
How do I change grub to allow it to boot on the USB?

Really want to upgrade as I have decided to only use Ubuntu now ;-)

---

### Post by new_tolinux on 2010-06-11
AFAIK booting from USB should be configured in the BIOS, not in Grub.

---

### Post by ifonlyiknew on 2010-06-16
Dapper is not giving me any access to the BIOS????
At the booting, if press ESC, I am only given the option in between the different kernels and the test. No drive selection...

---

### Post by lisati on 2010-06-16
If you want to boot from USB, you need to get to BIOS before grub has a chance to do its stuff. This is usually done by pressing one of your F keys while the computer manufacturer's splash screen is showing. On my laptop it's F12, and on my desktop it's F1. There should be a setting there to let you boot from USB

---

### Post by philinux on 2010-06-16
Mine's the delete key.

---

### Post by new_tolinux on 2010-06-16
F1, F2, F8, F10, F12, CTRL ALT ENTER (at the same time), DEL -> the keys/combinations I know to enter a BIOS. Not every combination works on every BIOS, these are all the different ones I've seen. Most likely there's some message "Press ....... to enter the BIOS" where ...... reveals which key/combination you'll have to press.

F8, F12, DEL, ESC -> the keys I know to enter the BIOS Bootmenu (_not_ Grub!) where you can choose which device you want to boot from. Most likely there's some message "Press ...... to enter the bootmenu" where ...... reveals which key/combination you'll have to press.

I don't claim the lists above to be complete.
Without knowing the brand/type of your computer it's almost impossible for us to say "Press that key to enter the BIOS".
If you don't get a lot of text on your screen before Grub loads, it can be helpful to press ESC, as that sometimes displays the real BIOS bootup screen. In some cases the messages you're looking for are only displayed there and not on the nice bootup screen with only the manufactorer's logo.

---

### Post by warfacegod on 2010-06-16
F2 on my Toshiba. Sometimes it's called System Settings on the Manufacturers Logo screen. When you get into the BIOS, you'll want to go to Boot Order and look for your USB. Mine lists under Hard drives. Yours may be that or Removable Media or *possibly* even CD-ROM (Part of making a LiveUSB is making the jump drive *think* it's a CD.)

I'm a PC. I'm a Mac.
I'm a PC. I'm a Mac.
Well *I'm* a USB jump drive with a personality disorder.

---

