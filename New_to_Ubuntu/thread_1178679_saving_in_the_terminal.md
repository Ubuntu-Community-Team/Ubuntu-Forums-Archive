---
title: "saving in the terminal"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by silvernitrate on 2009-06-04
how do you save what you did in the terminal like turning off the splash screen

---

### Post by utnubuuser on 2009-06-04
You don't.  You can however make changes to the appropriate configuration file  ie. rc.d.

There are also system modification commands that make permanent changes to yur configuration/modules etc, but you'll want to **know what you're doing before making those changes**.

Google .profile ubuntu, or, profile ubuntu to learn to make changes to an individual profile, such as removing a service from the startup list.

---

### Post by dje on 2009-06-04
I assume you are referring to your [previous thread]("http://ubuntuforums.org/showthread.php?t=1178662")? If so, if you edited /boot/grub/menu.lst then the changes are saved in the file until you change and save again, just like any other document, and the splash will be removed for every boot (unless you get a kernel upgrade in which case you will have to repeat the procedure for the new kernel entry). However if you edited at the grub menu at boot time it will only remove the splash for that boot

dje

---

