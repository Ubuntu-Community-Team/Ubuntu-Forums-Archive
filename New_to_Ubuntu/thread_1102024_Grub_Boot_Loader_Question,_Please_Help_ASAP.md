---
title: "Grub Boot Loader Question, Please Help ASAP"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-21
Hi guys,
I had Ubuntu and XP dual booting.

Using Grub Bootloader.

I decided I wanted to go back to Vista, so I installed Vista on the partition XP was on (erasing XP's partition first)

After doing this, theres no trace of grub bootloader. I can't boot into Ubuntu anymore.

How do I restore the bootloader, so I can choose between Vista and Ubuntu?

Thanks.

---

### Post by presence1960 on 2009-03-21
> **Gp. said:**
> Hi guys,
I had Ubuntu and XP dual booting.

Using Grub Bootloader.

I decided I wanted to go back to Vista, so I installed Vista on the partition XP was on (erasing XP's partition first)

After doing this, theres no trace of grub bootloader. I can't boot into Ubuntu anymore.

How do I restore the bootloader, so I can choose between Vista and Ubuntu?

Thanks.

Follow this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition nr is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.


```

---

### Post by Gp. on 2009-03-22
Thanks!
Worked...
just one thing...

It now says Windows XP professional as the operating system because I upgraded from XP to Vista...so the value shows up as XP still.


How do I change the name/value to show up as Windows Vista?

---

### Post by sonu 1807 on 2009-03-22
You can edit /boot/grub/menu.lst to change the name to Vista

---

### Post by mlentink on 2009-03-22
Change the name in /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```Go the entry for Windows XP (most likely the last entry in the list) and change the text only to e.g. Windows Vista (or whatver you like, it's just a designator)


Oops

---

### Post by presence1960 on 2009-03-22
> **Gp. said:**
> Thanks!
Worked...
just one thing...

It now says Windows XP professional as the operating system because I upgraded from XP to Vista...so the value shows up as XP still.


How do I change the name/value to show up as Windows Vista?

Just edit the name of Windows in menu.lst : ```
sudo gedit /boot/grub/menu.lst
``` or through nautilus : ```
gksu nautilus
```

Glad you got it working!

---

