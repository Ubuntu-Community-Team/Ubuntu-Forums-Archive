---
title: "how do i get ubuntu logo to show on boot"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by bac0926 on 2010-03-04
Some how I did something so the now when I boot UBUNTU 8.04 the UBUNTU LOGO and the loading bar no longer show.
When I boot I get the loading Grub..... then I get Starting Up..then nothing until I get the logon screen

---

### Post by swoll1980 on 2010-03-05
If you install startup manager you can fix your problem with a nice pretty GUI interface.

---

### Post by Iowan on 2010-03-05
You could check */boot/grub/menu.lst* to see if kernel options include **splash**.

---

### Post by bac0926 on 2010-03-06
I think this is what you mean. this is the section 


## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

---

