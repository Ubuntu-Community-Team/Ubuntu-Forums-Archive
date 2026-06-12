---
title: "Lenovo Enhanced Experience 2.0"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by KeremE on 2011-07-27
Hi, I just bought a Thinkpad E520, which comes with the "Lenovo Enhanced Experience 2.0", outlined here: [http://ubuntugide.wordpress.com/author/hardikbhatt123/page/21/](http://ubuntugide.wordpress.com/author/hardikbhatt123/page/21/), installed on it, and was wondering whether an install of Ubuntu would affect the existing Windows booting at all? Also, the last time I installed Ubuntu, I had problems setting Windows to be the primary OS in Grub, and was thinking about trying EasyBCD. Do any of you know how to set Windows to be the default OS in Grub or had any experience with EasyBCD? 

Thanks!

---

### Post by amjjawad on 2011-07-27
> **KeremE said:**
> Hi, I just bought a Thinkpad E520, which comes with the "Lenovo Enhanced Experience 2.0", outlined here: [http://ubuntugide.wordpress.com/author/hardikbhatt123/page/21/](http://ubuntugide.wordpress.com/author/hardikbhatt123/page/21/), installed on it, and was wondering whether an install of Ubuntu would affect the existing Windows booting at all? 


[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
OR
Check my signature
OR
Use Google
OR
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

There are many approaches to do that:

1- VirtualBox installed in Windows: [http://www.virtualbox.org/](http://www.virtualbox.org/)
2- Wubi - which I DO NOT recommend at all.
3- Install Ubuntu on an external HDD or USB Flash Drive so that your Windows won't even be effected or touched
4- Dual Boot with Windows.


> Also, the last time I installed Ubuntu, I had problems setting Windows to be the primary OS in Grub, and was thinking about trying EasyBCD. Do any of you know how to set Windows to be the default OS in Grub or had any experience with EasyBCD? 


Startup Manager.
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Of course, that's after installing Ubuntu.

---

### Post by KeremE on 2011-07-27
Thanks for the reply. So, after reading the section on booting, I am assuming that it shouldn't affect the tweaks made by Lenovo for Windows 7? I am still not sure how exactly EasyBCD works - I am assuming that on startup, the MBR points to EasyBCD, and selecting Windows from there will run the Windows bootloader with any modifications or changes that Lenovo has made. (Also, where does BIOS come in on this?)Please correct me if I am wrong in my understanding. Thanks!

---

### Post by amjjawad on 2011-07-27
> **KeremE said:**
> Thanks for the reply. 

Most welcome ;)

> So, after reading the section on booting, I am assuming that it shouldn't affect the tweaks made by Lenovo for Windows 7? 

Installing Ubuntu as a Dual-Boot with Windows, **if done correctly**, it should NOT effect anything installed inside Windows.

> I am still not sure how exactly EasyBCD works
I'd recommend to use GRUB2.

Please check GRUB2 link in my signature. You'll love it :)


> I am assuming that on startup, the MBR points to EasyBCD, and selecting Windows from there will run the Windows bootloader with any modifications or changes that Lenovo has made. (Also, where does BIOS come in on this?)Please correct me if I am wrong in my understanding. Thanks!

For better understanding for the whole process, please refer to these links:

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Booting#Boot_loader](http://en.wikipedia.org/wiki/Booting#Boot_loader)
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

Should you have any other question, please let us know :)

It's lunch time here so ... brb ;)

---

