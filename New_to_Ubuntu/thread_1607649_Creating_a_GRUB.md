---
title: "Creating a GRUB"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Robert Buckmaster on 2010-10-28
Hi.

What is the easiest way of making a GRUB, so that I may choose between Ubuntu and Puppy on booting?

---

### Post by garvinrick4 on 2010-10-28
> **Robert Buckmaster said:**
> Hi.

What is the easiest way of making a GRUB, so that I may choose between Ubuntu and Puppy on booting?
grub is in the installation and it is put into the mbr of drive and looks in the installation partition for grub. (put in sda and looks for in sda1 or sda5 or whatever it is in) but grub
always go's in sda that way it finds its way into the mbr (master boot record).
 There is a free pdf book in my signature download it and keep it handy.

---

### Post by Robert Buckmaster on 2010-10-28
I clicked on both the links but couldn't find the information I need. But I downloaded the PDF and it will probably come in handy. So thank you.

I should explain. At the moment I have both Ubuntu and Puppy installed. On booting the computer automatically opens Ubuntu; there is no Grub to enable me to choose. So I want to create a GRUB with both operating systems as options.

I tried using Startup Manager, but it wasn't helpful

---

### Post by Hatsune Miku on 2010-10-28
> **Robert Buckmaster said:**
> I clicked on both the links but couldn't find the information I need. But I downloaded the PDF and it will probably come in handy. So thank you.

I should explain. At the moment I have both Ubuntu and Puppy installed. On booting the computer automatically opens Ubuntu; there is no Grub to enable me to choose. So I want to create a GRUB with both operating systems as options.

I tried using Startup Manager, but it wasn't helpful

Do this my friend :D

Make Sure puppy linux is already installed. Now boot into ubuntu open up your Terminal and type this in :)

```
sudo update-grub
```


This will have Grub look for new Operating systems and add it to the boot list. Hope this works for you :)

---

### Post by Robert Buckmaster on 2010-10-28
Thanks! That worked perfectly.

There is only small matter of renaming 'Unknown Linux Operating system' to 'Puppy 5.1.1', but I am satisfied.

---

### Post by Hatsune Miku on 2010-10-28
No Problem! :) Mak your thread as solved please!

---

