---
title: "Synaptic Package Manager Immediately Closes"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Mdel34 on 2011-05-14
I just installed Ubuntu 11.04 as a dual boot on my Dell Inspiron 6000 - When I run certain application they immediately close, specifically Synaptic Package Manager and Update Manger.  They open for a split second and then close.

I was in the process of trying to install the driver for my wireless card -- i noticed i needed Ndiswrapper and tried to install it using Synaptic Package Manager but noticed that synaptic would not stay open.


Any ideas???  Thanks

---

### Post by wilee-nilee on 2011-05-14
Run these two commands in a taerminal and see what happens, the first is for unlocking, the second will kick any upgrade stopped back in gear.

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install 
```

---

### Post by Mdel34 on 2011-05-16
That worked -- synaptic package manger now works fine - thanks

---

### Post by jsellos on 2012-01-30
Hello,

This action doesn't work for me, it's absolutely the same as before, when I launch synaptic manager it stops immediately.
Do you have another idea I could try?

Thanks a lot,

---

