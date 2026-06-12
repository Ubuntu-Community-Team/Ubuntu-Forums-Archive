---
title: "smartlink driver compilation error"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by dckirba on 2007-04-21
Hello all,

i had my smartlink modem working with dapper.

I followed instructions on the wiki after upgrading to feisty, but I get a compilation error. Sorry for cross-posting but here';s the link:

[http://ubuntuforums.org/showthread.php?t=416571&highlight=compiling+errors]("http://ubuntuforums.org/showthread.php?t=416571&highlight=compiling+errors")

I really need internet access on my machine guys, so any help will be appreciated.

I have installed build-essential and kernel headers... I'm at a loss

Cheers,
David K

---

### Post by dckirba on 2007-04-22
Hello all,

I'm still not able to comp;ile my drivers, and I've been playing around a bit, so let me know if I'm on the right track.

I edited the makefile for ungrab-winmodem like so:

```
-- original make file --

KERNEL_VER:=$(shell uname -r)
KERNEL_DIR:=/lib/modules/$(KERNEL_VER)/build
INSTALL_DIR:=/lib/modules/$(KERNEL_VER)/extra


-- changed kernel-dir, complete make file --

KERNEL_VER:=$(shell uname -r)
KERNEL_DIR:=/usr/src/$(KERNEL_VER)/build
INSTALL_DIR:=/lib/modules/$(KERNEL_VER)/extra

obj-m := ungrab-winmodem.o


all:
	$(MAKE) modules -C $(KERNEL_DIR) SUBDIRS=$(shell pwd)

clean:
	$(RM) *.o *.ko *.mod.* .*.cmd *~
	$(RM) -r .tmp_versions

install: all
	install -D -m 644 ungrab-winmodem.ko $(INSTALL_DIR)/ungrab-winmodem.ko
	/sbin/depmod -a
uninstall:
	modprobe -r ungrab-winmodem ; echo -n
	$(RM) $(INSTALL_DIR)/ungrab-winmodem.ko
	/sbin/depmod -a


```

I still get an error, and I'm not a programmer at all, but it looks like something that can be easily fixed, I just don't know how! This is what I get

```
david@ChomonKora:~/Desktop/ungrab-winmodem$ make
make modules -C /usr/src/2.6.20-15-generic/build SUBDIRS=/home/david/Desktop/ungrab-winmodem
make: *** /usr/src/2.6.20-15-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
david@ChomonKora:~/Desktop/ungrab-winmodem$ 

```

So if anybody know what to do to fix this, please let me know. Thanks in advance,

David K

---

### Post by _duncan_ on 2007-04-23
i met the same errors with ungrab-winmodem. What I did was to totally bypass ungrab-winmodem and went directly to compiling the smartlink modem driver.

Seems to work in my case. I'm posting this reply from my newly-installed feisty box with a smartlink modem. Just make sure you're using the latest driver from linmodems.org (circa april 22, 2007).

P.S. This is quick fix since the connection is probably going to be unstable without ungrab-winmodem. Just too tired to fiddle with source codes right now.

---

### Post by dckirba on 2007-04-23
Thanks duncan,

I will try that right now. I hope it works... I´m clueless at anything related to programming so I have no idea what could be wrong.

I´ll let you know if all works, and please let me know if you find a solution.

cheers,
David K

---

### Post by AleXit on 2007-04-23
I've found a fix to compile ungrab-winmodem module:

Edit **ungrab-winmodem.c**

Change the line

```
#include <linux/config.h>
```

to

```
#include <linux/tipc_config.h>
```

Now it comples :)

Bye!

---

### Post by dckirba on 2007-04-23
duncan and alexit,

you are bothe geniuses!!!

All compiled, thanks a ton. Now I have to get home and off my office network and setup the dialup connection.

Once again, thank you so much!

Cheers and have a good one,
David the connected once again at home K!
:guitar:

---

