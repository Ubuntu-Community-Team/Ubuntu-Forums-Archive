---
title: "Problems with orinico_cs drivers,"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by xof7 on 2007-05-20
I'm trying to get my agere mini-pci wireless card into monitor mode to run airodump, etc.
I was able to with windows but now I am using feisty fawn and have read that I need to use a different driver. 
This is kind of a big poke in the blue but could i use the xp drivers and use ndiswrapper? or is that a completely stupid thought?

The drivers that I am trying to compile are "orinoco-0.13-26-r1.tar.gz". I try to sudo make them but I get a bunch of warnings and two errors. I have tried to fix a couple of them, one of them was it needing config.h in the kernel directory, but I dont understand the rest of them.
the card has a hermes chipset
```
eth1      IEEE 802.11b  ESSID:"article7."  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:2C:6A:A8   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/92  Signal level=-61 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
```
x@bengal:~/Desktop/orinoco$ sudo make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/x/Desktop/orinoco modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/x/Desktop/orinoco/orinoco.o
In file included from /home/x/Desktop/orinoco/orinoco.c:419:
include/linux/config.h:6:7: warning: no newline at end of file
In file included from /home/x/Desktop/orinoco/orinoco.c:442:
/home/x/Desktop/orinoco/hermes.h: In function &#8216;hermes_present&#8217;:
/home/x/Desktop/orinoco/hermes.h:391: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/hermes.h: In function &#8216;hermes_set_irqmask&#8217;:
/home/x/Desktop/orinoco/hermes.h:397: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/hermes.h: In function &#8216;hermes_read_words&#8217;:
/home/x/Desktop/orinoco/hermes.h:440: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/hermes.h: In function &#8216;hermes_write_words&#8217;:
/home/x/Desktop/orinoco/hermes.h:460: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/hermes.h: In function &#8216;hermes_clear_words&#8217;:
/home/x/Desktop/orinoco/hermes.h:476: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
In file included from /home/x/Desktop/orinoco/orinoco.c:444:
/home/x/Desktop/orinoco/orinoco.h: At top level:
/home/x/Desktop/orinoco/orinoco.h:86: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;uint8_t[16]&#8217;
/home/x/Desktop/orinoco/orinoco.h:217: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;char[16]&#8217;
/home/x/Desktop/orinoco/orinoco.c:465: error: expected &#8216;)&#8217; before string constant
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;__orinoco_down&#8217;:
/home/x/Desktop/orinoco/orinoco.c:670: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;orinoco_reset&#8217;:
/home/x/Desktop/orinoco/orinoco.c:1007: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;orinoco_interrupt&#8217;:
/home/x/Desktop/orinoco/orinoco.c:1480: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c:1524: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c:1526: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;__orinoco_ev_info&#8217;:
/home/x/Desktop/orinoco/orinoco.c:1604: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;__orinoco_ev_rx&#8217;:
/home/x/Desktop/orinoco/orinoco.c:1765: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;__orinoco_ev_txexc&#8217;:
/home/x/Desktop/orinoco/orinoco.c:1933: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c:1981: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;__orinoco_ev_tx&#8217;:
/home/x/Desktop/orinoco/orinoco.c:1991: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;__orinoco_ev_alloc&#8217;:
/home/x/Desktop/orinoco/orinoco.c:1998: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c:2009: warning: passing argument 2 of &#8216;writew&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;orinoco_tx_timeout&#8217;:
/home/x/Desktop/orinoco/orinoco.c:2612: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c:2613: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c:2613: warning: passing argument 1 of &#8216;readw&#8217; makes pointer from integer without a cast
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;orinoco_ioctl&#8217;:
/home/x/Desktop/orinoco/orinoco.c:4721: warning: implicit declaration of function &#8216;verify_area&#8217;
/home/x/Desktop/orinoco/orinoco.c:4755: warning: passing argument 3 of &#8216;orinoco_ioctl_setport3&#8217; from incompatible pointer type
/home/x/Desktop/orinoco/orinoco.c:4755: error: too many arguments to function &#8216;orinoco_ioctl_setport3&#8217;
/home/x/Desktop/orinoco/orinoco.c:4759: warning: passing argument 3 of &#8216;orinoco_ioctl_getport3&#8217; from incompatible pointer type
/home/x/Desktop/orinoco/orinoco.c:4759: error: too many arguments to function &#8216;orinoco_ioctl_getport3&#8217;
/home/x/Desktop/orinoco/orinoco.c:4781: error: too few arguments to function &#8216;orinoco_ioctl_setibssport&#8217;
/home/x/Desktop/orinoco/orinoco.c:4785: warning: passing argument 3 of &#8216;orinoco_ioctl_getibssport&#8217; from incompatible pointer type
/home/x/Desktop/orinoco/orinoco.c:4785: error: too many arguments to function &#8216;orinoco_ioctl_getibssport&#8217;
/home/x/Desktop/orinoco/orinoco.c:4806: warning: too many arguments for format
/home/x/Desktop/orinoco/orinoco.c:4810: error: &#8216;changed&#8217; undeclared (first use in this function)
/home/x/Desktop/orinoco/orinoco.c:4810: error: (Each undeclared identifier is reported only once
/home/x/Desktop/orinoco/orinoco.c:4810: error: for each function it appears in.)
/home/x/Desktop/orinoco/orinoco.c:4472: warning: unused variable &#8216;flags&#8217;
/home/x/Desktop/orinoco/orinoco.c:4471: warning: unused variable &#8216;tmp&#8217;
/home/x/Desktop/orinoco/orinoco.c: In function &#8216;alloc_orinocodev&#8217;:
/home/x/Desktop/orinoco/orinoco.c:5033: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
/home/x/Desktop/orinoco/orinoco.c:5036: error: &#8216;orinoco_handler_def&#8217; undeclared (first use in this function)
/home/x/Desktop/orinoco/orinoco.c:5057:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/x/Desktop/orinoco/orinoco.c:5057: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
make[2]: *** [/home/x/Desktop/orinoco/orinoco.o] Error 1
make[1]: *** [_module_/home/x/Desktop/orinoco] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
x@bengal:~/Desktop/orinoco$ 


