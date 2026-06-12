---
title: "ndiswrapper won't compile"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by jfinn on 2008-01-31
I just installed ubuntu 7.10 on my aspire 5050 laptop.  There are various writeups in the forums regarding the wireless atheros card and it's issues...apparently ndiswrapper is the way to go.  Unfortunately when I try to compile it I get stuck.  Here is what I'm getting.

ubuntu:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/jerrod/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/jerrod/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/jerrod/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/jerrod/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/jerrod/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/jerrod/ndiswrapper-1.5/driver/loader.o
/home/jerrod/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/jerrod/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/jerrod/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/jerrod/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/jerrod/ndiswrapper-1.5/driver'
make: *** [all] Error 2

I've seen other posts with similar outputs but no resolutions.  Any help would be greatly appreciated.  I really need to get this wireless working so I can dump the Vista install that came preloaded on this laptop.

---

### Post by akbob on 2008-01-31
I used the guide at [NDISWrapper: The Ultimate Guide]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/") which was the only way I got my wireless card working.  There were some steps that I was missing before.  Also, the [NDISWrapper Wiki]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/%20") was very helpful, particularly the "List of cards known to work" which showed me exactly which driver to install and where to get it from.  One other thing is that I installed the driver per the guide instruction in the terminal, rather than using the GUI. (don't know if that made a difference or not)

Good luck, I'm sure others here will have more to offer.

---

### Post by tangibleorange on 2008-02-01
Have you tried just installing ndiswrapper from the CD?

> sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 

This way synaptic handles it all - you shoudn't need to use the command line. It's worth a try I think.

---

### Post by wieman01 on 2008-02-01
See this thread if you need support:

[http://ubuntuforums.org/showthread.php?t=574501]("http://ubuntuforums.org/showthread.php?t=574501")

---

