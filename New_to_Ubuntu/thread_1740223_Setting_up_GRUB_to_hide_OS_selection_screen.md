---
title: "Setting up GRUB to hide OS selection screen"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by atirox on 2011-04-26
I can't seem to get GRUB to do what I want it to... I keep trying to get GRUB to default boot Windows XP, but also hide the OS Selection screen unless I hold down the SHIFT key on the keyboard. This was easy enough to do using GRUB legacy. However, now that GRUB has been updated, I can't seem to get it to hide the OS selection menu.
Can someone give me a few pointers on how to do this?

---

### Post by pi3.1415926535... on 2011-04-26
I think that GRUB Customizer and StartUp-Manager have options for this.

---

### Post by cipherboy_loc on 2011-04-26
This is copied and pasted from my /etc/default/grub:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
I think you need to change the GRUB_DEFAULT line to the windows xp's place in the menu (0 is the first one, etc).

EDIT: It appears to have been modified from what it should be to hide the menu, but the menu still gets hidden. Odd.. 


Cipherboy

---

### Post by Mark Phelps on 2011-04-28
The problem with changing the default number is that every time you do a kernel update, that number changes -- and you have to go back through this whole set of changes again.

Using Startup-Manager, you can make this change -- and it sticks.

---

