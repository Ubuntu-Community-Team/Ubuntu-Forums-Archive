---
title: "Dual boot Ubuntu and Backtrack 3 from USB"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by sprite-uk on 2009-01-17
Hi. I have previously successfully made my USB pen bootable to BT3 for testing systems at work (I work in reutrns for a computer shop). I love using ubuntu when Im at home an have also made the same pen ootbale to ubuntu again for testing. I was wondering if there is a way of memaking my pen dualbootbale so I can have both of these live OS' running together.

I have installed backtrack to it and then run the make usb starup pen in 8.10. however this doesnt allow me use BT3.

Does anyone know how to make it possible that I can have a grub like interface (like as comes with backtrack) that will allow me to boot into both BT3 and ubuntu (64 bit if possible)?

---

### Post by midnightfox2 on 2009-01-17
You could try making a fat32 partition for the backtrack 3 and leave some unpartitioned space. Then boot the live cd and choose the use largest free space. After that you probably just have to mess around with grub a little to get both booted (or if you're lucky the installer might pick up the backtrack 3 and you have absolutely no hard work to do :D). (I have a usb with ubuntu on it and it runs just great)

---

