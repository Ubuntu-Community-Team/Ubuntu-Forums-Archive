---
title: "Marvell Yukon 88E8040T on Ubuntu 8.04 partialy solved - kernel recompilation issues"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by nicocarbone on 2008-06-02
I have a Toshiba Satellite notebook with has the Marvell Yukon 88E8040T network card. This card is not supported by Hardy, and the drivers available on Marvell's page are broken. Doing some research, i found that the problem can be solved adding the line that identifies the card { PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4355) } , in the sky2.c file, located under the 'drivers/net/' directory of the kernel source, and recompiling it.
By doing so, and using the new compiled kernel, the ethernet card is recognized properly and works well. However, with the new kernel, my sound card (Intel HDA) and my wireless card (Intel 3945ABG) are not working. 
Apparently, this is related somehow with missing kernel modules. I recompile the kernel following this guide:

[http://boilinglinux.blogspot.com/2008/04/ubuntu-kernel-compile-and-patch.html](http://boilinglinux.blogspot.com/2008/04/ubuntu-kernel-compile-and-patch.html)

Is there a way to recompile the current using kernel and conserve the driver modules? Is there another way to make the sky2 driver recognize my ethernet card without recompiling the kernel, knowing where the problem is?
Thanks you,

Edit: Since it is just a line of code, and that it will solve an important incompatibility problem for Satellites users, Where can I report this issue in order to be analised for inclusion in a future kernel update by Ubuntu developers?

---

### Post by sophie27 on 2008-06-27
I have the same problem of you (Toshiba Satellite and Marvell Yukon 88E8040T and Kubuntu 8.04).

I have modified my sky2.c file, but now I can't rebuild. Notice that I'm not so comptetent and I can't connect to network. I'm trying to do that:

**AUTOBUILD=1 fakeroot debian/rules **

but tha answer is:

**/usr/bin/fakeroot: line 164 debian/rules: No such file or directory**

ANY SUGGESTION ABOUT THAT?

Of course, also for me, if it was possibile not to rebuild it would be better...
According to you is some upadated Marvell driver coming up?
read: [http://linux.toshiba-dme.co.jp/linux/eng/pc/sat_psaj1_report.htm](http://linux.toshiba-dme.co.jp/linux/eng/pc/sat_psaj1_report.htm)

---

### Post by sophie27 on 2008-06-27
Nexte step...

This is my situation now. Using this guide:


[http://boilinglinux.blogspot.com/200...and-patch.html](http://boilinglinux.blogspot.com/200...and-patch.html)

I succeeded in re-building! All seems ok, but when I reboot with the new kernel....KERNEL PANIC!

Which could be the problem?

---

### Post by sagilca on 2008-07-09
There is a much easier solution than recompiling the kernel in another thread:

[http://ubuntuforums.org/showthread.php?p=5290300](http://ubuntuforums.org/showthread.php?p=5290300)

And it works :)

---

