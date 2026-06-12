---
title: "Making bootable USB drive in ubuntu"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Santosa on 2009-12-20
Hi My friend needs to install ubuntu on his netbook but I can't seem to figure out how to make my USB drive bootable to install it, i came across a page on the ubuntu site talking about using usb creator to make it bootable but when i run the command to install it i get an error saying the package cannot be found :(. Does anyone know another way to make my device bootable?




Paulo, thanks.

---

### Post by orlox on 2009-12-20
How did you try to run the usb creator? You can open it from the menu in system->administration->startup disk creator.

Also, what is exactly the error you get?

---

### Post by laidback on 2009-12-20
First of all you need to be sure that the bios on the pc (notebook) can be adjusted to make the USB HDD (memory stick) bootable. You can enter the bios at boot time (just after you switch on) by pressing Del, F1 or perhaps Esc. It should tell you on the front page. 

Then when you are in the bios navigate to the boot sequence section (location varies from machine to machine) and make the USB HDD (or similar) boot before the standard HDD. You could end up with USB HDD, DVD, HDD as your sequence. 

I've used the System>USB Startup Disc Creator option in 9.04 to good effect. If you haven't got it load via Synaptic. Note I'm using v9.04.

---

