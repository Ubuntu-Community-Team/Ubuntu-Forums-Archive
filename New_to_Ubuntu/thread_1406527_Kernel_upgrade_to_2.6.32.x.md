---
title: "Kernel upgrade to 2.6.32.x"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by den160593 on 2010-02-14
Hi. I need to upgrade my kernel to 2.6.32.x (2.6.32.8 i think is the latest stable one) in order to use an update for a graphics driver. How can I install this on Ubuntu karmic?

I found: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.8/)

However I'm not sure how to install them. I'm an i386. How could I do so

Thanks!

---

### Post by mwcrowley on 2010-02-14
first things last.  If your pc won't start up correctly after you install this, you can always tell grub to boot your last kernel so you can still function.  Make sure you understand how to catch the grub menu at boot up.  The grub menu will list the installed kernels (and operating systems if you dual boot).

In firefox double click on linux-image-2.6.32-02063208-generic_2.6.32-02063208_i386.deb  It should ask you if you want to install this with gdebi, select yes and go from there.  You might need the linux-headers as well, it wouldn't hurt to install them.  After any kernel upgrade you need to reboot.

---

