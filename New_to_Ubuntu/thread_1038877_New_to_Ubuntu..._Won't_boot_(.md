---
title: "New to Ubuntu... Won't boot :("
date: 2009-01-14
forum: New to Ubuntu
---

### Post by lowe0292 on 2009-01-14
Had vista installed. Set up dual boot with grub. Both booted just fine. Used the update manager in ubuntu to update programs and such (i believe it downloaded like 300 things). Anywhom, after updating things, system required a reboot. When i select the Ubuntu with grub it starts to load then i get a black screen with a blinking cursor in the top left corner. Tried ctrl alt f1 and startx after searching forums but it didn't work...

Please help. :(

---

### Post by ianhaycox on 2009-01-14
Does it boot using the recovery option in Grub ?

---

### Post by PriceChild on 2009-01-14
As ianhaycox suggested, when your computer starts up, 'grub' the boot loader presents a choice of kernels to boot. It looks a little like this: [http://i3.photobucket.com/albums/y71/Cocasoca/grub.jpg](http://i3.photobucket.com/albums/y71/Cocasoca/grub.jpg)

Try changing the hilighted choice to the 3rd line (the second line without "recovery") and pressing enter then telling us if that helps.

---

### Post by stevoo on 2009-01-14
you may have downloaded an kernel that is not stable and has caused you system to behave as such. 

Try what Price has said. If it works then remove the newest kernel you have from Synaptic

---

