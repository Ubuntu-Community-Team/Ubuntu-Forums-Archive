---
title: "Change boot order in GRUB"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by richlatham on 2008-12-13
Hi
I've installed UBUNTU 8.10 on a 2nd drive. When my PC boots, grub gives me various boot options for Ubuntu, plus one for Windows XP. Is it possible to change the order of thse options so that XP is the default?
Thanks

---

### Post by taurus on 2008-12-13
Yes.  Just change the _default_ value from 0 to whatever the entry for windows.  Remember, each **title** is counted as 1 and you start counting from 0.  In other words, the first title is 0 and the next title is 1, etc.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by richlatham on 2008-12-13
Hi
Thanks for the info, but where do I type in the command, is it from within Ubuntu? I don't think it can be.
Thanks

---

### Post by fubbleskag on 2008-12-13
press Alt-F2 to open the "Open Application" prompt and paste that command into it

this will open an editor to change the file with the appropriate permissions to save it. this file is read upon boot, so you once it's saved just reboot.

---

### Post by rlunger on 2008-12-13
> **richlatham said:**
> Hi
Thanks for the info, but where do I type in the command, is it from within Ubuntu? I don't think it can be.
Thanks

Yes you can.  You can edit your GRUB 'menu.lst' file from within Linux (/boot/grub/menu.lst).  GRUB doesn't access this file until the next time your computer boots.

---

### Post by Michael.Godawski on 2008-12-13
The commands are run through the terminal: Applications > Accessories >Terminal

The command

```
gksudo gedit /boot/grub/menu.lst
```

 consists of three parts; gksudo give you the root rights for a graphical application, gedit is the applications, and /boot/grub/menu.lst is the path to the file we want to edit.

---

### Post by taurus on 2008-12-13
Applications -> Accessories -> Terminal

---

### Post by richlatham on 2008-12-13
Hi
Many thanks to all for the help and advice. It worked.
Cheers

---

