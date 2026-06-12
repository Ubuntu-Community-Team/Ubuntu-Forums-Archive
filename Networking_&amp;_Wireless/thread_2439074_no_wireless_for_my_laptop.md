---
title: "no wireless for my laptop"
date: 2020-03-22
forum: Networking &amp; Wireless
---

### Post by kickass1955 on 2020-03-22
hi, new to Linux, realteck wireless not working.  rtl 8821ce 802.11ac to  connect to. was told to image iso file, but i can't get it to mount
 . hp laptop, 4 gig ram, ryzen processor, no internet. was going by ross post.
have no internet and in was told drivers would be in iso image.


sudo mkdir /media/cdrom
cd ~
sudo mount -o loop ubuntu-* /media/cdrom.


iso is in home directory.
plz help

ok got it to mount...my bad on wording in terminal.   now how do i tell package updater to look at iso to get my drivers?
a fresh install, and only see one updater...help...
ok... got to look at iso and it has no realteck drivers available..
now i need help bad.
HELP...
did find a link from git to download drivers. but i do not know how to install them.
i extracted files and there is a install file there but to no avail.... i am too new at this....help

---

### Post by chili555 on 2020-03-22
Can you get internet connectivity by ethernet or tethering?

[https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce)

---

### Post by kickass1955 on 2020-03-22
no ethernet, can use phone and power cord for phone, but need instructions on how

---

### Post by kickass1955 on 2020-03-22
i have windows on other side of computer , downloaded file and going to attempt install...brb

---

### Post by kickass1955 on 2020-03-22
i cannot use (make)... not installed....help

---

### Post by chili555 on 2020-03-22
> **kickass1955 said:**
> i cannot use (make)... not installed....helpStop!

You will have a lot of difficulty without thethering. Please stand by.

---

### Post by kickass1955 on 2020-03-22
ok

---

### Post by kickass1955 on 2020-03-22
i am here

---

### Post by wildmanne39 on 2020-03-22
Attach your cell phone through your usb port to your computer, make sure the other end is plugged into your cell phone then turn on usb tethering on your phone and it should connect, the connection will show up as an ethernet connection.

---

### Post by kickass1955 on 2020-03-22
ok, thanks

---

### Post by kickass1955 on 2020-03-22
i have no phone availabe to tether

---

### Post by wildmanne39 on 2020-03-22
It will be harder and chili555 is better at the directions for this kind of thing, it may be possible to download the driver on another computer with an internet connection to an usb drive then transfer them to your ubuntu computer, it would probably be easier to take your computer to a friends house that has an ethernet connection and borrow there internet.

---

### Post by kickass1955 on 2020-03-22
i have no phone that will tether,not part of my service plan....now what?

---

### Post by kickass1955 on 2020-03-22
i cannot take to a friends house...not a option.

---

### Post by kickass1955 on 2020-03-22
i have windows on other side of computer...just need instructions and can transfer files over to Linux side

---

