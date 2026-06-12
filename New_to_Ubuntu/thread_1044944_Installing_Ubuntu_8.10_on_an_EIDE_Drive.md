---
title: "Installing Ubuntu 8.10 on an EIDE Drive"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by jets333 on 2009-01-19
Hello All,

I am new to the Ubuntu scene and am stuck with a problem. I am trying to install Ubuntu 8.10 on an IDE drive (40 GB). I also have Windows XP installed on a separate IDE drive(300 GB). How can I set up my system so that when I power up, it gives me the option to either boot Ubuntu 8.10 or boot Windows XP? Thank you very much.

~jets333

---

### Post by anjilslaire on 2009-01-20
Simply boot the Live CD and run through the installer. When it asks where to install, point it to the 40gig drive, not the 300gig Vista drive and continue on. During the installation it will install GRUB which will manage your dual-boot loader and provide you with a choice of OSes.

---

### Post by jets333 on 2009-01-20
How do I need to set up the master/slave stitches on the hard disks?

---

### Post by Idaho Dan on 2009-01-20
jets333,
I installed just like you want to. Windows on one hard drive and Ubuntu on another one.
I have Windows on the first drive, left it master.
Hooked up the second drive,made it slave and installed Ubuntu on it.
I'm no expert, but it worked just fine for me.

---

### Post by jets333 on 2009-01-20
But the last time I tried that, it autobooted to Ubuntu and I had no option weather to boot to XP or Ubuntu. What would be the solution to this?

---

### Post by alphacrucis2 on 2009-01-20
> **jets333 said:**
> But the last time I tried that, it autobooted to Ubuntu and I had no option weather to boot to XP or Ubuntu. What would be the solution to this?


Maybe grub was installed on the 40GB drive. You could try changing the boot order in the BIOS and see what happens if it tries the 40GB drive first.

Sorry I didn't read you post properly. Please ignore doh!

---

### Post by jets333 on 2009-01-21
Ok,

But now I cannot see my second drive at all. I tried to  change the boot order in BIOS, but the D: Drive is not even listed. How can I correct this problem.

Again

320 GB Windows XP IDE Drive (Master)
40 GB Ubuntu 8.10 EIDE Drive. (Slave)

---

