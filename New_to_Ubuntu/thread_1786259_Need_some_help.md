---
title: "Need some help"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-19
I am currently running Xubuntu 11.04 and i would like to dual boot Xubuntu with Tiny Core 3.7. I have a 160GiB hard drive and thought i could give Xubuntu 130 GiB, and Tiny Core 30 GiB. The problem is i don't know how to dual boot two different operating systems. Is there anyone who would like to help me please?

---

### Post by akand074 on 2011-06-19
All you have to do is install them both on separate partitions. Ubuntu has a bootloader called Grub which gives you a list of your operating systems when you boot to choose which one you want to go into. Basically, I'd install Tiny Core first on the 30GB space, and then install Ubuntu on the rest of the space. After the install, on a reboot you'll see a menu come up with the list of your operating systems which will include Tiny Core and Ubuntu. Then you just choose one and boot into it.

---

### Post by L Campbell on 2011-06-19
> **Old-un said:**
> I am currently running Xubuntu 11.04 and i would like to dual boot Xubuntu with Tiny Core 3.7. I have a 160GiB hard drive and thought i could give Xubuntu 130 GiB, and Tiny Core 30 GiB. The problem is i don't know how to dual boot two different operating systems. Is there anyone who would like to help me please?

Here is an article that might help you:-

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Old-un on 2011-06-19
Because i already have Xubuntu installed would i still have to install GRUB with Tiny Core?

---

### Post by akand074 on 2011-06-19
I don't think so. I don't know much about Tiny Core but I'm sure it has a bootloader. Otherwise it may not overwrite Grub. I only recommended XUbuntu last because I didn't know what Tiny Core provided. Just install Tiny Core, if you don't get a menu to choose which OS to boot into, just follow [these]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2") instructions on how to reinstall grub from a Live CD (though you could probably do it through TinyCore as well).

---

### Post by Old-un on 2011-06-19
Thanks for the help guys!

---

