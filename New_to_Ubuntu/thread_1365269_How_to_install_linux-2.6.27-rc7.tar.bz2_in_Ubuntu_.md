---
title: "How to install linux-2.6.27-rc7.tar.bz2 in Ubuntu 9.04"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mudresh on 2009-12-27
Hello Experts,

I am new to ubuntu, and i have installed aircrack on Ubuntu 9.04. I have wireless lan card Intel Wireless Wifi 5100 AGN, and i am facing problem to start the application. From few other thread i got to know for installation / patch of linux-2.6.27-rc7.tar.bz2.

This might be very easy question :(, but i would ask to how can in install linux-2.6.27-rc7.tar.bz2. I have downloaded this file from kernel.org to my ubunt desktop, now i want to install it for the kernel patch.

Do I need to recompile kernel? How can i install that downloaded file on my ubuntu to work Aircrack software?

Any help would be appriciated.

Thanks in Advance
Mudresh

---

### Post by taurus on 2009-12-27
There's a README from the same place that you've downloaded the kernel.

[http://www.kernel.org/pub/linux/kernel/README](http://www.kernel.org/pub/linux/kernel/README)

---

### Post by mudresh on 2009-12-27
Hello Taurus, 

I tried the readme you provided, but it gives me error below. 

root@mudresh-pc:/usr/src/linux-2.6.27-rc8/scripts# ./patch-kernel
usage: patch-kernel [-h] [ sourcedir [ patchdir [ stopversion ] [ -acxx ] ] ]
  source directory defaults to /usr/src/linux,
  patch directory defaults to the current directory,
  stopversion defaults to <all in patchdir>.

root@mudresh-pc:/usr/src/linux-2.6.27-rc8/scripts# patch-kernel /usr/src/linux-2.6.27-rc8
bash: patch-kernel: command not found

root@mudresh-pc:/usr/src/linux-2.6.27-rc8/scripts# ./patch-kernel /usr/src/linux-2.6.27-rc8
Current kernel version is 2.6.27-rc8 ( Rotary Wombat)
[: 275: =: unexpected operator
cannot find patch file: patch-2.6.28
root@mudresh-pc:/usr/src/linux-2.6.27-rc8/scripts# 

:( :confused: Actually I am doing this to make work wireless card as packet monitoring mode. My current kernel version is 

root@mudresh-pc:/usr/src/linux-2.6.27-rc8# uname -r
2.6.28-11-generic

.

How can i get out of this situation? 

Thanks
Mudresh

---

