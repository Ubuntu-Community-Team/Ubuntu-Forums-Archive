---
title: "Grub Error 17 - I do not have a CD drive"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Canadaboy on 2008-12-13
Hey everyone,

After successfully installing Intrepix Ibex on my Lenovo X61 tablet, I tried changing the grub splash screen and after some fidgeting I restarted my computer and got a Grub load error.

I then got a copy of Hardy Heron and put it on my USB key using UNetbootin and reinstalled Ubuntu (Hardy Heron) and now when it boots into **grub I get Error 17.**

I cannot run any Live CD / Windows recovery CD** because my computer does not have a CD drive.**

How can I fix this?

Thanks. :guitar:

---

### Post by tomtom1982 on 2008-12-13
Well, you could try SuperGrubDisk.

You'll find the usb-stick version here:
[http://forjamari.linex.org/frs/download.php/1123/super_grub_disk_english_usb_0.9766.tar.gz](http://forjamari.linex.org/frs/download.php/1123/super_grub_disk_english_usb_0.9766.tar.gz)

Here is discription how to make the stick:
[http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB).

And here is how to boot:
[http://www.supergrubdisk.org/wiki/SGD_Howto_Boot](http://www.supergrubdisk.org/wiki/SGD_Howto_Boot)

---

### Post by caljohnsmith on 2008-12-13
Do you get the Grub error 17 before seeing a Grub menu, or before seeing the text "Press ESC to see menu", or do you get the error after selecting an OS in the Grub menu? How about booting your Ubuntu USB drive, open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
```
Note that "-l" is a lowercase L, not a one. That will help clarify your setup.

---

