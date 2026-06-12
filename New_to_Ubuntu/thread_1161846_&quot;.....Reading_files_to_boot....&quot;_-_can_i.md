---
title: "&quot;.....Reading files to boot....&quot; - can i remove this?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by listerdl on 2009-05-17
Hi, I am not sure what I have done but my boot start-up is taking 2 mins longer, i get this "Reading files needed to boot..." and then the system decides to list many programs that are [OK] and the firewall is [failed]

It then loads fine.

Any ideas how to remove this extra start-up process?

Thanks!

---

### Post by labinnsw on 2009-05-17
```
sudo gedit /boot/grub/menu.lst
```

Edit your default item. Change from:

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

to: 
> 
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro **quiet splash**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

---

### Post by Bush_Roo on 2009-05-17
If your system is freezing on boot, System Log might help you find out what is freezing on boot. (It lists the time, so you can see what takes a long time to start by following the time column.)

```
Alt+F2
gksu gnome-system-log
[enter]
```

---

### Post by listerdl on 2009-05-17
Hey thanks for the reply!

I did what you said but it does appear that my settings are already set to the 'quiet-splash' setting....the recovery mode settings have not been set - I can try making them quiet but I doubt that I am booting in the recovery mode? 

]## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		3fa8af0d-8ffe-4f98-ac6c-0577932e0d60
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3fa8af0d-8ffe-4f98-ac6c-0577932e0d60 [COLOR="Red"]ro quiet splash[/COLOR] 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		3fa8af0d-8ffe-4f98-ac6c-0577932e0d60
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3fa8af0d-8ffe-4f98-ac6c-0577932e0d60 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3fa8af0d-8ffe-4f98-ac6c-0577932e0d60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3fa8af0d-8ffe-4f98-ac6c-0577932e0d60 [COLOR="Red"]ro quiet splash [/COLOR]
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3fa8af0d-8ffe-4f98-ac6c-0577932e0d60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3fa8af0d-8ffe-4f98-ac6c-0577932e0d60 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3fa8af0d-8ffe-4f98-ac6c-0577932e0d60
kernel		/boot/memtest86+.bin
quiet[/HTML]

---

### Post by listerdl on 2009-05-17
> **Bush_Roo said:**
> If your system is freezing on boot, System Log might help you find out what is freezing on boot. (It lists the time, so you can see what takes a long time to start by following the time column.)

```
Alt+F2
gksu gnome-system-log
[enter]
```

Thanks for the advice - when I look at the time column is seems to have listed every program or function that I have used in the last 40 minutes that i have been online...is there something inn particular i should look for? Thanks again..

---

### Post by labinnsw on 2009-05-17
> my settings are already set to the 'quiet-splash' setting

If that is not the problem, I have no idea what it could be. Sorry I could not be of more help.

---

### Post by listerdl on 2009-05-17
thanks for your help.

---

### Post by Theo148 on 2009-05-17
> **listerdl said:**
> Thanks for the advice - when I look at the time column is seems to have listed every program or function that I have used in the last 40 minutes that i have been online...is there something inn particular i should look for? Thanks again..
Well the 'dmesg' log generally contains information pertaining to booting up. If you could post its contents, I suppose it might help us to help you (well not me specifically, I'm clueless when it comes to boot stuff :P ).

---

