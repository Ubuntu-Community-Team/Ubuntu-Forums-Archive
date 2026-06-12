---
title: "Choosing run level via Grub"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Primefalcon on 2009-01-19
Hey all....

I'm running Intrepid and I've been modifying my run levels to suit specific needs.

for example I have run level 3 booting to just a command line prompt

The only way I know atm of booting into a run level though is at the recovery terminal or in the inittab file. Is there any way to choose a run level during grub bootup?

---

### Post by Primefalcon on 2009-01-19
Ok I went to:

```
/boot/grub/menu.lst
```

after examining the option at the grub boot screen figured it looked pretty striaght forward after examining the info and added in

```
title		Ubuntu 8.10, kernel 2.6.27-9-generic (run level 3)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6192e9e7-d6be-45f7-8601-c0ac98d9e03d ro quiet splash 3
initrd		/boot/initrd.img-2.6.27-9-generic
```


after

```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6192e9e7-d6be-45f7-8601-c0ac98d9e03d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

It did appear on the boot grub list, but when selected it still booted into the default run level as set in the inittab file, dang I must got this wrong

---

### Post by Primefalcon on 2009-01-20
Did I figure this wrong or am what I trying to do just impossible

---

### Post by Primefalcon on 2009-01-20
Anyone?

---

