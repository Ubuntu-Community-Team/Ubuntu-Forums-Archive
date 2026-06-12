---
title: "installation dilemma"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by mcstat on 2011-08-04
Hi guys I urgently need some help, I got an hp 4530 with windows 7 and I tried dual booting along side ubuntu 10.04 using usb boot, I formatted the recovery partitions and installed it without any problems. I reboot the pc and it went directly to the windows 7 withou showing the grub and it failed to finish booting the windows 7 (only ended at splash screen). After that it tried to automatically recover and failed and gave the reason why it failed (hardware necessary for booting is missing). Please can somebody help me.

---

### Post by jtarin on 2011-08-04
> **mcstat said:**
> Hi guys I urgently need some help, I got an hp 4530 with windows 7 and I tried dual booting along side ubuntu 10.04 using usb boot, I formatted the recovery partitions and installed it without any problems. I reboot the pc and it went directly to the windows 7 withou showing the grub and it failed to finish booting the windows 7 (only ended at splash screen). After that it tried to automatically recover and failed and gave the reason why it failed (hardware necessary for booting is missing). Please can somebody help me.It sounds as if Grub is installed on your USB and it can not find it to boot.

---

### Post by mcstat on 2011-08-04
Is  there a way of installing the grub on the hard drive without reinstalling the whole operating system?

---

### Post by jtarin on 2011-08-04
On [this page]("https://help.ubuntu.com/community/Grub2#ChRoot") follow the instructions for using CHROOT method for booting to your install and installing Grub. Read carefully and if you have any questions along the way....ask.

---

### Post by mcstat on 2011-08-04
Ok, thank you, will try it out.

---

