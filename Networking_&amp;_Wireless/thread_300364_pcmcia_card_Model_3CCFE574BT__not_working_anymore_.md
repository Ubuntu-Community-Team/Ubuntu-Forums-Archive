---
title: "pcmcia card Model 3CCFE574BT  not working anymore with 2.6.15-27-286"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by mayankjohri on 2006-11-15
My 3com pcmcia card Model 3CCFE574BT is not working with the Linux kernel version 2.6.15-27-286, but if i boot with 2.6.12-9-386 it starts working.

I am not able to detect it even with the latest version of Linux Kernel.

I am using dapper linux on IBM 600E. 

Thanks
Mayank Johri

---

### Post by Jose Catre-Vandis on 2006-11-15
I have a 3CCFE575BT-D which works fine on the Edgy default kernel (I think they use the same driver?) so lets see if we can get you working. Are you getting no response and no lights at all on your card? Does ubuntu tell you anything if you try:

dmesg
lspci -v
lspcmcia -v
lshw

in a terminal

You have also taken a big jump in kernels, do you have anything inbetween you can try?

---

### Post by mayankjohri on 2006-11-16
Thanks for the help, i finally got it working. I upgraded the kernel to 2.6.17-10-386 and it started working again.

---

