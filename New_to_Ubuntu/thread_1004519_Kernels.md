---
title: "Kernels"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by texas.chef94 on 2008-12-07
I only want to know this from the perspective of my being curious. What might I have done or not done that allowed me at the initial boot sequence screen to have access to more then one kernel.

Thanks:?:

---

### Post by cartisdm on 2008-12-07
Everytime you update to a new kernal it keeps the old ones so you can revert back if you need to.



EDIT:  [Here's a great tutuorial on how to clean that GRUB up]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")

---

### Post by kansasnoob on 2008-12-07
I like to use Startup Manager:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

In my screenshot you can see that you can limit the number of kernels to be displayed:

[ATTACH]95544[/ATTACH]

**Take note however, that anytime there is a kernel update I change that to "2" temporarily until I'm sure the new kernel boots OK!**

---

### Post by billgoldberg on 2008-12-07
> **cartisdm said:**
> Everytime you update to a new kernal it keeps the old ones so you can revert back if you need to.



EDIT:  [Here's a great tutuorial on how to clean that GRUB up]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")

It is advised to always keep a back-up kernel in case a kernel update causes trouble.

---

