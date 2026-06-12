---
title: "Permanent changes in file /boot/grub/menu.lst"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by VictimsOfGoatRunner on 2010-02-22
Hi, this weekend I revived my old and useless laptop with ubuntu and now it works very well. However, when I installed I had to use the bootparameters to make it work and every time I start my computer I have to re-enter them to make ubutu launch correctly. 

On the webbpage It says that I should make changes in the file /boot/grub/menu.lst
So far I have failed and I need help, the parameters I'm using is: noapic nolapic irqpoll acpi=off  and last but not least; lapic pci=routeirq

I appreciate the help

---

### Post by Ozymandias_117 on 2010-02-22
Are you using Ubuntu 8.04 or 9.10? (Or something else?) 8.04 uses Legacy Grub, and 9.10 uses Grub 2.

---

### Post by VictimsOfGoatRunner on 2010-02-22
ubuntu 9.10 :D

---

### Post by Ozymandias_117 on 2010-02-22
Pretty sure you need to make your changes to /etc/default/grub then run update-grub when you're done.

---

### Post by VictimsOfGoatRunner on 2010-02-22
okey, since i'm new to this

shoud I add the boot parameters here:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

And BTW, how do I update GRUB?

---

### Post by VictimsOfGoatRunner on 2010-02-22
p.s It doesn't seem to want to save:(

---

### Post by r-senior on 2010-02-22
Did you use sudo to edit /etc/default/grub? You need system privileges.

In a terminal:

$ sudo gedit /etc/default/grub
$ sudo update-grub

---

### Post by Miljet on 2010-02-22
> sudo gedit /etc/default/grub

That should be ```
gksudo gedit /etc/default/grub
```

---

### Post by VictimsOfGoatRunner on 2010-02-22
thanks allot, so far it's working. But where do I apply the boot parameter changes?

---

### Post by _khAttAm_ on 2010-02-22
after you are done editing /etc/default/grub, launch the terminal and then execute sudo updategrub. That should do.

---

### Post by VictimsOfGoatRunner on 2010-02-22
Thanks everyone, think I managed to solve it

---

