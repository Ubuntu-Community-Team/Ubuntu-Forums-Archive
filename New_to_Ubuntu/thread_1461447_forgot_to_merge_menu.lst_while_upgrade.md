---
title: "forgot to merge menu.lst while upgrade"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by George7a on 2010-04-24
Hi,

I have upgrade from 9.04 to 9.10 and forgot to merge the menu.lst, now I am still working on the old kernel.

How do I know my new kernel?
What should I write in the menu.lst so I can boot into the new kernel?

- George

---

### Post by xumuk37 on 2010-04-24
you have to point grub to load kernel you want... you can see all availables in /boot folder. Something like this

kernel /vmlinuz-2.6.32-21-generic root=/dev/disk/by-uuid/uuid_of_ubuntu_partition(or /dev/sdaX) ro
initrd /initrd.img-2.6.32-21-generic

---

### Post by George7a on 2010-04-24
Isn't there an automatic option to merge the current menu.lst with the new one that I forgot to merge with?

---

### Post by xumuk37 on 2010-04-24
if you're using grub2 yes there is... as you start with menu.lst (not grub.cfg) I supposed you was talking about grub v1. 
```
update-grub
```

I'd make a copy of grub.cfg... it may be usefull:
```
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.old
```

---

### Post by cgroza on 2010-04-24
Maybe you can do something with the "startupmanager", i know you can handle kernels there.

---

### Post by George7a on 2010-04-24
I had grub 0.97, I am upgrading it now..

---

### Post by George7a on 2010-04-24
update-grub did not help.. any other advices?

---

### Post by George7a on 2010-04-24
startupmanager showed me whats in menu.lst.. I could not find the new kernel!

---

### Post by ed-koala on 2010-04-24
[http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html]("http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html")

---

### Post by George7a on 2010-04-24
I upgraded grub, followed the instructions and now I get:

> GRUB loading stage 1.5
GRUB loading, please wait
Error 15!

I can not boot now!! what should I do?

---

### Post by George7a on 2010-04-24
I installed the GRUB 2 from the live Cd and now it is working

---

