---
title: "Re-install Ubuntu"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-29
Hi  Want to re-install Ubuntu 8.10 but cannot get system to boot from CD.Just runs through the normal HDD load. Advice please. Thanks

---

### Post by perrti-y02 on 2009-03-29
In the bios you will need to change the boot order so that CD is number 1. This might be under something obvious such as disk management or less obvious such as basic CMOS setup. You get into the BIOS by pressing a key before it gets to the hard drive bit. Usually you need to press F2 or F10 or Del or Esc.

Then let it run as usual with the cd in the drive and all should be wonderful.

---

### Post by thunk77 on 2009-03-29
You have to change the boot order in your BIOS.
Try hitting the Delete (or Esc, or F2) button when your computer boots, this should take you to your computers BIOS settings. Navigate to the "boot sequence" and change the order so that it's 
1)CDROM
2)HARD DISK
3)FLOPPY
or whatever, the important thing is that the cdrom option is first, and presto!

---

### Post by clive littlewood on 2009-03-29
Hi

You need to change your boot order in Bios.

When your system boots you will see a key to press for your Bios (usually esc or one of the F keys)

When you enter Bios look for Boot Order usually on second page.

Use arrow keys to select and move up "Boot from CD"

Save and exit Bios and then try with your CD in the tray.

Hope this helps      :)

Clive

OOps beat me to it thunk77 !!!!!!!!!!!!!

---

### Post by mkvnmtr on 2009-03-29
If you have a dual boot then grub should give you time to choose the cd. If not the bios are the way to go.

---

### Post by thunk77 on 2009-03-29
All good advice Clive!  :)

---

