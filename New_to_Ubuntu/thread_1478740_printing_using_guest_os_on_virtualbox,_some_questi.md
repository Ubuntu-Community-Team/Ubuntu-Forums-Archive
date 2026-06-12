---
title: "printing using guest os on virtualbox, some questions... ..."
date: 2010-05-10
forum: New to Ubuntu
---

### Post by techno-mole on 2010-05-10
I have some questions about printing from virtualbox (xp guest os) to a printer connected to ubuntu 9.10.

I tried to get the guest os to see the printer, but it didnt show up anywhere, despite being fine on the ubuntu system (printed out a test page fine)

Is there a specific setting or something you need to adjust in virtualbox ? I tried adding a usb device filter but no dice, so what is the best way to set up printing from a guest os on virtualbox (from the sun/oracle website) on ubuntu (all variants)

Thanks in advance for any help.

---

### Post by Paqman on 2010-05-10
You'll need to hand over control of that USB device from your host (Ubuntu) to your guest (XP). I forget the actual menu items, but at the top of your VM window you should have an option to select USB devices for the guest OS. Obviously you'll then need to install the correct drivers into Windows to get it to work.

---

### Post by techno-mole on 2010-05-10
I see what you mean, but from the usb option in the vm window al the usb devices are grayed out, and I cant select any of them, I assume this is because ubuntu has control over them, so how do you go about releasing that control so that the vm can pick what ever device up ?

Also could the printer be added as a network printer ? even though it is connected to the same machine ? although I did try this with no luck.

Thanks.

---

### Post by Paqman on 2010-05-10
Shut down your VM and check it's settings in Virtualbox, make sure it's set up to use USB.

---

