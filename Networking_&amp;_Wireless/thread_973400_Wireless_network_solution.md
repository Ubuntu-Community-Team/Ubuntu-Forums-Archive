---
title: "Wireless network solution"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by wgjhstt247 on 2008-11-06
Hello Ubuntu Community,

I recently upgraded to Itrepid Ibex, like most of you. I had the problem where the connection would not work after 20 minutes to an hour. I thought I might have to switch wireless drivers or something, but I remember someone writing about the boot option pci=noacpi . It changes the way Linux handles drivers. All I did was modified the /boot/grub/menu.lst file and added pci=noacpi after the kernel on the kernel line. Like this:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f9e9f0e0-f2dc-4f86-a748-14f07b2aadd4 ro quiet splash **pci=noacpi**
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

Hopefully it will help you with your wireless problems.

In Him,
Ryan M.

---

