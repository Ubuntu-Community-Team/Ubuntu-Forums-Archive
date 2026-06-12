---
title: "Can't boot ubuntu from USB - &quot;menu.c32: not a COM32R image&quot;"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by RailTracer on 2011-03-09
Hi, absolute beginner here. Followed the instructions [here]("http://www.ubuntu.com/netbook/get-ubuntu/download") on creating a pen drive linux to install ubuntu netbook remix on my netbook, set USB to highest boot priority in BIOS, but the message  "menu.c32: not a COM32R image" repeats ad infinitum. What do I do?

Thanks in advance.

---

### Post by RailTracer on 2011-03-09
Tried doing the same with desktop ubuntu on the netbook, but the same problem occurs.

---

### Post by I2k4 on 2011-03-09
Didn't have your problem with those instructions but different machines / BIOS.  

Google turns this up - can't speak for it but maybe works,

[http://forums.linuxmint.com/viewtopic.php?f=46&t=60436](http://forums.linuxmint.com/viewtopic.php?f=46&t=60436)

FYI, I found the Netbook Remix incredibly slow, consistent with other reports.  I recommend the Desktop 10.10 or (less preinstalled and very quick) Lubuntu.  Good luck.

---

### Post by coffeecat on 2011-03-09
> **RailTracer said:**
> Hi, absolute beginner here. Followed the instructions [here]("http://www.ubuntu.com/netbook/get-ubuntu/download") on creating a pen drive linux to install ubuntu netbook remix on my netbook,

Did you create the pendrive using Windows or Ubuntu? Since you are new to Ubuntu, I guess the answer is Windows, but in case you used Ubuntu's startup disk creator there is a bug (more than one) that means you have to use the 10.04 startup disk creator to create a 10.04 pendrive, or the 10.10 startup disk creator to create a 10.10 pendrive. Sample bug report here:

[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)

So, if you used Ubuntu, which version, and which version ISO did you download?

---

