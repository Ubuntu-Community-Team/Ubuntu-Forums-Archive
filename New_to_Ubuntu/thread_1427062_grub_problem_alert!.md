---
title: "grub problem alert!"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-03-11
I was going to sell my acer aspire computer and decided the buyer did not need ubuntu as I use it all the time so I decided to wipe ubuntu off. So i did resulting in me commiting a very scary mistake and I think all my data has gone off my computer :o

Please help me as it comes up with grub rescue > and I do not have any vista recovery cd's or anything. is there anyway to bypass this or even better delete grub?

I buyer needs it by friday!


Its an acer aspire win vista 160gb 2gb ram!

All help much appreciated!

(just wondering if u guys had any commands to disable this annoying thing!")

Thank you!!

---

### Post by bumanie on 2010-03-11
Go [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and download the repair disk - it should repair vista's bootloader and mbr for you, as long as vista has been untouched otherwise, vista then should boot as grub will be removed.

---

### Post by vnpifhf on 2010-03-11
i do not have a cd drive on my spare computer and my usb... thats a different story altogether :D:D

any other ways  like disabling grub?

---

### Post by bumanie on 2010-03-11
Which version of ubuntu are you using? And which version of grub? Also can you boot an ubuntu live cd and post the output of > sudo fdisk -lThe restore partition may well be in tact - and if you are selling the computer I would certainly want to overwrite everything with a fresh install via the restore partition.

---

