---
title: "Install driver for my wifi card (intel 3945abg)"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by tweedi2 on 2013-09-05
Hi everyone ! 

I looked everwhere on the net to find how to install the driver for my built-in wifi card. Apparently I had to install the ipwraw-ng driver (other people speak about iwlwifi)

So i followed a topic to install this ipwraw-ng driver:

1 - sudo apt-get install build-essential
2 - sudo apt-get install libssl-dev
3 - wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2)
4 - tar -xjf ipwraw-ng*
5 - cd ipwraw-ng 
6 - make

And when i type this last command it doest not work:

> make -C /lib/modules/2.6.30.9/build M=/root/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-source-2.6.30.9'

WARNING: Symbol version dump /usr/src/linux-source-2.6.30.9/Module.symvers
is missing; modules will have no dependencies and modversions.

CC [M] /root/ipwraw-ng/ipwraw.o
/root/ipwraw-ng/ipwraw.c:43:27: error: net/ieee80211.h: No such file or director
y
In file included from /root/ipwraw-ng/ipwraw.h:51,
from /root/ipwraw-ng/ipwraw.c:48:
/root/ipwraw-ng/iwlwifi_hw.h:525: error: array type has incomplete element type
/root/ipwraw-ng/iwlwifi_hw.h:847: error: array type has incomplete element type
In file included from /root/ipwraw-ng/ipwraw.c:48:
/root/ipwraw-ng/ipwraw.h:531: error: field ‘frame’ has incomplete type
/root/ipwraw-ng/ipwraw.h:532: error: ‘IEEE80211_FRAME_LEN’ undeclared here (not
in a function)
/root/ipwraw-ng/ipwraw.c: In function ‘frame_get_hdrlen’:
/root/ipwraw-ng/ipwraw.c:52: error: ‘IEEE80211_3ADDR_LEN’ undeclared (first use
in this function)
/root/ipwraw-ng/ipwraw.c:52: error: (Each undeclared identifier is reported only
once
/root/ipwraw-ng/ipwraw.c:52: error: for each function it appears in.)
/root/ipwraw-ng/ipwraw.c:53: error: implicit declaration of function ‘WLAN_FC_GE
T_STYPE’
/root/ipwraw-ng/ipwraw.c:55: error: implicit declaration of function ‘WLAN_FC_GE
T_TYPE’
/root/ipwraw-ng/ipwraw.c:56: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use
in this function)
/root/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_FROMDS’ undeclared (first us
e in this function)

and so on ..

So i researched for a long time and it appears that maybe i had to install the headers, so i downloaded them on windows, transfer them with a usb stick and i installed the .deb file, but when i tried again the same error message appeared.

What should I do ?

thanks a lot for your replies!
Tweedi

---

### Post by varunendra on 2013-09-06
Hi, and Welcome to the forums tweedi2 !

The driver for Intel 3945ABG card is already included in the Linux kernel. You don't need to compile or install it from 3rd parties.

However, this card is way too outdated and the driver for it has some old firmware bugs which Intel never bothered to fix. Nevertheless, it works for most people. Aren't you able to connect with it?

Please post the outputs of -
```
lspci -nnk | grep -iA2 net
dmesg | grep iwl
```

---

### Post by Bucky Ball on 2013-09-06
> **varunendra said:**
> 

The driver for Intel 3945ABG card is already included in the Linux kernel. You don't need to compile or install it from 3rd parties.

This.

It is common coming from Windows to expect to install drivers for all your hardware. Most things 'just work' in Ubuntu, though, unless the hardware was released yesterday. Welcome to Ubuntu, the forums and the learning curve. ;)

PS: You may need to undo something you've done to get this up now.

---

