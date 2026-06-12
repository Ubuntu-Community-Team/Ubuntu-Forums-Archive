---
title: "how do I check latest installed kernel?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-04-05
hi,
I used 'uname -a' but I think that just tells me the kernel I'm running. Due to being a paranoid freak, when given the option to update the menu.lst, I've just opted to keep the old, being scared of screwing something up. Now I want to run the latest kernel, but I'm not sure which the latest is! I'm apparently up-to-date so will likely match your kernel if you are up-to-date too.
I'm just going to copy the OS option in the menu list, and change the kernel number, but what is the latest? Is there a simple command to check?

TFC!
Robin

---

### Post by sandyd on 2009-04-05
just do
ls /boot

choose the highest initrd.img-*

and you know, ubuntu doesn't run the latest linux kernel ;)

[http://kernel.org/](http://kernel.org/)

---

### Post by SuperSonic4 on 2009-04-05
```
uname -r
```

---

### Post by AllenGG on 2009-04-05
First, look at Synaptic.  This will show you the latest kernel version available for your distro.  
Mine reads : Linux kernel headers for version 2.6.27 on x86/x86_64
(2.6.27-11-generic)
from experience IMHO stick with the version offered through Synaptic. 8)

---

### Post by hungryOrb on 2009-04-05
Thanks guys :) 
Oh Carlee! So, using the latest initrd is sound? :O You mean that the latest linux kernel isn't used right? Why's that? Doesn't linux run the ones that Debian does?

---

### Post by hungryOrb on 2009-04-05
Hm. So I just changed the 3 number 19's in bold to 23 like so:

```
title		Ubuntu 8.04.1, kernel 2.6.24-**19**-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-**19**-generic root=UUID=298c41c5-3150-47f8-9817-86b95d2c7ad7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-**19**-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=298c41c5-3150-47f8-9817-86b95d2c7ad7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

```

Will that suffice to load kernel 23?
TFC :)

---

### Post by AllenGG on 2009-04-05
latest is 2.6.27-11
Use Synaptic. Should show up with a star.

---

