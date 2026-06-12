---
title: "connection problem..again!"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by kingswood71 on 2009-04-20
Ok..so I have configured the usb modem,when I ping the address suggested in ubuntu help, it comes back showing a very good connection.. The problem is..I have disabled ivp6 (ubuntu and firefox).. but firefox still will not load a page!! It was working yesterday in the morning, but stopped in the afternoon.

Also, package manager fails to download any new packages!

Help... still loving ubuntu...
Cheers Rohan (australia)

---

### Post by ptn107 on 2009-04-20
A few days ago I applied a kernel update that did this to me, effectively making my wireless card inoperable.  I couldn't update my system or view web pages.  The problem turned out to be the kernel module included in that update.  Installing the linux-backports-modules package solved my problem, it may help you.
_[linux-backports-modules-2.6.28-11-generic (32-bit)]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-11-generic_2.6.28-11.12_i386.deb")_
_[linux-backports-modules-2.6.28-11-generic (64-bit)]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-11-generic_2.6.28-11.12_amd64.deb")_

After you install the package, restart and see if it helps or not.

---

### Post by cariboo on 2009-04-20
IF you can ping an ip address, but have problems access a web site by name, I would suggest you have a look at what the dns nameserver addresses look like in /etc/resolv.conf. If you are using a router, resolv.conf should have the same dns addresses as the staus page on your router.

Jim

---

### Post by kingswood71 on 2009-04-20
thanks for replies guys!
Problem sorted.. It was the ipv6 thing again.. followed the advice on the thread, made bad list and its good to go!!
I am actually falling in love with this ubuntu!!

---

