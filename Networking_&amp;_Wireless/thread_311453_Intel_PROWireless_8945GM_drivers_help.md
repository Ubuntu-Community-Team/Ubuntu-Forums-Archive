---
title: "Intel PRO/Wireless 8945GM drivers help"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by Dieter24 on 2006-12-02
So I downloaded the drivers and downloaded the latest version of ieee80211, however when I do a check for ARC4 cipher algorithm and CRC32, I come up with this:
```
grep: /lib/modules/2.6.10/build/include/linux/autoconf.h: No such file or directory
grep: /lib/modules/2.6.10/build/include/linux/autoconf.h: No such file or directory
```
So I either did something wrong, or I'm missing something I need.
Here's all of what I put into Terminal before I got the error.
```
bray@bray-laptop:~$ for i in CRYPTO_ARC4 CRC32; do \
> grep CONFIG_INSTALL \
> /lib/modules/2.6.10/build/include/linux/autoconf.h; done
```
Not a whole lot at all, but it's what the INSTALL.txt file told me to do.

Also, I went forward a little to see if I was missing anything else, and apparently I'm missing the kernel source packages for my distro (xubuntu).

So I need help with these:
Where can I find the kernel source packages, and
How do I fix the ARC4 cipher algorithm and CRC32 problem?

Any and all help is much appreciated.

P.S. I did search through the wiki and the forums and google for a solution and I could find none.

I am using Xubuntu Edgy Eft

---

### Post by pestilence4hr on 2006-12-02
You don't need to build these drivers...they are included in edgy.  sudo apt-get install linux-restricted-modules-generic

---

### Post by Dieter24 on 2006-12-02
Ah, ok, it said it was installed, but then I just did this:
```
sudo apt-get upgrade linux-restricted-modules-generic
```
And now everything is all fine and dandy. Thanks for your help.

---

