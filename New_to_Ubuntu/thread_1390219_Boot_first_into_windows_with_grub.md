---
title: "Boot first into windows with grub"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Malice007 on 2010-01-25
I have a Windows and Ubuntu on a machine and I am running a remote program on the Windows end and from time to time I need to reboot the system but the Grub menu forces the machine to boot into windows if no one is at the desktop to choose windows. Is there a way to force grub to boot to windows first and make ubuntu the second option?

---

### Post by pjones0404 on 2010-01-25
you can edit the file manually... or install a program called startup mamanger and there are settings in there for it.

---

### Post by Malice007 on 2010-01-25
> **pjones0404 said:**
> you can edit the file manually... or install a program called startup mamanger and there are settings in there for it.

startup mamanger for what I read is for windows is this going to modify the grub menu to start right into windows?

---

### Post by oldfred on 2010-01-25
If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find windows entry in this and copy to
gedit /boot/grub/grub.cfg
and copy here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

---

