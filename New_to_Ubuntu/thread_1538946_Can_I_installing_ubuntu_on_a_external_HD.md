---
title: "Can I installing ubuntu on a external HD"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by dfairley on 2010-07-25
Can I install ubuntu on a external HD to learn it before installing on my pc. Or do I have to continue to run it live from the CD?

---

### Post by johnsonfarms on 2010-07-25
Yes definitely. just make sure it is plugged in and when you use the installer it will be available for you to chose from.

---

### Post by dfairley on 2010-07-25
Thanks for the info..... I didn't think I could run a seprate OS on an external....

---

### Post by johnsonfarms on 2010-07-25
Just be cautious of how you install the boot loader. If you install it to the external you won't be able to boot up your computer unless it is plugged in. Make sure the boot loader is on your primary drive and add the external as an option. There are plenty of examples on the google if you need help with it.

---

### Post by JustinR on 2010-07-26
> **johnsonfarms said:**
> Just be cautious of how you install the boot loader. If you install it to the external you won't be able to boot up your computer unless it is plugged in. Make sure the boot loader is on your primary drive and add the external as an option. There are plenty of examples on the google if you need help with it.

Basically what he's saying is when you get to the last step of the install process (where is shows you the summary) click the 'Advanced' button and change the Bootloader location to your external hard drive.

Edit: I assume your running Windows, if so, you can just run WUBI to test out Ubuntu.

---

### Post by PaulReaver on 2010-07-26
I just remove my windows drive when installing to an external drive,  I then use my bios boot menu to select what to boot.

Dirty solution but more reliable than messing with grub.

---

### Post by JustinR on 2010-07-26
> **PaulReaver said:**
> I just remove my windows drive when installing to an external drive,  I then use my bios boot menu to select what to boot.

Dirty solution but more reliable than messing with grub.

Your not messing with grub when you do what was suggested - it's more work to do your solution anyways!

---