### Post by chili555 on 2020-03-23
This method, although it is tedious, will work. The list of deb files you need is this (with the exception of bcmwl-kernel-source): [https://paste.ubuntu.com/p/GbZ689gYXw/](https://paste.ubuntu.com/p/GbZ689gYXw/) Create a folder on your desktop to hold the files you will download. I suggest:

```
mkdir ~/Desktop/debs
```

Go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Select your Ubuntu version; find out with:

```
lsb_release -d
```

And your architecture; either 32- or 64-bit:

```
arch
```

I suspect that your installation is 64-bit, also known as amd64 or x86_64. 

Search for and download to a USB drive, the package build-essential. Continue until every package on the list I provided is downloaded to the USB drive. When you have all of them downloaded, drag and drop them to the folder you created, Desktop/debs.

Now, back to the terminal:

```
cd ~/Desktop/debs
sudo dpkg -i *.deb
```

Now you may proceed to install the driver you downloaded. Post back if you get stuck.

---

### Post by kickass1955 on 2020-03-23
ok, thanks...will try this...if i get stuck i will ask for help...thank you so much

---

### Post by kickass1955 on 2020-03-23
and what about the reltek 8821ce drivers i need to install?
i guess that is next after that

---

### Post by kickass1955 on 2020-03-23
yes it is 64 bit amd, 4 gig of ram, quad core

---

### Post by kickass1955 on 2020-03-23
am i to download bcmwl-kernal source?  that is for broadcom wireless, and i have realtek 8821ce chipset

---

### Post by chili555 on 2020-03-23
> and what about the reltek 8821ce drivers i need to install?
i guess that is next after that

Please see my post #2 where I gave you the link which includes instructions.

> am i to download bcmwl-kernal source? that is for broadcom wireless, and i have realtek 8821ce chipset

My instructions above clearly say, "...with the *exception *of bcmwl-kernel-source," so no.

---

### Post by kickass1955 on 2020-03-23
ok  ...all files copied...going over to ubuntu to try....brb

---

### Post by kickass1955 on 2020-03-23
ok back....no good... a lot of errors...  dependency problems - leaving unconfigured


  Setting up libc6-dev:amd64 (2.27-3ubuntu1) ...
  Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
  Processing triggers for libc-bin (2.27-3ubuntu1) ...
  Errors were encountered while processing:
   dpkg-dev
   g++-7
   gcc-7
   libasan4:amd64
   libatomic1:amd64
   libcilkrts5:amd64
   libgcc-7-dev:amd64
   libitm1:amd64
   liblsan0:amd64
   libmpx2:amd64
   libquadmath0:amd64
   libstdc++-7-dev:amd64
   libtsan0:amd64
   libubsan0:amd64
   build-essential
   dkms
   g++
   gcc


and then this...



  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ dir
  clean  hal           ifcfg-wlan0  Kconfig  os_dep    rtl8821c.mk wlan0dhcp
  core   halmac.mk  include      Makefile  platform  runwpa
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ make clean
  /bin/sh: 1: cc: not found
  (standard_in) 1: syntax error
  #make -C /lib/modules/5.3.0-28-generic/build M=/home/dominic/Downloads/rtl8821ce clean
  cd hal ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
  cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
  cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
  cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
  cd core ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
  cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
  cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
  cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
  cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
  rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
  rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
  rm -fr .tmp_versions
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ make
  /bin/sh: 1: cc: not found
  (standard_in) 1: syntax error
  make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.3.0-28-generic/build M=/home/dominic/Downloads/rtl8821ce  modules
  make[1]: Entering directory '/usr/src/linux-headers-5.3.0-28-generic'
  /home/dominic/Downloads/rtl8821ce/Makefile:2157: home/dominic/Downloads/rtl8821ce/hal/phydm/phydm.mk: No such file or directory
  /home/dominic/Downloads/rtl8821ce/Makefile:2166: home/dominic/Downloads/rtl8821ce/rtl8821c.mk: No such file or directory
  make[2]: *** No rule to make target 'home/dominic/Downloads/rtl8821ce/rtl8821c.mk'.  Stop.
  Makefile:1655: recipe for target '_module_/home/dominic/Downloads/rtl8821ce' failed
  make[1]: *** [_module_/home/dominic/Downloads/rtl8821ce] Error 2
  make[1]: Leaving directory '/usr/src/linux-headers-5.3.0-28-generic'
  Makefile:2237: recipe for target 'modules' failed
  make: *** [modules] Error 2
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ sudo make install
  /bin/sh: 1: cc: not found
  (standard_in) 1: syntax error
  install -p -m 644 8821ce.ko  /lib/modules/5.3.0-28-generic/kernel/drivers/net/wireless/
  install: cannot stat '8821ce.ko': No such file or directory
  Makefile:2243: recipe for target 'install' failed
  make: *** [install] Error 1
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ sudo modprobe 8821ce
  modprobe: FATAL: Module 8821ce not found in directory /lib/modules/5.3.0-28-generic
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$

did i mess it up worse?
help

---

### Post by chili555 on 2020-03-23
Try to install the packages that ended in errors one at a time and let&#8217;s see exactly what the error is, for example:

sudo dpkg -i dpkg-dev*.deb

And so on.

---

### Post by kickass1955 on 2020-03-23
ok ... will make a list  of ones bad....brb

---

### Post by chili555 on 2020-03-23
> **kickass1955 said:**
> ok ... will make a list  of ones bad....brb
We need to see the exact error.

---

### Post by kickass1955 on 2020-03-23
here is whole list....sorry for it is long

 ```
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/debs$ sudo dpkg -i *.deb
  (Reading database ... 132444 files and directories currently installed.)
  Preparing to unpack build-essential_12.4ubuntu1_amd64.deb ...
  Unpacking build-essential (12.4ubuntu1) over (12.4ubuntu1) ...
  Preparing to unpack dkms_2.3-3ubuntu9_all.deb ...
  Unpacking dkms (2.3-3ubuntu9) over (2.3-3ubuntu9) ...
  Preparing to unpack dpkg-dev_1.19.0.5ubuntu2_all.deb ...
  Unpacking dpkg-dev (1.19.0.5ubuntu2) over (1.19.0.5ubuntu2) ...
  Preparing to unpack fakeroot_1.22-2ubuntu1_amd64.deb ...
  Unpacking fakeroot (1.22-2ubuntu1) over (1.22-2ubuntu1) ...
  Preparing to unpack g++_7.4.0-1ubuntu2.3_amd64.deb ...
  Unpacking g++ (4:7.4.0-1ubuntu2.3) over (4:7.4.0-1ubuntu2.3) ...
  Preparing to unpack g++-7_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking g++-7 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack gcc_7.4.0-1ubuntu2.3_amd64.deb ...
  Unpacking gcc (4:7.4.0-1ubuntu2.3) over (4:7.4.0-1ubuntu2.3) ...
  Preparing to unpack gcc-7_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking gcc-7 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libalgorithm-diff-perl_1.19.03-1_all.deb ...
  Unpacking libalgorithm-diff-perl (1.19.03-1) over (1.19.03-1) ...
  Preparing to unpack libalgorithm-diff-xs-perl_0.04-5_amd64.deb ...
  Unpacking libalgorithm-diff-xs-perl (0.04-5) over (0.04-5) ...
  Preparing to unpack libalgorithm-merge-perl_0.08-3_all.deb ...
  Unpacking libalgorithm-merge-perl (0.08-3) over (0.08-3) ...
  Preparing to unpack libasan4_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libasan4:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libatomic1_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libatomic1:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libc6-dev_2.27-3ubuntu1_amd64.deb ...
  Unpacking libc6-dev:amd64 (2.27-3ubuntu1) over (2.27-3ubuntu1) ...
  Preparing to unpack libc-dev-bin_2.27-3ubuntu1_amd64.deb ...
  Unpacking libc-dev-bin (2.27-3ubuntu1) over (2.27-3ubuntu1) ...
  Preparing to unpack libcilkrts5_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libcilkrts5:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libfakeroot_1.22-2ubuntu1_amd64.deb ...
  Unpacking libfakeroot:amd64 (1.22-2ubuntu1) over (1.22-2ubuntu1) ...
  Preparing to unpack libgcc-7-dev_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libgcc-7-dev:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libitm1_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libitm1:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack liblsan0_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking liblsan0:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libmpx2_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libmpx2:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libquadmath0_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libquadmath0:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libstdc++-7-dev_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libstdc++-7-dev:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libtsan0_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libtsan0:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libubsan0_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libubsan0:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack linux-libc-dev_4.15.0-91.92_amd64.deb ...
  Unpacking linux-libc-dev:amd64 (4.15.0-91.92) over (4.15.0-91.92) ...
  Preparing to unpack make_4.1-9.1ubuntu1_amd64.deb ...
  Unpacking make (4.1-9.1ubuntu1) over (4.1-9.1ubuntu1) ...
  Preparing to unpack manpages-dev_4.15-1_all.deb ...
  Unpacking manpages-dev (4.15-1) over (4.15-1) ...
  dpkg: dependency problems prevent configuration of dpkg-dev:
   dpkg-dev depends on libdpkg-perl (= 1.19.0.5ubuntu2); however:
    Version of libdpkg-perl on system is 1.19.0.5ubuntu2.3.
   
  dpkg: error processing package dpkg-dev (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of g++-7:
   g++-7 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package g++-7 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of gcc-7:
   gcc-7 depends on cpp-7 (= 7.5.0-3ubuntu1~18.04); however:
    Version of cpp-7 on system is 7.4.0-1ubuntu1~18.04.1.
   gcc-7 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package gcc-7 (--install):
   dependency problems - leaving unconfigured
  Setting up libalgorithm-diff-perl (1.19.03-1) ...
  Setting up libalgorithm-diff-xs-perl (0.04-5) ...
  Setting up libalgorithm-merge-perl (0.08-3) ...
  dpkg: dependency problems prevent configuration of libasan4:amd64:
   libasan4:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package libasan4:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of libatomic1:amd64:
   libatomic1:amd64 depends on gcc-8-base (= 8.3.0-26ubuntu1~18.04); however:
    Version of gcc-8-base:amd64 on system is 8.3.0-6ubuntu1~18.04.1.
   
  dpkg: error processing package libatomic1:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up libc-dev-bin (2.27-3ubuntu1) ...
  dpkg: dependency problems prevent configuration of libcilkrts5:amd64:
   libcilkrts5:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package libcilkrts5:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up libfakeroot:amd64 (1.22-2ubuntu1) ...
  dpkg: dependency problems prevent configuration of libgcc-7-dev:amd64:
   libgcc-7-dev:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   libgcc-7-dev:amd64 depends on libatomic1 (>= 7.5.0-3ubuntu1~18.04); however:
    Package libatomic1:amd64 is not configured yet.
   libgcc-7-dev:amd64 depends on libasan4 (>= 7.5.0-3ubuntu1~18.04); however:
    Package libasan4:amd64 is not configured yet.
   libgcc-7-dev:amd64 depends on libcilkrts5 (>= 7.5.0-3ubuntu1~18.04); however:
    Package libcilkrts5:amd64 is not configured yet.
   
  dpkg: error processing package libgcc-7-dev:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of libitm1:amd64:
   libitm1:amd64 depends on gcc-8-base (= 8.3.0-26ubuntu1~18.04); however:
    Version of gcc-8-base:amd64 on system is 8.3.0-6ubuntu1~18.04.1.
   
  dpkg: error processing package libitm1:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of liblsan0:amd64:
   liblsan0:amd64 depends on gcc-8-base (= 8.3.0-26ubuntu1~18.04); however:
    Version of gcc-8-base:amd64 on system is 8.3.0-6ubuntu1~18.04.1.
   
  dpkg: error processing package liblsan0:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of libmpx2:amd64:
   libmpx2:amd64 depends on gcc-8-base (= 8.3.0-26ubuntu1~18.04); however:
    Version of gcc-8-base:amd64 on system is 8.3.0-6ubuntu1~18.04.1.
   
  dpkg: error processing package libmpx2:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of libquadmath0:amd64:
   libquadmath0:amd64 depends on gcc-8-base (= 8.3.0-26ubuntu1~18.04); however:
    Version of gcc-8-base:amd64 on system is 8.3.0-6ubuntu1~18.04.1.
   
  dpkg: error processing package libquadmath0:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of libstdc++-7-dev:amd64:
   libstdc++-7-dev:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   libstdc++-7-dev:amd64 depends on libgcc-7-dev (= 7.5.0-3ubuntu1~18.04); however:
    Package libgcc-7-dev:amd64 is not configured yet.
   
  dpkg: error processing package libstdc++-7-dev:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of libtsan0:amd64:
   libtsan0:amd64 depends on gcc-8-base (= 8.3.0-26ubuntu1~18.04); however:
    Version of gcc-8-base:amd64 on system is 8.3.0-6ubuntu1~18.04.1.
   
  dpkg: error processing package libtsan0:amd64 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of libubsan0:amd64:
   libubsan0:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package libubsan0:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up linux-libc-dev:amd64 (4.15.0-91.92) ...
  Setting up make (4.1-9.1ubuntu1) ...
  Setting up manpages-dev (4.15-1) ...
  dpkg: dependency problems prevent configuration of build-essential:
   build-essential depends on dpkg-dev (>= 1.17.11); however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package build-essential (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of dkms:
   dkms depends on dpkg-dev; however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package dkms (--install):
   dependency problems - leaving unconfigured
  Setting up fakeroot (1.22-2ubuntu1) ...
  dpkg: dependency problems prevent configuration of g++:
   g++ depends on g++-7 (>= 7.4.0-1~); however:
    Package g++-7 is not configured yet.
   g++ depends on gcc-7 (>= 7.4.0-1~); however:
    Package gcc-7 is not configured yet.
   
  dpkg: error processing package g++ (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of gcc:
   gcc depends on gcc-7 (>= 7.4.0-1~); however:
    Package gcc-7 is not configured yet.
   
  dpkg: error processing package gcc (--install):
   dependency problems - leaving unconfigured
  Setting up libc6-dev:amd64 (2.27-3ubuntu1) ...
  Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
  Processing triggers for libc-bin (2.27-3ubuntu1) ...
  Errors were encountered while processing:
   dpkg-dev
   g++-7
   gcc-7
   libasan4:amd64
   libatomic1:amd64
   libcilkrts5:amd64
   libgcc-7-dev:amd64
   libitm1:amd64
   liblsan0:amd64
   libmpx2:amd64
   libquadmath0:amd64
   libstdc++-7-dev:amd64
   libtsan0:amd64
   libubsan0:amd64
   build-essential
   dkms
   g++
   gcc
  dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/debs$
```

---

### Post by chili555 on 2020-03-23
Quite a few of the errors seem to want gcc-8-base 8.3.0-26ubuntu1. Please download and install it and try again.

I will be off for the evening. I’ll check in tomorrow.

---

### Post by wildmanne39 on 2020-03-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by kickass1955 on 2020-03-23
ok will do...should i use pastebin for long text?

---

### Post by wildmanne39 on 2020-03-23
You can but it is easier for the people helping you imo if you just wrap the terminal output in code tags.

---

### Post by kickass1955 on 2020-03-23
ok here is new text for you

```
 dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/debs$ sudo dpkg -i *deb
  (Reading database ... 132444 files and directories currently installed.)
  Preparing to unpack build-essential_12.4ubuntu1_amd64.deb ...
  Unpacking build-essential (12.4ubuntu1) over (12.4ubuntu1) ...
  Preparing to unpack dkms_2.3-3ubuntu9_all.deb ...
  Unpacking dkms (2.3-3ubuntu9) over (2.3-3ubuntu9) ...
  Preparing to unpack dpkg-dev_1.19.0.5ubuntu2_all.deb ...
  Unpacking dpkg-dev (1.19.0.5ubuntu2) over (1.19.0.5ubuntu2) ...
  Preparing to unpack fakeroot_1.22-2ubuntu1_amd64.deb ...
  Unpacking fakeroot (1.22-2ubuntu1) over (1.22-2ubuntu1) ...
  Preparing to unpack g++_7.4.0-1ubuntu2.3_amd64.deb ...
  Unpacking g++ (4:7.4.0-1ubuntu2.3) over (4:7.4.0-1ubuntu2.3) ...
  Preparing to unpack g++-7_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking g++-7 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack gcc_7.4.0-1ubuntu2.3_amd64.deb ...
  Unpacking gcc (4:7.4.0-1ubuntu2.3) over (4:7.4.0-1ubuntu2.3) ...
  Preparing to unpack gcc-7_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking gcc-7 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack gcc-8-base_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking gcc-8-base:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libalgorithm-diff-perl_1.19.03-1_all.deb ...
  Unpacking libalgorithm-diff-perl (1.19.03-1) over (1.19.03-1) ...
  Preparing to unpack libalgorithm-diff-xs-perl_0.04-5_amd64.deb ...
  Unpacking libalgorithm-diff-xs-perl (0.04-5) over (0.04-5) ...
  Preparing to unpack libalgorithm-merge-perl_0.08-3_all.deb ...
  Unpacking libalgorithm-merge-perl (0.08-3) over (0.08-3) ...
  Preparing to unpack libasan4_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libasan4:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libatomic1_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libatomic1:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libc6-dev_2.27-3ubuntu1_amd64.deb ...
  Unpacking libc6-dev:amd64 (2.27-3ubuntu1) over (2.27-3ubuntu1) ...
  Preparing to unpack libc-dev-bin_2.27-3ubuntu1_amd64.deb ...
  Unpacking libc-dev-bin (2.27-3ubuntu1) over (2.27-3ubuntu1) ...
  Preparing to unpack libcilkrts5_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libcilkrts5:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libfakeroot_1.22-2ubuntu1_amd64.deb ...
  Unpacking libfakeroot:amd64 (1.22-2ubuntu1) over (1.22-2ubuntu1) ...
  Preparing to unpack libgcc-7-dev_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libgcc-7-dev:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libitm1_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libitm1:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack liblsan0_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking liblsan0:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libmpx2_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libmpx2:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libquadmath0_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libquadmath0:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libstdc++-7-dev_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libstdc++-7-dev:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack libtsan0_8.3.0-26ubuntu1~18.04_amd64.deb ...
  Unpacking libtsan0:amd64 (8.3.0-26ubuntu1~18.04) over (8.3.0-26ubuntu1~18.04) ...
  Preparing to unpack libubsan0_7.5.0-3ubuntu1~18.04_amd64.deb ...
  Unpacking libubsan0:amd64 (7.5.0-3ubuntu1~18.04) over (7.5.0-3ubuntu1~18.04) ...
  Preparing to unpack linux-libc-dev_4.15.0-91.92_amd64.deb ...
  Unpacking linux-libc-dev:amd64 (4.15.0-91.92) over (4.15.0-91.92) ...
  Preparing to unpack make_4.1-9.1ubuntu1_amd64.deb ...
  Unpacking make (4.1-9.1ubuntu1) over (4.1-9.1ubuntu1) ...
  Preparing to unpack manpages-dev_4.15-1_all.deb ...
  Unpacking manpages-dev (4.15-1) over (4.15-1) ...
  dpkg: dependency problems prevent configuration of dpkg-dev:
   dpkg-dev depends on libdpkg-perl (= 1.19.0.5ubuntu2); however:
    Version of libdpkg-perl on system is 1.19.0.5ubuntu2.3.
   
  dpkg: error processing package dpkg-dev (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of g++-7:
   g++-7 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package g++-7 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of gcc-7:
   gcc-7 depends on cpp-7 (= 7.5.0-3ubuntu1~18.04); however:
    Version of cpp-7 on system is 7.4.0-1ubuntu1~18.04.1.
   gcc-7 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package gcc-7 (--install):
   dependency problems - leaving unconfigured
  Setting up gcc-8-base:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libalgorithm-diff-perl (1.19.03-1) ...
  Setting up libalgorithm-diff-xs-perl (0.04-5) ...
  Setting up libalgorithm-merge-perl (0.08-3) ...
  dpkg: dependency problems prevent configuration of libasan4:amd64:
   libasan4:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package libasan4:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up libatomic1:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libc-dev-bin (2.27-3ubuntu1) ...
  dpkg: dependency problems prevent configuration of libcilkrts5:amd64:
   libcilkrts5:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package libcilkrts5:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up libfakeroot:amd64 (1.22-2ubuntu1) ...
  dpkg: dependency problems prevent configuration of libgcc-7-dev:amd64:
   libgcc-7-dev:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   libgcc-7-dev:amd64 depends on libasan4 (>= 7.5.0-3ubuntu1~18.04); however:
    Package libasan4:amd64 is not configured yet.
   libgcc-7-dev:amd64 depends on libcilkrts5 (>= 7.5.0-3ubuntu1~18.04); however:
    Package libcilkrts5:amd64 is not configured yet.
   
  dpkg: error processing package libgcc-7-dev:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up libitm1:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up liblsan0:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libmpx2:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libquadmath0:amd64 (8.3.0-26ubuntu1~18.04) ...
  dpkg: dependency problems prevent configuration of libstdc++-7-dev:amd64:
   libstdc++-7-dev:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   libstdc++-7-dev:amd64 depends on libgcc-7-dev (= 7.5.0-3ubuntu1~18.04); however:
    Package libgcc-7-dev:amd64 is not configured yet.
   
  dpkg: error processing package libstdc++-7-dev:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up libtsan0:amd64 (8.3.0-26ubuntu1~18.04) ...
  dpkg: dependency problems prevent configuration of libubsan0:amd64:
   libubsan0:amd64 depends on gcc-7-base (= 7.5.0-3ubuntu1~18.04); however:
    Version of gcc-7-base:amd64 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package libubsan0:amd64 (--install):
   dependency problems - leaving unconfigured
  Setting up linux-libc-dev:amd64 (4.15.0-91.92) ...
  Setting up make (4.1-9.1ubuntu1) ...
  Setting up manpages-dev (4.15-1) ...
  dpkg: dependency problems prevent configuration of build-essential:
   build-essential depends on dpkg-dev (>= 1.17.11); however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package build-essential (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of dkms:
   dkms depends on dpkg-dev; however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package dkms (--install):
   dependency problems - leaving unconfigured
  Setting up fakeroot (1.22-2ubuntu1) ...
  dpkg: dependency problems prevent configuration of g++:
   g++ depends on g++-7 (>= 7.4.0-1~); however:
    Package g++-7 is not configured yet.
   g++ depends on gcc-7 (>= 7.4.0-1~); however:
    Package gcc-7 is not configured yet.
   
  dpkg: error processing package g++ (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of gcc:
   gcc depends on gcc-7 (>= 7.4.0-1~); however:
    Package gcc-7 is not configured yet.
   
  dpkg: error processing package gcc (--install):
   dependency problems - leaving unconfigured
  Setting up libc6-dev:amd64 (2.27-3ubuntu1) ...
  Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
  Processing triggers for libc-bin (2.27-3ubuntu1) ...
  Errors were encountered while processing:
   dpkg-dev
   g++-7
   gcc-7
   libasan4:amd64
   libcilkrts5:amd64
   libgcc-7-dev:amd64
   libstdc++-7-dev:amd64
   libubsan0:amd64
   build-essential
   dkms
   g++
   gcc
  dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/debs$
```

---

### Post by kickass1955 on 2020-03-23
i dont know how to do that...plz show me

---

### Post by chili555 on 2020-03-24
Now it wants gcc-7-base 7.5.0-3ubuntu1. Please download and install it and try again.

It is useless to try to build the driver until every one of the prerequisites is successfully installed. Just one step at a time.

---

### Post by kickass1955 on 2020-03-24
ok i am here till 11 pm est
will try and let you know

---

### Post by kickass1955 on 2020-03-24
ok back...it is getting shorter...i think we are making progress...i only copied the problems to make it easier to go thru.  here:

 dpkg: dependency problems prevent configuration of dpkg-dev:
   dpkg-dev depends on libdpkg-perl (= 1.19.0.5ubuntu2); however:
    Version of libdpkg-perl on system is 1.19.0.5ubuntu2.3.
   
  dpkg: error processing package dpkg-dev (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of gcc-7:
   gcc-7 depends on cpp-7 (= 7.5.0-3ubuntu1~18.04); however:
    Version of cpp-7 on system is 7.4.0-1ubuntu1~18.04.1.
   
  dpkg: error processing package gcc-7 (--install):
   dependency problems - leaving unconfigured
  Setting up gcc-7-base:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up gcc-8-base:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libalgorithm-diff-perl (1.19.03-1) ...
  Setting up libalgorithm-diff-xs-perl (0.04-5) ...
  Setting up libalgorithm-merge-perl (0.08-3) ...
  Setting up libasan4:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up libatomic1:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libc-dev-bin (2.27-3ubuntu1) ...
  Setting up libcilkrts5:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up libfakeroot:amd64 (1.22-2ubuntu1) ...
  Setting up libitm1:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up liblsan0:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libmpx2:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libquadmath0:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libtsan0:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libubsan0:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up linux-libc-dev:amd64 (4.15.0-91.92) ...
  Setting up make (4.1-9.1ubuntu1) ...
  Setting up manpages-dev (4.15-1) ...
  dpkg: dependency problems prevent configuration of build-essential:
   build-essential depends on dpkg-dev (>= 1.17.11); however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package build-essential (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of dkms:
   dkms depends on dpkg-dev; however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package dkms (--install):
   dependency problems - leaving unconfigured
  Setting up fakeroot (1.22-2ubuntu1) ...
  dpkg: dependency problems prevent configuration of g++:
   g++ depends on gcc-7 (>= 7.4.0-1~); however:
    Package gcc-7 is not configured yet.
   
  dpkg: error processing package g++ (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of g++-7:
   g++-7 depends on gcc-7 (= 7.5.0-3ubuntu1~18.04); however:
    Package gcc-7 is not configured yet.
   
  dpkg: error processing package g++-7 (--install):
   dependency problems - leaving unconfigured
  dpkg: dependency problems prevent configuration of gcc:
   gcc depends on gcc-7 (>= 7.4.0-1~); however:
    Package gcc-7 is not configured yet.
   
  dpkg: error processing package gcc (--install):
   dependency problems - leaving unconfigured
  Setting up libc6-dev:amd64 (2.27-3ubuntu1) ...
  Setting up libgcc-7-dev:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up libstdc++-7-dev:amd64 (7.5.0-3ubuntu1~18.04) ...
  Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
  Processing triggers for libc-bin (2.27-3ubuntu1) ...
  Errors were encountered while processing:
   dpkg-dev
   gcc-7
   build-essential
   dkms
   g++
   g++-7
   gcc
  dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/debs$ sudo dpkg -i *.deb


12 problems down to 7 ...i need to learn more...thank youn for all your help...i haven"t touch ubuntu in 6 years....i miss it.  this laptop is dual boot now... just need the wireless drivers

---

### Post by kickass1955 on 2020-03-24
well i saw another problem and installed  cpp_7.7.5.0 and ran whole install again and got less errors....here is what i have now....hope i did not screw it up....looks like 3 errors or dependencies 

 dpkg: dependency problems prevent configuration of dpkg-dev:
   dpkg-dev depends on libdpkg-perl (= 1.19.0.5ubuntu2); however:
    Version of libdpkg-perl on system is 1.19.0.5ubuntu2.3.
   
  dpkg: error processing package dpkg-dev (--install):
   dependency problems - leaving unconfigured
  Setting up gcc-7-base:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up gcc-8-base:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libalgorithm-diff-perl (1.19.03-1) ...
  Setting up libalgorithm-diff-xs-perl (0.04-5) ...
  Setting up libalgorithm-merge-perl (0.08-3) ...
  Setting up libasan4:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up libatomic1:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libc-dev-bin (2.27-3ubuntu1) ...
  Setting up libcilkrts5:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up libfakeroot:amd64 (1.22-2ubuntu1) ...
  Setting up libitm1:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up liblsan0:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libmpx2:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libquadmath0:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libtsan0:amd64 (8.3.0-26ubuntu1~18.04) ...
  Setting up libubsan0:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up linux-libc-dev:amd64 (4.15.0-91.92) ...
  Setting up make (4.1-9.1ubuntu1) ...
  Setting up manpages-dev (4.15-1) ...
  dpkg: dependency problems prevent configuration of build-essential:
   build-essential depends on dpkg-dev (>= 1.17.11); however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package build-essential (--install):
   dependency problems - leaving unconfigured
  Setting up cpp-7 (7.5.0-3ubuntu1~18.04) ...
  dpkg: dependency problems prevent configuration of dkms:
   dkms depends on dpkg-dev; however:
    Package dpkg-dev is not configured yet.
   
  dpkg: error processing package dkms (--install):
   dependency problems - leaving unconfigured
  Setting up fakeroot (1.22-2ubuntu1) ...
  Setting up libc6-dev:amd64 (2.27-3ubuntu1) ...
  Setting up libgcc-7-dev:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up libstdc++-7-dev:amd64 (7.5.0-3ubuntu1~18.04) ...
  Setting up gcc-7 (7.5.0-3ubuntu1~18.04) ...
  Setting up g++-7 (7.5.0-3ubuntu1~18.04) ...
  Setting up gcc (4:7.4.0-1ubuntu2.3) ...
  Setting up g++ (4:7.4.0-1ubuntu2.3) ...
  update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
  Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
  Processing triggers for libc-bin (2.27-3ubuntu1) ...
  Errors were encountered while processing:
   dpkg-dev
   build-essential
   dkms
  dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/debs$

---

### Post by chili555 on 2020-03-24
Please go get and install libdpkg-perl 1.19.0.5ubuntu2. We may be just about there!

---

### Post by kickass1955 on 2020-03-24
ok will do....be back in ten minutes

---

### Post by kickass1955 on 2020-03-24
ok...installed perl....ran all and no errors....whoo...hoo....now what?

---

### Post by kickass1955 on 2020-03-24
ok...tried to install by directions on page you gave me...here is what i got....it is at least short.....

 dominic@dominic-HP-Laptop-15-db1xxx:~$ cd ~/Downloads/rtl8821ce
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ dir
  clean  hal           ifcfg-wlan0  Kconfig  os_dep    rtl8821c.mk wlan0dhcp
  core   halmac.mk  include      Makefile  platform  runwpa
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ make
  make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.3.0-28-generic/build M=/home/dominic/Downloads/rtl8821ce  modules
  make[1]: Entering directory '/usr/src/linux-headers-5.3.0-28-generic'
  /home/dominic/Downloads/rtl8821ce/Makefile:2157: home/dominic/Downloads/rtl8821ce/hal/phydm/phydm.mk: No such file or directory
  /home/dominic/Downloads/rtl8821ce/Makefile:2166: home/dominic/Downloads/rtl8821ce/rtl8821c.mk: No such file or directory
  make[2]: *** No rule to make target 'home/dominic/Downloads/rtl8821ce/rtl8821c.mk'.  Stop.
  Makefile:1655: recipe for target '_module_/home/dominic/Downloads/rtl8821ce' failed
  make[1]: *** [_module_/home/dominic/Downloads/rtl8821ce] Error 2
  make[1]: Leaving directory '/usr/src/linux-headers-5.3.0-28-generic'
  Makefile:2237: recipe for target 'modules' failed
  make: *** [modules] Error 2
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ sudo make install
  [sudo] password for dominic:
  install -p -m 644 8821ce.ko  /lib/modules/5.3.0-28-generic/kernel/drivers/net/wireless/
  install: cannot stat '8821ce.ko': No such file or directory
  Makefile:2243: recipe for target 'install' failed
  make: *** [install] Error 1
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$ sudo modprobe 8821ce
  modprobe: FATAL: Module 8821ce not found in directory /lib/modules/5.3.0-28-generic
  dominic@dominic-HP-Laptop-15-db1xxx:~/Downloads/rtl8821ce$

---

### Post by kickass1955 on 2020-03-24
my bad....disregard this post.......

---

### Post by wildmanne39 on 2020-03-24
All support is done here on the forum so everyone who has this same issue can benefit from the answer, asking for phone support is very inappropriate.

---

### Post by kickass1955 on 2020-03-24
my bad....will not happen again....plz forgive....

---

### Post by wildmanne39 on 2020-03-24
> **kickass1955 said:**
> my bad....will not happen again....plz forgive....
No worries.

---

### Post by chili555 on 2020-03-24
Download this file instead and transfer it to the desktop of the Ubuntu machine: [https://github.com/tomaspinho/rtl8821ce/archive/master.zip](https://github.com/tomaspinho/rtl8821ce/archive/master.zip)

Now do:

```
cd ~/Desktop
unzip master.zip
cd rtl8821ce-master
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh   
sudo modprobe 8821ce
```

Your wireless should now be working.

---

### Post by kickass1955 on 2020-03-24
ok will try this....be back in 20 minutes....

---

### Post by kickass1955 on 2020-03-24
ok back,  ...
here is error...

dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop$ cd rtl8821ce-master
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$ chmod +x dkms-install .sh
chmod: cannot access 'dkms-install': No such file or directory
chmod: cannot access '.sh': No such file or directory
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$ chmod +x dkms install .sh
chmod: cannot access 'dkms': No such file or directory
chmod: cannot access 'install': No such file or directory
chmod: cannot access '.sh': No such file or directory
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$ chmod +x dkms-install .sh
chmod: cannot access 'dkms-install': No such file or directory
chmod: cannot access '.sh': No such file or directory
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$

---

### Post by chili555 on 2020-03-24
>  chmod +x dkms-install .shI believe you have an extra space in there. It is not dkms-install<space>.sh.

There is no space at all. It is dkms-install.sh and not dkms-install .sh. Please try again.

---

### Post by kickass1955 on 2020-03-24
ok ,....my bad....brb   10 minutes

---

### Post by kickass1955 on 2020-03-24
ok back....no wireless....one error or more...i do not know


ominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$ chmod +x dkms-install.sh
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$ chmod +x dkms-remove.sh
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$ sudo ./dkms-install.sh
[sudo] password for dominic: 
About to run dkms install steps...

Creating symlink /var/lib/dkms/rtl8821ce/v5.5.2_34066.20190614/source ->
                 /usr/src/rtl8821ce-v5.5.2_34066.20190614

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j8 KVER=5.3.0-28-generic..........
cleaning build area...

DKMS: build completed.

8821ce:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.3.0-28-generic/updates/dkms/

depmod...

DKMS: install completed.
Finished running dkms install steps.
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$ sudo modprobe 8821ce
modprobe: ERROR: could not insert '8821ce': Operation not permitted
dominic@dominic-HP-Laptop-15-db1xxx:~/Desktop/rtl8821ce-master$

---

### Post by chili555 on 2020-03-24
You will probably just need to disable Secure Boot in the BIOS/EFI.

Off for the evening.

Enjoy your new wireless!

---

### Post by kickass1955 on 2020-03-24
ok will do that and try again....thanks for all the help....will post if i still have a problem....again thanks

---

### Post by kickass1955 on 2020-03-25
just stopped in to let you know all is working...only one problem....after ubuntu sits there for 20 seconds....a error pops up and says do you want to report problem....i say yes but don't know what problem is or how to address it....all is updated....runs great except for error message....once again, thank you for all your help....i have some learning to do again....thanks

---

### Post by kickass1955 on 2020-03-25
this thread can now be finished.....hope all this helps some one else like it did me

---

### Post by chili555 on 2020-03-25
> **kickass1955 said:**
> this thread can now be finished.....hope all this helps some one else like it did meIt will help much better if you use thread tools at the top to mark Solved.

Glad it's working.

---

### Post by kickass1955 on 2020-03-25
ok, did that...what thread do i use for the minor error message?  And again thanks for all your help...

---

### Post by chili555 on 2020-03-25
> **kickass1955 said:**
> ok, did that...what thread do i use for the minor error message?  And again thanks for all your help...Please try here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by brentallenk on 2020-04-05
I am having the same problem with the same system. I have followed all the steps and this is what comes up at the end:

```

kramer@kramer-HP-Laptop-14-dk0xxx:~$ sudo apt install git dkms build-essential
[sudo] password for kramer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.4ubuntu1).
dkms is already the newest version (2.3-3ubuntu9.7).
git is already the newest version (1:2.17.1-1ubuntu0.5).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kramer@kramer-HP-Laptop-14-dk0xxx:~$ git clone https://github.com/tomaspinho/rtl8821ce.git
fatal: destination path 'rtl8821ce' already exists and is not an empty directory.
kramer@kramer-HP-Laptop-14-dk0xxx:~$ cd rtl8821ce
kramer@kramer-HP-Laptop-14-dk0xxx:~/rtl8821ce$ sudo ./dkms-install.sh
About to run dkms install steps...
Error! DKMS tree already contains: rtl8821ce-v5.5.2_34066.20200325
You cannot add the same module/version combo more than once.
Module rtl8821ce/v5.5.2_34066.20200325 already built for kernel 5.3.0-45-generic/4
Module rtl8821ce/v5.5.2_34066.20200325 already installed on kernel 5.3.0-45-generic/x86_64
Finished running dkms install steps.
kramer@kramer-HP-Laptop-14-dk0xxx:~/rtl8821ce$ 

```
[h=1][/h]

---

### Post by brentallenk on 2020-04-05
After another reboot, somehow my wi-fi is now working! Glory!

---

