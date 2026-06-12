---
title: "Can't connect to wifi or ethernet on Dell Inspiron 1520"
date: 2016-07-21
forum: Networking &amp; Wireless
---

### Post by sampeckinpah on 2016-07-21
Hey, I just installed Ubuntu 16.04 on my dad's old Dell Inspiron 1520 laptop, as a way of getting it up and running again. I myself use Ubuntu on my own machine, but am not all that technically skilled.

So my dad is 100% new to Ubuntu, has never used any Linux distro before. When I installed 16.04, the machine was able to connect to the internet via ethernet, and under the DRIVERS section in settings, we were able to locate the proprietary drivers needed to connect to wifi. Well, after installing the driver and rebooting his machine, we were still not able to access the web via wifi - but now, even the ethernet connection wasn't working!

I'm hoping someone would be able to help me out here. My dad was really psyched to be able to get his old computer up and running again (with a much better OS than the Windows Vista that had previously been installed on the HDD), but we've run into this snag. I'm fairly new to Ubuntu as well so unfortunately I wasn't much help.

Any help or advice would be hugely appreciated!

---

### Post by howefield on 2016-07-21
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by gordintoronto on 2016-07-21
On an old machine like that, use Xubuntu or Lubuntu. How much memory does the laptop have? If the answer is less than 1 GB, it should be retired or have a memory upgrade.

BTW, I have installed Xubuntu on several Dell 1520s, and it runs OK -- but a little slow.

---

### Post by wildmanne39 on 2016-07-21
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and ethernet should be working, then do:
```
sudo apt-get install firmware-b43-installer
```
Reboot and wireless should come on.
Thanks

---

