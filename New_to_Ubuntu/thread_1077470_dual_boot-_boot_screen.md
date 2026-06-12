---
title: "dual boot- boot screen"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by nshailesh on 2009-02-22
I have a dual boot system with windows and ubuntu as the two os.
The boot screen typically shows 4 options viz
ubuntu 8.04
ubuntu 8.04 (recovery mode)
memtest

windows xp


I tryed to use 1st option on the screen i.e ubuntu 8.04 but nothing happened.
so I have to use the recovery mode.
what is the difference between the two options ??????????

Also on my friends pc both the options work properly.
why this happens ??
is it because my processor is p4 and he has core2 duo ??????

what is the use of memtest option ??

Also I want to customise the boot screen .
I want windows to be the default choice after timeout and ubuntu should appear below windows.
how to do it (how to edit the master boot record of ubuntu) ??????

---

### Post by Walter Melon on 2009-02-22
memtest is exactly what the name says it is.  it checks the memory for any errors.

And to customize the boot screen as well as edit the boot menu you have to edit /boot/grub/menu.lst.  
mine looks like this:

```
## ## End Default Options ##


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows Vista/Longhorn (loader)
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f6226139-20ec-4a65-816a-f735b995de43 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f6226139-20ec-4a65-816a-f735b995de43 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

