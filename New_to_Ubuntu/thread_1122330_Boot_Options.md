---
title: "Boot Options"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by math&amp;music on 2009-04-10
So I'm still pretty new to Ubuntu and getting used to it, and linux in general. 

So here is my problem along with some questions:

I updated Ubuntu and previous to the update in the grub loader there was only one kernel a recovery option and the memory test (along with my other OS thats on here)

After the updates there are now 2 options to load 2 different versions 2.26.7-generic and 2.26.11-generic

However my wireless only works on 2.26.7-generic for whatever reason. 

So my question is:

1. Does it matter which kernel I use?
2. Can I edit the Grub Loader to only show the primary kernel, recovery, and my other operating system?

SPECS: (if needed)
Toshiba Satellite L305
2gb Ram
160 HD
2.16 dual core processor
Atheros 5007eg wireless card
Dual booted with Ubuntu 8.10 and Vista (sorry it came w/ the comp)  


Any Help will be greatly appreciated!

---

### Post by cariboo on 2009-04-10
Yes you can use the older kernel if it works better for you. Personally I would investigate why my wireless isn't working with 2.6.11. to edit /boot/grub/menu.lst press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

the above command will open the default text editor as root, allowing you to save the file after you edit it. Remove the entries that you don't want.

Jim

---

### Post by math&amp;music on 2009-04-10
Thank you cariboo!

Thats exactly what I needed to know! :)

---

