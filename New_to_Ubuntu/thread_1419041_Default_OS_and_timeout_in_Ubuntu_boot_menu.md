---
title: "Default OS and timeout in Ubuntu boot menu"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Alex Farber on 2010-03-01
I installed Ubuntu 9.10 on the computer with existing Windows XP. Now I have boot menu with number of options, default is Ubuntu, and XP is the last option. How can I set XP as default option? Is it possible to change also timeout?
I already made search and found information about /boot/grub/menu.lst editing, but I don't see this file on my computer:

alex@alex-linux:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

---

### Post by MelDJ on 2010-03-01
find and install startup-manager from software CENTER

---

### Post by philinux on 2010-03-01
+1 for startupmanager.

9.10 uses grub2 there is no menu.lst. Click the grub2 link below.

To install startupmanager click the link.

[install sum]("apt:startupmanager")

---

### Post by natravis on 2010-03-01
The file you should be editing is /etc/default/grub as root.
```
gksudo gedit /etc/default/grub
``` or ```
sudo nano /etc/default/grub
```

Run sudo update grub2 afterwards to create the new file. See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for more info.

---

### Post by DirtyBeets on 2010-03-01
menu.lst is not used anymore.

If you want to manually edit Grub boot options you can edit ```
/etc/default/grub
```

Or download the manager to do it through a gui.

---

### Post by Alex Farber on 2010-03-02
Solved by installing Startup Manager. Thank you.

---

