---
title: "error making rtl8101e driver"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by bazzle. on 2008-05-04
I followed the instructions in the readme for the realtek linux driver for the rtl8101e ethernet card and after the first step received the following response:

bazzle@bazzle-laptop:~$ cd /home/bazzle/Desktop/r8101-1.007.00
bazzle@bazzle-laptop:~/Desktop/r8101-1.007.00$ sudo make clean modules
[sudo] password for bazzle:
make -C src/ clean
make[1]: Entering directory `/home/bazzle/Desktop/r8101-1.007.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/bazzle/Desktop/r8101-1.007.00/src'
make -C src/ modules
make[1]: Entering directory `/home/bazzle/Desktop/r8101-1.007.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'. Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/bazzle/Desktop/r8101-1.007.00/src'
make: *** [modules] Error 2
bazzle@bazzle-laptop:~/Desktop/r8101-1.007.00$

The driver file is attached.
Please help, I would really like to get this card working.

---

### Post by quadrispro on 2008-06-14
I have this problem:

```

alessio@quadrispro-laptop:~/Scrivania/r8101-1.007.00$ make modules
make -C src/ modules
make[1]: Entering directory `/home/alessio/Scrivania/r8101-1.007.00/src'
make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/alessio/Scrivania/r8101-1.007.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.o
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c: In function &#8216;rtl8101_init_board&#8217;:
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:2244: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c: In function &#8216;rtl8101_init_one&#8217;:
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:2643: error: &#8216;struct net_device&#8217; has no member named &#8216;poll&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:2644: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c: In function &#8216;rtl8101_rx_interrupt&#8217;:
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3686: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3686: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_y&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3686: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3686: warning: comparison of distinct pointer types lacks a cast
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c: In function &#8216;rtl8101_interrupt&#8217;:
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3866: error: too few arguments to function &#8216;netif_rx_schedule_prep&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3867: error: too few arguments to function &#8216;__netif_rx_schedule&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c: In function &#8216;rtl8101_poll&#8217;:
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3913: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3913: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_y&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3913: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3921: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.c:3924: error: too few arguments to function &#8216;netif_rx_complete&#8217;
make[3]: *** [/home/alessio/Scrivania/r8101-1.007.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/alessio/Scrivania/r8101-1.007.00/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/alessio/Scrivania/r8101-1.007.00/src'
make: *** [modules] Error 2

```

---

### Post by quadrispro on 2008-06-27
The driver doesn't support kernel 2.6.24, I prepared a patch [link]("http://www.alessiotreglia.com/wp-content/uploads/r8101-1.007.00.hardy.diff.txt")

---

### Post by kogz on 2008-07-06
> **quadrispro said:**
> The driver doesn't support kernel 2.6.24, I prepared a patch [link]("http://www.alessiotreglia.com/wp-content/uploads/r8101-1.007.00.hardy.diff.txt")

Can you tell us how to apply this patch? Thanks.

//edit

patch < r8101-1.007.00.hardy.diff.txt

nevermind. thanks.

---

### Post by thi3d on 2008-08-18
I get the exact same error messages as bazzle, even though I've patched the driver... 

```
marcus@woodie:~$ sudo patch < r8101-1.007.00.hardy.diff 
can't find file to patch at input line 4
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ruN ../r8101-1.007.00/src/r8101.h ./src/r8101.h
|--- ../r8101-1.007.00/src/r8101.h	2008-03-31 09:57:16.000000000 +0200
|+++ ./src/r8101.h	2008-06-27 15:20:21.000000000 +0200
--------------------------
File to patch: ./r8101-1.007.00/src/r8101.h
patching file ./r8101-1.007.00/src/r8101.h
can't find file to patch at input line 15
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ruN ../r8101-1.007.00/src/r8101_n.c ./src/r8101_n.c
|--- ../r8101-1.007.00/src/r8101_n.c	2008-03-31 09:53:47.000000000 +0200
|+++ ./src/r8101_n.c	2008-06-27 15:20:21.000000000 +0200
--------------------------
File to patch: ./r8101-1.007.00/src/r8101_n.c
patching file ./r8101-1.007.00/src/r8101_n.c

marcus@woodie:~$ cd r8101-1.007.00/

marcus@woodie:~/r8101-1.007.00$ sudo make clean modules 
make -C src/ clean
make[1]: Entering directory `/home/marcus/r8101-1.007.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/marcus/r8101-1.007.00/src'
make -C src/ modules
make[1]: Entering directory `/home/marcus/r8101-1.007.00/src'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/marcus/r8101-1.007.00/src'
make: *** [modules] Error 2

```


I'm using Hardy on a D945gclf motherboard...

Would be very thankful for any help!

---

### Post by ludw on 2008-09-01
I think you need the kernel headers for your kernel...

[http://ubuntuforums.org/showpost.php?p=27384&postcount=2](http://ubuntuforums.org/showpost.php?p=27384&postcount=2)

---

### Post by newlin on 2008-09-08
The latest Ubuntu 8.10 Intrepid Alfa 5  sees the RTL8101E but cannot DHCP.  All other versions of Ubuntu have the same problem.  
Realtek have new drivers as do Intel.  Driver install scripts running Ubuntu do not work.  As a newbie where to do from here?   
TIA.

---

### Post by kogz on 2008-09-08
Well.. Set static IP to be sure this is only DHCP issue.

You must patch realtek files before trying install.

---

### Post by bobe84 on 2008-09-08
I have Intel D945GCLF board with Realtek 8101E.
1)find module r8169.ko it's located in /lib/modules/<<kernel version>>/kernel/drivers/net/ and delete it...
2 )do sudo update-initrams -u
3 )download realtek driver from their site
for example [ftp://66.104.77.130/cn/nic/r8101-1.009.00.tar.bz2](ftp://66.104.77.130/cn/nic/r8101-1.009.00.tar.bz2)
4 )**extract driver to /root**
5 )sudo -i
6 )go to driver folder
7 )make
8 )make install
9 )depmod -a
10 )edit /etc/modules and add **r8101** driver to list

this is working on hardy 64bit, intel d945glcf board...

---

### Post by newlin on 2008-09-08
Thanks

The "extract driver to \root" has solved the error 2 problem.
Is this the case with all drivers?  There is very little documentation on this.

---

### Post by cdnaerogeek on 2008-09-11
I'm trying to install version 1.009 of the same driver, (I have the same network card,) but I'm having some difficulty with the instructions. Specifically, my computer won't let me rmmod r8169, and I can't find the file to edit that will let me rmmod that driver.

I'm running Ubuntu 8.04 64-bit on my laptop. I get the following output from lspci for reference:
```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
```

Also, the instructions ask me to set a bunch of IP addresses manually, but I don't know where to find them. Can someone please point me in the right direction?

Here's a [[COLOR="Blue"]_link_[/COLOR]]("ftp://61.56.86.122/cn/nic/r8101-1.009.00.tar.bz2") to the driver download, I'm taking these instructions from the README file inside the tarball.

---

### Post by copleykj on 2008-09-21
> **bobe84 said:**
> I have Intel D945GCLF board with Realtek 8101E.
1)find module r8169.ko it's located in /lib/modules/<<kernel version>>/kernel/drivers/net/ and delete it...
2 )do sudo update-initrams -u
3 )download realtek driver from their site
for example [ftp://66.104.77.130/cn/nic/r8101-1.009.00.tar.bz2](ftp://66.104.77.130/cn/nic/r8101-1.009.00.tar.bz2)
4 )**extract driver to /root**
5 )sudo -i
6 )go to driver folder
7 )make
8 )make install
9 )depmod -a
10 )edit /etc/modules and add **r8101** driver to list

this is working on hardy 64bit, intel d945glcf board...

Thank you! My god, I have searched literally for the last 2 days straight for a solution for this problem. There are hundreds that don't work.. Fortunately this worked great! Might as well call this thread solved :)

---

### Post by Arthur Millar on 2008-11-10
> **bazzle. said:**
> I followed the instructions in the readme for the realtek linux driver for the rtl8101e ethernet card and after the first step received the following response:

bazzle@bazzle-laptop:~$ cd /home/bazzle/Desktop/r8101-1.007.00
bazzle@bazzle-laptop:~/Desktop/r8101-1.007.00$ sudo make clean modules
[sudo] password for bazzle:
make -C src/ clean
make[1]: Entering directory `/home/bazzle/Desktop/r8101-1.007.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/bazzle/Desktop/r8101-1.007.00/src'
make -C src/ modules
make[1]: Entering directory `/home/bazzle/Desktop/r8101-1.007.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'. Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/bazzle/Desktop/r8101-1.007.00/src'
make: *** [modules] Error 2
bazzle@bazzle-laptop:~/Desktop/r8101-1.007.00$

Please help, I would really like to get this card working.
 i had this problem too man was i pissed 
i have had this driver working perfectly until i upgraded to ubuntu studio 
i didnt disable my propriatry drivers before the install 
so the r8101 module was blacklisted somewhere!!!
I looked under my modprobe.d and used search to find r8101 
nothing so i did a reinstall it works now still didnt find a way around that though

---

### Post by kogz on 2008-11-10
I've done kernel upgrade last time, and I had to remove from blacklist generic realtek network driver. So I use old one, and now it works good.

---

