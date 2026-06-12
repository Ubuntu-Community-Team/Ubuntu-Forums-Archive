---
title: "using update-grub"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by MiTavis on 2009-11-07
I have installed Ubuntu 9.10 on an external USB hard drive. To do so, I removed the main hard drive on my laptop (Compac nc6000) I did not do this the last time and had to have my company IT support recover the hard drive since the hard drive is encrypted. I believe what happened is that the installation put GRUB on the hard drive which then caused a boot problem. Anyway, the new install would not work on the computer until I tried it on a netbook where it worked fine. I then did a sudo aptitude update, sudo aptitude upgrade, and then did a sudo update-grub. At that point on the netbook it shows an option for booting into the windows XP home addition. This option works. On my original computer, the boot into Ubuntu works ok. There are two options for booting into Windows but they don't work.

Question: If I do another sudo update-grub, will the system again write something to the internal hard drive thereby corrupting it again?

---

### Post by lisati on 2009-11-28
If you did a clean install of 9.10, you won't have grub. 9.10, by default, uses grub2

---

