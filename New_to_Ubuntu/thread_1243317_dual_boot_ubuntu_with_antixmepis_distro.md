---
title: "dual boot ubuntu with antixmepis distro"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-08-18
hi
I used the ubuntu live cd to partition my drive so I now have mepis on sda3
I did not install grub when doing the install therefore I believe I have to add something to  my ubuntu grub/ boot menu
how do I find out what this instruction should be?
will I then be able to press esc during grub loading and select the distro I want to use? (I have different home folders but a swap partition)
thanks

---

### Post by mdmarmer on 2009-08-18
Best guess is that you add this to /boot/grub/menu.lst

title MEPIS at sda3, newest kernel
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda3 nomce quiet splash vga=791  
initrd /boot/initrd.img
boot

If that doesn't work, boot from the antix live cd -- there will be an option for "restore grub" in the Mepis System Tools or something similar -- this will restore grub to your Antix install, and it will recognize and set up a selection for Ubuntu as well

Mike

---

