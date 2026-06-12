---
title: "Grub boot menu: do I need all those entries?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Chris Hansen on 2008-12-05
Hello and thanks to everyone who helped me with my last question. 

I have a dual boot set up with Vista and Ubuntu. 

When the boot menu comes up it looks something like this:

Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)

Can someone explain why there are so many boot options and if I really need all of them?

It seemed kind of cluttered and hard to read to me so I went to the menu.lst file and remmed out all but the first two and last one and it's much less cluttered now but I wanted to find out if this was a bad idea.

Thanks.

---

### Post by utsuprainfra on 2008-12-05
No, you're fine.  Commenting them out was a good idea.

---

### Post by barisurum on 2008-12-05
You can remove the old kernel (kernel 2.6.27-7-generic) by entering in a terminal:

> sudo apt-get --purge remove linux-image-2.6.27-7-generic

or you can remove it in synaptic and you wont see it in grub menu. 

You may also remove linux-headers-2.6.27-7-generic as well. This way is better because you will have a collection of old kernels every time you upgrade if you dont do it.

---

### Post by binbash on 2008-12-05
you may want to remove old kernels, however i recommend keeping min 2.You can comment out them at /boot/grub/menu.lst

---

### Post by 2hot6ft2 on 2008-12-05
One reason for having more than 1 kernel is that if something stops working with the new kernel you can go back to the one that worked.

For me kernel 2.6.27-9-generic made my wifi keep dropping signal but when I boot with kernel 2.6.27-7-generic it stays connected. Go figure.

There is another way of doing it for those who feel uncomfortable editing the menu.lst and that is StartUp-Manager ("sum" in synaptic) where you can choose how many kernels to show and whether or not to show the (recovery mode) options or the memtest86+ option

Yes I know that can all be done by editing the menu.lst file. Just thought I would give an alternative method.

---

