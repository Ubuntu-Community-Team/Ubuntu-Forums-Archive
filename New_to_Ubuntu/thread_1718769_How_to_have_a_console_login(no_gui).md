---
title: "How to have a console login(no gui)"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by MIKRO402 on 2011-03-31
How can I have the system start with just a login prompt and not gnome?
I would like to add kde and do some command line things right from the prompt.
After I have a login prompt do I just do 'startx'? How do I go about choosing between KDE and Gnome?

Thanks...

---

### Post by MIKRO402 on 2011-03-31
I may have found the answer in GRUB2. Am I to change the following line in' /etc/default/grub' ?

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

---

### Post by MIKRO402 on 2011-03-31
Found the answer here:

[http://www.thecoderanger.com/disable-gdm-at-system-boot-ubuntu-10-10-maverick/](http://www.thecoderanger.com/disable-gdm-at-system-boot-ubuntu-10-10-maverick/)

---

