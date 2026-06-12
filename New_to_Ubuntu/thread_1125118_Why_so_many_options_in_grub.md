---
title: "Why so many options in grub?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by baxna on 2009-04-14
[FONT="Franklin Gothic Medium"][SIZE="3"]After installing 8.10 and rebooting, I notice all sorts of kernel options to boot into. What are all these for? When would I use a different kernel? Or can anyone point me to a FAQ or something about these options?

[LIST=1]
[*]Ubuntu 8.10, Kernel 2.6.27-11-generic
[*]Ubuntu 8.10, Kernel 2.6.27-11-generic (recovery mode)
[*]Ubuntu 8.10, Kernel 2.6.27-7-generic
[*]Ubuntu 8.10, Kernel 2.6.27-7-generic (recovery mode)
[*]Ubuntu 8.10, memtest86+
[/LIST]

Thanks for the help! :-D
~Mike[/SIZE][/FONT]

---

### Post by SunnyRabbiera on 2009-04-14
Usually when you update the kernel, the older kernel is listed as a "just in case" the newer kernel has issues with the system.
It adds no real extra space to your system and is normal

---

### Post by Razmear on 2009-04-14
I've got about a page and a half of kernel versions, so don't feel to bad. 

This article has some info for you: 
[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

There are better tips in the comments than in the main article. 

eb

---

### Post by Elfy on 2009-04-14
1 the newest kernel
2 it's recovery mode - you might need this 

3 and 4 are the previous kernel options

5 a memtest

When you get a kernel upgrade - you will get a new pair added to the top.

You can remove old kernels by uninstalling them - this updates grub, you could also just comment them out of the list - this won;t actually uninstall anything.

I always keep at least the previous kernel - just in case of problems with the newest one.

---

### Post by zika on 2009-04-14
> **Razmear said:**
> I've got about a page and a half of kernel versions, so don't feel to bad. 

This article has some info for you: 
[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

There are better tips in the comments than in the main article. 

eb
this "article" is a good example of what NOT to follow, I agree.

if You want to remove unused kernels go to Synaptic and search for "linux-image" and "linux-headers" and (carefully) pick those (by the numbers) that You do not need anymore. once You located them, mark them for "complete removal" and, after re-checking the list, apply that ...

be careful and do not do anything You are not comfortable with and not sure about what You are doing. feel free to ask ...

---

