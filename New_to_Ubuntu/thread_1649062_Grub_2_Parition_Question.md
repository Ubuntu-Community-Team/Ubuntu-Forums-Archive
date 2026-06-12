---
title: "Grub 2 Parition Question"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-19
Right now i have GRUB2 installed. I have a hidden Partition on my computer called PQSERVICE.  It is a acer recovery partition that is hidden. What i want to do is boot to that recovery parition, however it doesnt show up on GRUB2.  How do I go about accessing that partition?

---

### Post by coffeecat on 2010-12-19
If you install Gparted (or run it from the live CD session) you can unset the hidden flag. In Gparted, select the partition and then Partition > Manage Flags. Once you've unset the hidden flag, simply run this from a terminal (not in the live CD):

```
sudo update-grub
```And that (hopefully) will pick up the recovery partition and add a grub entry for you. Post back if it doesn't and we can investigate further.

---

### Post by hunter99507 on 2010-12-19
I clicked manage flags but none were hilighted.  Is their something else i can do to boot to that PQSERVICE

---

### Post by alzie on 2010-12-19
Try <alt>+F10 during the boot sequence.  If you are dual booting you can do it at any time during a windows session.

---

### Post by hunter99507 on 2010-12-20
I have been doing some research and my acer computer and the alt + f10 is not working. I made sure to turn it on in the bios and it still doesnt work.  From reading, it says I have to press alt + f10 at POST.  I tried that but it didnt work.  Also i read that the acer MBR has to be installed in order to use the alt + f10.  Right now i have GRUB2 installed under Easy BCD, so i diffidently overwrote the MBR.  Is their a way grub and recognize my PQSERVICE so i can boot to it?

---

