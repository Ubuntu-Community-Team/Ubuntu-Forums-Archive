---
title: "(Another) Grub2 question!"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Paul T. on 2010-01-05
I've just installed Ubuntu onto a friends netbook to replace the original Xandros OS. On boot up, I get the 'Grub Loading' message, but it then goes straight into Ubuntu without showing the grub menu. Is this normal when Ubuntu is the only OS?

---

### Post by audiomick on 2010-01-05
Yes.
I am assuming that you have installed a 9.10 Ubuntu. It will be using grub2.
If you want to see the menu, you need to press "ESC" [COLOR="Blue"]edit: not "ESC", "SHIFT". [/COLOR] at the right moment during boot whilst it is showing "grub loading". Having said that, I wanted to do just that when I booted this morning and couldn't find the moment. I've done some upgrading recently, and what I see during the boot sequence has changed...

Have a look at this
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
for info about grub2.
for your question, particularly the link to the Startup manager and the bit in the "configuring" section about "grub hidden" and "grub hidden quiet"

---

### Post by Paul T. on 2010-01-05
Michael,

thx for info, much appreciated. :)

---

### Post by Paul T. on 2010-01-05
Dumb Question.... :confused:

I've edited the etc/default/grub file as per link above, but how do I save the changes?

---

### Post by audiomick on 2010-01-05
Hi.
Not dumb.
you need to have opened the file in and editor with root privileges.
```
gksu gedit /etc/default/grub
```
will do it, whereby "gksu" is the command to run a graphical application with root privileges, "gedit" is the (graphical) editor, and /etc/default/grub is the path to the file.

Open it like this, do your changes, and you should be able to save without a problem.

---

### Post by Paul T. on 2010-01-05
Success, many thx again.
Another lesson learned :)

---

