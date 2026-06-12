---
title: "GRUB startup troubles"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by synicalx on 2010-04-13
Hey all,

Just a quick question - I have Ubuntu on one HDD and W7 on another, both OS's work perfectly however when I boot up GRUB loads itself first and gives me all the usual options. However as I use W7 95% of the time I'd rather use the Windows Boot loader as the primary boot loader - at the moment I have to tell GRUB to load WBL and then tell it too boot W7. What I'd rather be able to go directly into WBL and select Ubuntu from there (as you do with a Wubi installation).

Is that possible/relatively easy? It's not a major problem, I'd just like to be able to hit the power button, walk off and have it load into W7 by itself rather than Ubuntu.

EDIT: Ugh how embarassing, just found an article with google, first result on page 1 and I missed it....

/thread

---

### Post by oldfred on 2010-04-13
There are ways but I do not recommend them. Look at easyBCD. 

You can change the default in grub to auto boot the windows partition.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

Or the quick graphical way, although earlier someone had it add additional setting for VGA= which are obsolete.
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

---

