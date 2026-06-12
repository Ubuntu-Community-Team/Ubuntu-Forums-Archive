---
title: "Error 28 Selected item cannot fit into memory."
date: 2010-03-18
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-03-18
Hi, I am trying to boot a iso image from a solid state disk using the grub menu, and I get this error.

At first I got a error 26 Contigous file( dont remember rest) and we did some changes to the menu.lst and used the --map -mem  way, and we got this error.

Anyways getting around grub errors 26 and 28 while booting a Iso image from grub menu?

---

### Post by ericeclifford on 2010-03-18
The SSD is IDE and is 4gigs

I have a 2g ram board on the MoBo.

I think the grub version is grub4dos( not 100% sure) I will post the menu.lst that we created for viewing ability if you think it would help find a solution to this disaster.

---

### Post by ericeclifford on 2010-03-18
I think the main problem is this line in the menu.lst,

initrd /casper/initrd.gz

I am not sure but when this is entered after all the other menu.lst items, it comes with this error, I think this is the source of the problem, dont know why.

---

### Post by ericeclifford on 2010-03-19
bump

---

