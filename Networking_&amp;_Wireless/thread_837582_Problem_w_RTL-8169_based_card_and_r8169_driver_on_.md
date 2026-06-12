---
title: "Problem w/ RTL-8169 based card and r8169 driver on Hardy"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by mbobak on 2008-06-22
Hi,

I've had no luck using my RTL-8169 based NIC:
```
lspci|grep -i net
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

working with my up-to-date Hardy installation:
```
uname -a
Linux jupiter 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
```

So, I tried downloading and compiling the latest driver from RealTek, here:
```
http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true
```

And, when attempting to compile, I am getting the following error:
```
make clean modules
make -C src/ clean
make[1]: Entering directory `/home/mjb/Desktop/rtl8169/r8169-6.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/mjb/Desktop/rtl8169/r8169-6.006.00/src'
make -C src/ modules
make[1]: Entering directory `/home/mjb/Desktop/rtl8169/r8169-6.006.00/src'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/mjb/Desktop/rtl8169/r8169-6.006.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/mjb/Desktop/rtl8169/r8169-6.006.00/src/r8169_n.o
/home/mjb/Desktop/rtl8169/r8169-6.006.00/src/r8169_n.c: In function ‘rtl8169_init_one’:
/home/mjb/Desktop/rtl8169/r8169-6.006.00/src/r8169_n.c:2432: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[3]: *** [/home/mjb/Desktop/rtl8169/r8169-6.006.00/src/r8169_n.o] Error 1
make[2]: *** [_module_/home/mjb/Desktop/rtl8169/r8169-6.006.00/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mjb/Desktop/rtl8169/r8169-6.006.00/src'
make: *** [modules] Error 2

```

Does anyone have any idea how to resolve this problem??

Thanks,

-Mark

---

### Post by mbobak on 2008-06-22
Ok, nevermind.....

I did some more digging, and I discovered that since kernel 2.6.24, SET_MODULE_OWNER is no longer required.  So, I simply commented that line out of the code, and the module built cleanly.

However, I still can't seem to 'UP' the interface:
```
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe800
``` 

And now:
```

sudo ifconfig eth0 up
SIOCSIFFLAGS: Invalid argument

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe800
``` 

So, it would seem that I can set IP address, net mask, etc, but I can't actually UP the interface.  I always get the invalid argument error when trying to UP the interface.....

Any thoughts or ideas, anyone?

-Mark

---

### Post by wdaniels on 2008-06-22
You could try the patched r8168 driver ([see LP 141343 here]("http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/141343/comments/21")) instead.

---

### Post by wdaniels on 2008-06-22
> **wdaniels said:**
> You could try the patched r8168 driver ([see LP 141343 here]("http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/141343/comments/21")) instead.

Forget that actually, I just saw the last comment in that thread:

> Just installed 2.6.24-19 and rebooted, r8169 running fine.

So I guess you should try that first...

---

### Post by skumarisation on 2009-12-20
Hi Daniel
I am also facing the same problem with my RT8169 LAN card. How to install 2.6.24-19 
rgds
skumar

---

