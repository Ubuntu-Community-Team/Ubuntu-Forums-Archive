---
title: "Drivers for wireless pcmcia networkcard, where to find kernel source?"
date: 2005-06-23
forum: Networking &amp; Wireless
---

### Post by Nasso on 2005-06-23
Hi all
I just bought a CNET CWC-854 wireless networkcard. ( [http://www.cnet.com.tw/product/cwc854.htm](http://www.cnet.com.tw/product/cwc854.htm) )
I got the drivers here [http://www.ralink.com.tw/supp-1.htm](http://www.ralink.com.tw/supp-1.htm)

I am going through the steps in the readme file but i got stuck on step b;

> 
For 2.6 series kernel:
a.  run 'cd STA/Module'
        'cp ./2.6.x/Makefile .'
        'cp ./2.6.x/load .'

b.  $make -C /path/to/source SUBDIRS=$PWD modules
    Where /path/to/source is the path to the source directory for the (configured and built) target kernel.

c.  run '/sbin/insmod rt2500.ko'  (as root)
        '/sbin/ifconfig ra0 inet YOUR_IP up'


For big endian platform:
a.  replace Makefile with Makefile.BigEndian


Im using Hoary and i havnt made any changes on the kernel (does adding bluetoothsupport via Synaptic Package Manager count?). Where do i find the source to the kernel? :)

---

### Post by alastair on 2005-06-23
Well, they've not made much of an effort. I don't have the h/w but had a look.

You wil need the linux kernel headers at least e.g. I have :

linux-headers-2.6.10-5

Then, try someting like :

make -C /usr/src/linux-headers-2.6.10-5 SUBDIRS=$PWD modules

Inside the "Module" directory.

---

