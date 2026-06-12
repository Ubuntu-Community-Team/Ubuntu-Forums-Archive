---
title: "Hang on boot - cannot find sda3"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-03-18
I have put together a multiboot with Partition 1 = DOS, Partition 2 = XP, Partition 3 = Ubuntu 8.1 Server. This is using GRUB4DOS. It works quite well. This is on a 100g IDE (PATA)  drive. 

Now I want to add a drive for data so I take a blank SATA drive and attach it to the sata card. Boots DOS and XP as expected. Trying to boot Ubuntu it hangs with the info that it cannot find SDA3.

So I put the image on a SATA drive and everything works as expected. Boots DOS, XP and UBUNTU just fine. Then when I attach a second SATA drive It works fine. Or, I can attach a blank PATA and all is fine. As it should be.

So only failure is attaching a drive (blank or formatted to the SATA card when booting from PATA. This will do the same thing when the PATA drive contains on a single partition (no multi boot) of Ubuntu on a PATA drive. 

What is causing this? DOS and XP always boot and the problem only occurs with Ubuntu.:confused:

---

### Post by Al Fischer on 2009-03-19
I would really like to understand this and maybe an approach to fixing it.

---

