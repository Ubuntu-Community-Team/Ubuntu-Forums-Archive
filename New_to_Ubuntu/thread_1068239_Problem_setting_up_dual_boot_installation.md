---
title: "Problem setting up dual boot installation"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by smuir00 on 2009-02-12
Hi, I have downloaded the unbuntu 8.10 file and burnt it to disk using the ISO burner, have then installed a partition using wubi and have set up the dual boot on startup. 
The problem I have is after slecting to go into unbuntu is that after 1 min of the unbunto logo being displayed the PC then says: 

Loading, please wait ... 
Busybox v1.10.2 (unbuntu 1:1.10.2-1unbuntu6) built-in shell (ash) 
Enter 'help' for a list of built-in commands. 
(initramfs) _ (and the cursor sits here) 

If I leave the PC for a while it just sits here and does not move, help ? 

If I boot up with the CD in the drive I can load Unbuntu through to the gnome screen as shown in the magazine. 

I am running a standard Dell inspiron 530 with, core 2 processor and 3Gb of RAM. 

Any help with why the loading process stops with the dual boot appreciated. 

Simon

---

### Post by Ripose on 2009-02-12
I'm confused, it sounds like you used Wubi to create a partition and you did not install Ubuntu at that time.

You don't need an install CD if you ran Wubi, it runs from within Windows.

---

### Post by presence1960 on 2009-02-12
I am not sure if your setup is proper. But if it is you want to add this to your Ubuntu selection in your menu.lst file after ro > splash all_generic_ide floppy=off irqpoll 

Mine looks like this 

> title		Linux Mint x64, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb1 ro splash all_generic_ide floppy=off irqpoll
initrd		/boot/initrd.img-2.6.24-16-generic

I had the same problem with Mint and adding the above solved the problem of the boot hanging. It never happend again.

I could not make out for sure if you installed via wubi or actually set up an ubuntu partition. As far as wubi goes I know nada since i have never used it.

---

### Post by smuir00 on 2009-02-13
Hi, thank you for the feedback / suggestion.

Can you please confirm where I would find the file to make the edit suggested ?

Thanks

     Simon

---

### Post by avtolle on 2009-02-13
From looking at the Wubi forum, etc., I'd suggest to the OP that he uninstall Ubuntu through his Windows install; then, checkdsk be run (IIRC, with -r); the HDD be defragged; then, if he wishes, reinstall Ubuntu using Wubi. A common cause of dropping into busy box in a Windows install is a problem with the HDD caused by a "hard" shutdown.

---

### Post by Ripose on 2009-02-13
I use nano to edit these types of files.
From a terminal type sudo nano /boot/grub/menu.lst

Make changes --> [CTRL] O to write out changes --> [ENTER] to use same file filename --> [CTRL] X to exit nano

Reboot

---

### Post by presence1960 on 2009-02-13
Ripose: +1

I still don't know if smuirr00 installed Ubuntu to a partition on his hard drive or used wubi. My suggestion will work if he installed Ubuntu to a partition. I have no idea how wubi is set up or how it works.

---

### Post by Ripose on 2009-02-13
Yeah, I'm not sure what he done either.

WUBI is downloaded AND installed from within Windows.
No CD's, partitioning, etc.

---

