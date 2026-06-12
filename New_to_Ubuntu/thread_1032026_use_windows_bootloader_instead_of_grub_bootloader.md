---
title: "use windows bootloader instead of grub bootloader?"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Eggbertx on 2009-01-05
I am going to install Ubuntu Intrepid Ibex, but I have a question. I want to use the windows bootloader instead of Grub, from my firends advice. How do I make it my mbr uses the windows bootloader instead of grub but still dual boot windows and ubuntu?

---

### Post by semi_fiction on 2009-01-05
In step 7 of install, go to advanced, and install grub in the /boot folder. If you are dual booting with Vista, download the program EasyBCD (in Windows), and use it to make an entry for Ubuntu in Vista's bootloader.

---

### Post by bodhi.zazen on 2009-01-05
First this is a Linux forum, not a Windows forum so while you are welcome to use the windows boot loader you will not find as much support here as you would on a windows form.

Second, GRUB is easier then the windows boot loader and will be configured by default. You will find more support for grub.

Third you can easily restore the windows boot loader if you need to.

If you still wish to use the windows boot loader see:

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)

---

