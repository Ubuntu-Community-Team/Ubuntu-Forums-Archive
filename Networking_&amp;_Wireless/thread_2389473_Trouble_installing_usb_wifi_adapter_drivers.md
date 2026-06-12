---
title: "Trouble installing usb wifi adapter drivers"
date: 2018-04-17
forum: Networking &amp; Wireless
---

### Post by riversplitter on 2018-04-17
Hi everyone, I recently started using Ubuntu 16 in class. I installed it on an old computer at home to have the same setup as class.

Everything is working fine, except I can't seem to get my USB wifi adapter to work.

I followed the instructions I found here: [https://ubuntuforums.org/showthread.php?t=2362669](https://ubuntuforums.org/showthread.php?t=2362669) 

I believe the driver was downloaded and "made", but I'm not seeing the wifi network and I get this error when I run "modinfo 88x2bu": modinfo: ERROR: Module 88x2bu not found

Any idea?

I now know I could probably just return the wifi adapter and get another one that will plug and play nicely with Ubuntu, but I want to learn how to do this.

Thanks!

---

### Post by SeijiSensei on 2018-04-17
Did you run "sudo make install" after the compilation finished?

---

### Post by slickymaster on 2018-04-17
*Thread moved to **Networking & Wireless**.*

---

### Post by riversplitter on 2018-04-17
Yes. And it seemed to install.

It output this:

install -p -m 644 8822bu.ko  /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.13.0-38-generic

I'm not sure what to do next. I didn't see any change to my network, or anything.

---

### Post by riversplitter on 2018-04-17
I feel silly, but I rebooted my machine and now it works!

Thanks.

---

