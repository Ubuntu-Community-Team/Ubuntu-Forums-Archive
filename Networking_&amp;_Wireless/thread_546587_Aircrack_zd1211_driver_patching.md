---
title: "Aircrack zd1211 driver patching"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by fyrefly07 on 2007-09-09
Just wondering if anyone has had success patching the zd1211 driver to support packet injection via the drivers available through the Aircrack-ng project? 

[http://www.aircrack-ng.org/doku.php?id=zd1211rw](http://www.aircrack-ng.org/doku.php?id=zd1211rw)


When trying to install the patch, I get the following:

user@uBuntu:/usr/src/linux-headers-2.6.20-16$ patch -Np1 --verbose --dry-run -i zd1211rw_inject_2.6.20.patch 
Hmm...  Looks like a unified diff to me...can't find file to patch at input line 4Perhaps you used the wrong -p or --strip option?The text leading up to this was:
--------------------------|diff -Naur linux-2.6.20.4-orig/drivers/net/wireless/zd1211rw/zd_mac.c linux-2.6.20.4-rawtx/drivers/net/wireless/zd1211rw/zd_mac.c
|--- linux-2.6.20.4-orig/drivers/net/wireless/zd1211rw/zd_mac.c 2007-03-23 20:52:51.000000000 +0100
|+++ linux-2.6.20.4-rawtx/drivers/net/wireless/zd1211rw/zd_mac.c        2007-04-16 01:53:58.000000000 +0200
--------------------------
File to patch: 


Right now my zd1211 adapter functions normally, supports Monitor mode, able to find AP's, but running the injection test fails.  I'm at a brick wall, my linux knowledge is limited, any pointers?

---

### Post by SintraKikuta on 2007-09-16
I have the same issue, any help?

---

### Post by ankhou on 2007-09-16
Hi, 

I had the same problem this morning

 Having seen ther is no answer here, i passed my sunday working on it, and I managed to setup the driver.

In fact, the Ubuntu standard package has no kernel sources to build modules, it seems to have only c headers.

 Download the kernel at [www.kernel.org](www.kernel.org), for me it was kernel 2.6.20.16. Be sure to take the same source as you kernel, you can check that with the bash command "uname -a".

Untar the file to /usr/src/linux and go back to the tutorial. Compilation and wireless work is ok, but I have not tried yet the aircrack. Be sure to be in super user mode, or use sudo.

Good luck

---

