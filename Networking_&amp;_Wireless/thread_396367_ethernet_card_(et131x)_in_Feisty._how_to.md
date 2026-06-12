---
title: "ethernet card (et131x) in Feisty. how to?"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by uterrorista on 2007-03-29
the next tutorial worked fine in the 6.10 version, but in 7.04 i'm having some problems.
the tutorial is:
> ENABLE ETHERNET CARD

After installing the new kernel, its time to work on the ethernet card support. First of all you need to install the proper kernel header to be able to compile modules, then download the module, apply some patches, compile and install it. Follow these steps:

- Execute apt-get build-essential linux-headers-686
- Download the et131x module from [http://dadams1969.googlepages.com/et131x-1.2.2-3.src.tar.gz](http://dadams1969.googlepages.com/et131x-1.2.2-3.src.tar.gz)
- Extract the contents in a folder. There must be 6 files. One of them is a tar.bz2 file that should be extracted IN THE SAME FOLDER so there are 42 files in total.
- Apply the patches in the following order:
patch < new_ver_x86_3-10-06.patch
patch < fix-patch_et131x_x86_3-10-06.diff
patch < fix-get_mac_address_from_EEPROM.diff
patch < MODULE_PARM.diff
- Execute make
- Execute make modules_install
- Execute insmod et131x.ko
- Execute depmod
- Execute modprobe et131x

That’s it!

but when i type **MAKE**, i gives me this error:
> qaz@blue:~/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES$ make
#@make -C /lib/modules/2.6.20-13-generic/build M=/home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
  CC [M]  /home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES/et131x_main.o
In file included from /home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES/et131x_main.c:79:
/home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES/et131x_version.h:85:26: error: linux/config.h: No such file or directory
In file included from /home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES/et131x_adapter.h:85,
                 from /home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES/et131x_main.c:116:
/home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES/ET1310_rx.h:441: warning: ‘kmem_cache_t’ is deprecated
make[2]: *** [/home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES/et131x_main.o] Error 1
make[1]: *** [_module_/home/qaz/Desktop/aa/et131x-1.2.2-3.src.tar.gz_FILES] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
make: *** [modules] Error 2

 How can i fix this?

---

### Post by uterrorista on 2007-04-04
does someone have this card already installed in Feisty ???

---

### Post by chili555 on 2007-04-04
Do you have linux-headers installed? It is available in Synaptic. If you have no internet without the et131x module, you can search [http://packages.ubuntu.com](http://packages.ubuntu.com) for linux-headers in Feisty to match your running kernel *uname -r*, burn a CD and install on your Ubuntu machine with *sudo dpkg -i linux-headers<whichever>.deb*

There is also this: [http://sourceforge.net/projects/et131x/](http://sourceforge.net/projects/et131x/) which, after you get headers, may work.

---

### Post by uterrorista on 2007-04-04
yes i have...

---

### Post by chili555 on 2007-04-04
I just tried 3-4 methods on my Feisty machine. All of them failed and I Trashed files until I downloaded the tar.gz here: [http://sourceforge.net/projects/et131x/](http://sourceforge.net/projects/et131x/).

I then:```
tar -zxvf et131x..etc.
cd et131..etc.
sudo make
sudo make modules_install
```
For ..etc. you can use the TAB key to auto-complete the commands.

I got warnings but no errors in 'make' and no warning or errors in 'make modules_install.' At the end, I have an et131x.ko module in /lib/modules/.. that I could modprobe.

Now this may or may not work; I have no way to test it, as I do not have an et131x device. Please post back; there are others here trying to get et131x going.

---

### Post by uterrorista on 2007-04-12
it's finally working.
it think it was the updates!!!

---

### Post by uterrorista on 2007-04-17
it was not the updates. it needs **human installation**!!!!!

check my blog for solution » [http://linuxinside.blogspot.com/2007/03/tuning-lg-p1.html]("http://linuxinside.blogspot.com/2007/03/tuning-lg-p1.html")
if you have any different LG hardware thats needs installation please give me some feedback.

---

