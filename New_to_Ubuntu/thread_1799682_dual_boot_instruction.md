---
title: "dual boot instruction"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-07-07
I have Windows XP currently and I want to make it a dual boot with ubuntu 11.04.  Do you have a step by step installation documentation of ubuntu 11.04 to make it a dual boot for my machine please?

---

### Post by jtarin on 2011-07-07
[Here's a guide.]("http://members.iinet.net.au/~herman546/index.html").....it's basically the same setup.You can install it side by side or in its own partition. Either way choosing the default Grub (bootmanger) option will install Grub to the MBR or your disk overwriting Windows Boot loader. Grub will detect Windows and boot it. However if you ever want to uninstall Ubuntu you will need to restore the MBR so windows will boot.There is one way to avoid this in my signature you will see a link to EasyBCD...it's an option. Are you using the install CD or a USB flash?

---

### Post by hoangtu69 on 2011-07-08
I'm thinking of USB since I have an external hard drive already so I'm thinking of downloading ubuntu onto it.

Basically ideally when my laptop starts, I want it to display 2 choices, Windows XP and Ubuntu for me to pick.  If I don't pick then Windows will start by default.

Will you have a different instruction guide given what I want?

Thanks

---

### Post by jtarin on 2011-07-08
You plan on installing Ubuntu to an external USB drive.....is that correct?

---

### Post by jtarin on 2011-07-08
[Here's a read]("http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/") of one way to dual boot using XP boot.ini and not installing Grub to your windows MBR. I used to use this method with Lilo and Grub when I had XP. Now with 7 I use EasyBCD.

---

