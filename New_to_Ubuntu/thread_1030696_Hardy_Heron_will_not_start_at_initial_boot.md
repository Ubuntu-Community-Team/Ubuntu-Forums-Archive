---
title: "Hardy Heron will not start at initial boot"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by booty_x on 2009-01-04
I have a dual-boot PC with Ubuntu Hardy Heron and Windows XP professional.  When powering on my PC, it will always start Windows correctly from the first time, however it will never start Ubuntu correctly.  When restarting the PC, either out of Windows or by CTRL-ALT-DEL-eting at the hanging Ubuntu splash screen, Ubuntu will start correctly.

When it hangs on the Ubuntu start-up, it hangs on:
'Waiting for root file system...'

My entry for the Ubuntu boot in menu.lst:

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=/dev/sda3 ro splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

Does this sound familiar to anyone and if so - what did you do to get this solved??

Thanks up front!

---

### Post by tomtom1982 on 2009-01-04
Please post the output of

```
sudo fdisk -l
```

in terminal.

---

### Post by booty_x on 2009-01-05
Hi tomtom1982,

The output of sudo fdisk -l:

```
Schijf /dev/sda: 200.0 GB, 200049647616 bytes
255 koppen, 63 sectoren/spoor, 24321 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xea1aa9c7

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        1959    15735636    7  HPFS/NTFS
/dev/sda2            1960       21512   157059472+   f  W95 Uitgeb. (LBA)
/dev/sda3           21513       24321    22563292+  83  Linux
/dev/sda5            1960       21385   156039313+   7  HPFS/NTFS
/dev/sda6           21386       21512     1020096   82  Linux wisselgeheugen

```

This is dutch-language output; just let me know if you need translation of anything.

---

### Post by booty_x on 2009-01-19
Does anyone have any idea on how to get this fixed?

---