```

Can anyone help?
thanks

---

### Post by tturrisi on 2007-05-20
> I was able to with windows
Exactly how did you do this?  Monitor mode is impossible in windows using windows drivers and also ndiswrapper using windows drivers will not support monitor mode.  It can't be done.

There are patched orinoco drivers that support monitor mode.  See this thread:
[http://ubuntuforums.org/showthread.php?t=286621&highlight=orinoco](http://ubuntuforums.org/showthread.php?t=286621&highlight=orinoco)

---

### Post by xof7 on 2007-05-20
I'm sorry i worded that incorrectly. I was able to get the wireless card to capture data from 802.11b via the peek drivers.  That method that you posted a link to doesnt work for me. It doesnt compile anything when I make it. I still get a page full of errors and no .ko files.
```
x@bengal:~/Desktop/orinoco-0.13e-SN-14$ sudo makemake -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/x/Desktop/orinoco-0.13e-SN-14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/x/Desktop/orinoco-0.13e-SN-14/orinoco.o
In file included from /home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c:419:
include/linux/config.h:6:7: warning: no newline at end of file
In file included from /home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c:444:
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.h:86: warning: ‘packed’ attribute ignored for field of type ‘uint8_t[16]’
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.h:217: warning: ‘packed’ attribute ignored for field of type ‘char[16]’
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c: In function ‘alloc_orinocodev’:
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c:5141: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c:5166:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c:5166: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c:5166: error: (Each undeclared identifier is reported only once
/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.c:5166: error: for each function it appears in.)
make[2]: *** [/home/x/Desktop/orinoco-0.13e-SN-14/orinoco.o] Error 1
make[1]: *** [_module_/home/x/Desktop/orinoco-0.13e-SN-14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

```

---

### Post by xof7 on 2007-05-21
Anybody?

---

### Post by xof7 on 2007-05-23
I've also had problems with the wireless card showing up in the network selection.
Where it lists the wired and wireless networks. Could this be driver related? or something with ubuntu itself?

---

