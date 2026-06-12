---
title: "Kernel versions."
date: 2009-12-15
forum: New to Ubuntu
---

### Post by DeeDez on 2009-12-15
What's the reason for having 3 different kernel versions to choose from when booting Ubuntu 9.04?

---

### Post by Hetepeperfan on 2009-12-15
New kernel are constantly added. You should always keep one working version for your newst version might crash. Thus you can consider removing one of them.

go to system>administration>synaptic and search for linux images. There you can remove the redundant one.

best

Maarten

---

### Post by audiomick on 2009-12-15
When it was freshly installed, there was only one. When you get a kernel update, as happens from time to time, the update doesn't remove the old kernel. It is recommended to keep at least one "old" one to boot into should something go wrong with the current one.

I have never bothered to remove old kernels. They don't take up much space. It is possible to remove them, but I don't know how.

---

### Post by ukripper on 2009-12-15
> **DeeDez said:**
> What's the reason for having 3 different kernel versions to choose from when booting Ubuntu 9.04?

If you are happy with current latest kernel update and it is stable for you then thre is no need for you to have 3 different kernel entries. you can remove them from synaptic or just run this command:
```
sudo apt-get autoremove
```

---

### Post by DeeDez on 2009-12-15
> **audiomick said:**
> When it was freshly installed, there was only one. When you get a kernel update, as happens from time to time, the update doesn't remove the old kernel. It is recommended to keep at least one "old" one to boot into should something go wrong with the current one.

I have never bothered to remove old kernels. They don't take up much space. It is possible to remove them, but I don't know how.

Here's what I found: 
[**http://tinyurl.com/CleanUpBoot**]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")

I like things to look clean, plus I dual boot so it's less to scroll through.

Thanks you guys.

---

### Post by drs305 on 2009-12-15
DeeDeez,

Welcome to the Ubuntu forums. You can clean up the menu in a variety of ways. For removing or hiding old kernels, there is a section in the guide about StartUpManager that discusses the various options (removing, hiding). It is near the bottom of the guide. 

Click on the "SUM" link in my signature line if you want further information about old kernels or the other tweaks available with this Grub legacy GUI boot menu tweaker.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

