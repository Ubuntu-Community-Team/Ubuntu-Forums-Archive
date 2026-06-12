---
title: "Installing rtl8169/8110 Gigabit drivers"
date: 2005-06-16
forum: Networking &amp; Wireless
---

### Post by Lexical Unit on 2005-06-16
First let me say I love Ubuntu :)

There seems to be a problem installing the drivers for my new rtl8169/8110 Gigabit ethernet card.  The specific card I got is a LinksKey LKG-6100, it claims to use rtl8169/8110 drivers.  It came with a floppy disk which had support for 2.2.x and 2.4.x kernels but if I'm not mistaken my uname -a which displays "Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux" means that I need newer drivers.

So I searched google and found this site: [http://www.realtek.com.tw/downloads/downloads1-3.aspx?series=2003072&Software=True#2003072Unix%20(Linux](http://www.realtek.com.tw/downloads/downloads1-3.aspx?series=2003072&Software=True#2003072Unix%20(Linux))

After downloading the "Linux driver for kernel 2.4.x and 2.6.x" version 2.21 I attempted to follow the README file but it simply does not work.  It tells me to do:

make clean modules
make install
depmod -a

But on the first command I get:> make -C src/ clean
make[1]: Entering directory `/home/andrew/gigabit/src'
Makefile:28: /home/andrew/gigabit/Makefile_linux26x: No such file or directory
make[1]: *** No rule to make target `/home/andrew/gigabit/Makefile_linux26x'.  Stop.
make[1]: Leaving directory `/home/andrew/gigabit/src'
make: *** [clean] Error 2Since it's looking for /home/andrew/gigabit/Makefile_linux26x I moved that file there (it's actually in the /src directory, I guess whoever wrote the Makefile was either lazy or stupid or both) and tried it again:> andrew@ubuntu:~/gigabit $ sudo make clean modules
Password:
make -C src/ clean
make[1]: Entering directory `/home/andrew/gigabit/src'
rm -f *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags
make[1]: Leaving directory `/home/andrew/gigabit/src'
make -C src/ modules
make[1]: Entering directory `/home/andrew/gigabit/src'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/andrew/gigabit/src modulesmake: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/andrew/gigabit/src'
make: *** [modules] Error 2Ok so now it's looking for /lib/modules/2.6.10-5-386/build, I have a /lib/modules/2.6.10-5-386/ directory but no build directory therin.  Here's where I'm lost... I have no idea how to continue here.

Does anyone have any ideas? :(

---

### Post by Lexical Unit on 2005-06-16
:) Hey guess what I found /lib/modules/2.6.10-5-386/kernel/drivers/net/r8169.ko

---

### Post by jasonj75 on 2006-03-09
Same card, same drivers on 5.10, but I'll be damned if I can get the card to install. Should it be as simple as an insmod command for r8169.ko and away I go?

---

