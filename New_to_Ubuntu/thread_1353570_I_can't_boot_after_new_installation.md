---
title: "I can't boot after new installation"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by garyed on 2009-12-12
Well exactly what I was worried about happened.
I just installed 64 Studio over my most recent U-studio installation
& now I get error 22 & can't get back into Ubuntu at all.
I made a grub2 boot floppy before I reformatted the partition so i can boot to a grub prompt but I'm stuck there.
Can I issue any command that will put grub2 back & find all my Os's?


Obviously Studio 64 uses grub legacy because i see stage 1 or 2 on the screen before I get the error. 

Here's how I made the grub2 floppy that gets me to the grub prompt: 
> grub-mkrescue --overlay=/boot/grub --image-type=floppy grub2.img
dd if=grug2.img of=/dev/fd0 

Helllllp!

---

### Post by garyed on 2009-12-13
bump

---

