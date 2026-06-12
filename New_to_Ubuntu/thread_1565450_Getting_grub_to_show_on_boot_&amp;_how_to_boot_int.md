---
title: "Getting grub to show on boot &amp; how to boot into a command-line"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by lukemk1 on 2010-08-31
So the title gives the basic idea, I'd like to know how to boot with grub showing every time (without holding shift) and I would also like to know how to boot into the command-line form which I could use startx to start up the gui.

Is this easy/possible to do after I have installed Ubuntu 10.04?

---

### Post by andrewthomas on 2010-09-01
> **lukemk1 said:**
> So the title gives the basic idea, I'd like to know how to boot with grub showing every time (without holding shift)You could edit /etc/default grub so GRUB_HIDDEN_TIMEOUT=0 is commented
 
 ```
GRUB_DEFAULT=0
 #GRUB_HIDDEN_TIMEOUT=0
 GRUB_HIDDEN_TIMEOUT_QUIET=true
 GRUB_TIMEOUT=10
```
 > **lukemk1 said:**
> and I would also like to know how to boot into the command-line form which I could use startx to start up the gui.

Is this easy/possible to do after I have installed Ubuntu 10.04?
edit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="single"

and then sudo update-grub

---

### Post by lukemk1 on 2010-09-01
> **andrewthomas said:**
> edit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="single"

and then sudo update-grub

That will make it boot into the command-line from which I can boot into the gui by typing startx?

---

### Post by andrewthomas on 2010-09-01
> **lukemk1 said:**
> That will make it boot into the command-line from which I can boot into the gui by typing startx?
Yes.  You can test it out by pressing e at the grub menu to edit and switching "quiet splash" to "single."

---

### Post by lukemk1 on 2010-09-02
> **andrewthomas said:**
> Yes.  You can test it out by pressing e at the grub menu to edit and switching "quiet splash" to "single."

Awesome, thank you for your help.

---

