---
title: "Installation inside Windows on a external hard disk."
date: 2009-01-19
forum: New to Ubuntu
---

### Post by bart_b on 2009-01-19
Hello, I just started to find out how Linux works, so I downloaded the 8.04 LTS version of Ubuntu. While I used the virtual DAEMON manager, I saw that it was possible to install Ubuntu inside Windows, so I did. Because of not having enough free space on my HDD, I resolved to try to install it on my external hard disk. The installation ran smoothly, but when I rebooted my system en selected Ubuntu as operation system, I got a black screen with : "GRUB>" and I don't know what I have to do further to boot the Ubuntu operation system. Now I also began to ask myself if it 's possible to start Ubuntu from an external hard disk? As you will notice, I 'm an absolute Beginner...

Best,

Bart

---

### Post by mikewhatever on 2009-01-19
Is it correct to assume you have Ubuntu installed on an external hdd and Windows on an internal? If that's the case, can you boot Windows?

---

### Post by bart_b on 2009-01-19
Yes, that's right. And I still can boot Windows.

---

### Post by superprash2003 on 2009-01-19
check out this link [www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/) especially step 9 where you should specify to install the boot loader onto the external hdd.. also while booting select usb hdd as booting device

---

### Post by bart_b on 2009-01-19
Thanks for the information. 
I have been able to resolve my problem, just by switching the priority in my BIOS whereby my internal HDD has the highest priority above my external USB HDD. And now UBUNTU runs smoothly!

---

