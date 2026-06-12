---
title: "yet another dual boot/multi-boot question"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by beew on 2011-01-28
Hi,

I downloaded a Ubuntu 11.04 iso and want to test it on my system. I intend to make a full installation on an external drive so I can test in on different computer.

Now I have an external hdd which already has ubuntu 10.10 and Fedora on it, I am going to make a small partition for 11.04 and use the advanced method of specifying layout. Now I notice that there is no option for not installing grub in the installer. Obviously I don't want its grub to overwrite Ubuntu 10.10's . Maverick is the working system in this setup.

There are three questions.

1) Is this normal that the Ubuntu installer doesn't offer the option of not installing bootloader in advanced installation or is my live usb somehow has a bug? (I wouldn't be surprised as the live usb is quite buggy, none of the buttons on the panel work, drop down menu in installer doesn't work, etc)

2) Suppose I have to install a bootloader, would I be able to easily reinstall grub from 10.10 by booting into it and then run ```
sudo grub-install recheck /dev/sdb
``` ? Assuming of course that grub in NN is not itself corrupt.

3) If grub in NN is corrupt then I am screwed?

Thanks.

---

