---
title: "Ubuntu shutdown problem"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by hariwonderful on 2011-07-06
Hey there everyone!

I installed ubuntu 11.04 64bit on my brother's hp dv6 laptop. We have Windows 7 Home premium installed alongside. Now the bootloader is GRUB2.

When I first ran the ubuntu disk to install, after installation it hanged when trying to restart. We had to poweroff the laptop after waiting for 20-30 minutes. After that I ran ubuntu from bootloader and it worked fine. But when i try shutting down/restarting ubuntu, it keeps hanging. i tried editing /etc/modules adding:

> 
apm power_off = 1


And i also edited /etc/default/grub adding:

> 
acpi=off


after quiet splash in DEFAULT line. 
It didnt work. I really wish to get my hands on Natty Narwhal.

Please help.

---

