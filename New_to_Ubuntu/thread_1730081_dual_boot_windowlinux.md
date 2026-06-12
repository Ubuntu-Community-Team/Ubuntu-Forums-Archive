---
title: "dual boot window/linux"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by union12011 on 2011-04-15
My computor is a HP laptop
I know nothing
How do I find, access, implement, and use the windows
that is installed somewhere in front of me
Need it to run two programs that only run
in windows, lego nxt and icamDVR2
You can laugh but try and explain as if dealing
with a seven year old
I boot up in Ubuntu and all other software was
set up by a mentor that moved away

---

### Post by Locke_99GS on 2011-04-15
Hopefully Windows is still installed. Reboot the computer, and when you see something about "GRUB Loading" or something of that sort, hold down the shift key. You should be presented with a menu. If Windows is installed and detected by GRUB, it'll probably be the last item on the list. 

If Windows is not on that list, open a terminal and give us the output of this command:
```
sudo fdisk -l
```

---

### Post by union12011 on 2011-04-15
[sudo] password for linsay:  this was the reply to sudo fdisk -l
my mentor only gave me one password 
And it will not input as it is numerical
attempting option 1 now

---

### Post by jtarin on 2011-04-15
Your password should input as numerical. Does your numlock key come on at the point you need it?

---

### Post by union12011 on 2011-04-15
Would not input numerals in terminal HP has funny numloc
but looked up in manual and regular and numloc numbers would not input
On restart hit f9 and it came up
                        SELECT BOOT DEVICE
             Notebook: MultiBay
             Notebook: Hard Drive


   f10=ROM Based Setup

Also tried Shift on restart and it just opened in Ubuntu

---

