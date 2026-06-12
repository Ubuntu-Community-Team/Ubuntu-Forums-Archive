---
title: "11n based PCI Express card RT2790 driver"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by xodeus on 2008-03-01
Hi there all.
Now I'm back. I was getting tired of Vista as it everyday got slower and slower and used too much of my HDD space. 

I'm back with a minty taste. I have got my sound to work thanks to all the great forum posters, but I now need the last thing... oh almost the last thng but this is more imortant than the last thing.

I've got a new Zepto Note 3215W it's a great Intel based laptop. I've customized it with Zepto's own Wireless extension and it uses Ralink RT2790 chip and driver. 

I've got the Linux driver from Ralink, but when I read the README file, there's a bunch of stuff I've to configure before compiling. Can anyone help me with that?
The Ralink driver can be found here: 
[http://www.ralinktech.com.tw/data/drivers/2008_0108_RT2860_Linux_STA_v1.5.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0108_RT2860_Linux_STA_v1.5.0.0.tar.bz2)

The stuff I was talking about is here:
2> In Makefile
set the "MODE = STA" *[okay that should be easy]*
chose the TARGET to Linux by set "TARGET = LINUX"* [just that]*
define the linux kernel source include file path LINUX_SRC[I] [do they mean /usr/src/linux here]
[/I]

3> In os/linux/config.mk 
define the GCC and LD of the target machine
define the compiler flags CFLAGS
*[I need help with those two]*

---

### Post by xodeus on 2008-03-02
I've now built the module and it's working, but I need an answer to this question instead. It's about module loading. Please help.
[http://ubuntuforums.org/showthread.php?p=4440776](http://ubuntuforums.org/showthread.php?p=4440776)

---

