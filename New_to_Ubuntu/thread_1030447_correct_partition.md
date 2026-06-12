---
title: "correct partition"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by daniz70 on 2009-01-04
Hi
i would like to get suggestions about a correct partition..
here is my HD from gparted...i would like to keep xp and lnx only 
if possible would like to delete the other linux partitions and keep DUAL BOOT 
THX a lot

---

### Post by homemadejam on 2009-01-04
erm, okay... I don't really get what you are asking here.
Just delete the ones that you do not need, then re-size your Windows & Linux partitions to fill up the space...?

Jam

---

### Post by rolnics on 2009-01-04
Do you have a /home partition? If not, which looking at the picture I would assume not, then do as homemadejam said.

---

### Post by Elfy on 2009-01-04
It depends where you are booting from as to how easy it is. If one of the linux partitions controls the bootloader then deleting the partiton will mean you need to reinstall it.

Simple enough to do with either a livecd or supergrub. If windows controls the boot thenI have no idea.

A little more information might help people help you.

If you want to resize sda5 then you will need to resize the extended partition beforehand.

---

### Post by daniz70 on 2009-01-04
excuse me but from live cd and g parted i just format the partitions that i do not want? do i have to format i ext3?

---

### Post by Elfy on 2009-01-04
Formatting will remove data that already exists - so if that's what you want then yes.

There are some other linux filetypes available in gparted, but ext3 is the type ubuntu defaults to.

---

