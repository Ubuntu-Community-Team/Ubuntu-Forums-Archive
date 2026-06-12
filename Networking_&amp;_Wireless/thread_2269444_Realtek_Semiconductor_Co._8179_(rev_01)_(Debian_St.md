---
title: "Realtek Semiconductor Co. 8179 (rev 01) (Debian Style)"
date: 2015-03-15
forum: Networking &amp; Wireless
---

### Post by Reckful on 2015-03-15
Hello every one,

I am sorry if this question has been asked before but I have searched all over the internet in order to get my wireless to work correctly. Now it's been some time since I have missed around in linux but I am not lazy and have exhasted all my resources at this time, this is why I am posting here. I currently have a toshiba with debian (wheezy 7) with a 

```

Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)

```

which I understand is the 8188ee model, I believe but here is all the commands I have issued.

Verion of debian
```

root@debian:/home/reckful/Downloads/backports-3.11-rc3-1# uname -a
Linux debian 3.2.0-4-686-pae #1 SMP Debian 3.2.65-1+deb7u2 i686 GNU/Linux

```

lspci -vnn | grep -i net -A 8
```

01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at c8500000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable+ Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable- Count=16 Masked-
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0191]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 2000 [size=256]
    Memory at c8400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting

```

Installing headers and buil-essential
```

sudo apt-get install linux-headers-generic build-essential

```
Kernal 
```

root@debian:/home/reckful/Downloads/backports-3.11-rc3-1# uname -r
3.2.0-4-686-pae

```

Error Mesage
```

root@debian:/home/reckful/Downloads/backports-3.11-rc3-1# make defconfig-rtlwifi
make[2]: `conf' is up to date.
#
# configuration written to .config
#
root@debian:/home/reckful/Downloads/backports-3.11-rc3-1# make
make[5]: `conf' is up to date.
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/reckful/Downloads/backports-3.11-rc3-1/compat/main.o
  CC [M]  /home/reckful/Downloads/backports-3.11-rc3-1/compat/compat-3.3.o
In file included from /usr/src/linux-headers-3.2.0-4-common/arch/x86/include/asm/swiotlb.h:4:0,
                 from /usr/src/linux-headers-3.2.0-4-common/arch/x86/include/asm/dma-mapping.h:14,
                 from /home/reckful/Downloads/backports-3.11-rc3-1/backport-include/asm/dma-mapping.h:3,
                 from /usr/src/linux-headers-3.2.0-4-common/include/linux/dma-mapping.h:68,
                 from /home/reckful/Downloads/backports-3.11-rc3-1/backport-include/linux/dma-mapping.h:3,
                 from /usr/src/linux-headers-3.2.0-4-common/include/linux/skbuff.h:32,
                 from /home/reckful/Downloads/backports-3.11-rc3-1/backport-include/linux/skbuff.h:3,
                 from /home/reckful/Downloads/backports-3.11-rc3-1/compat/compat-3.3.c:13:
/home/reckful/Downloads/backports-3.11-rc3-1/backport-include/linux/swiotlb.h:11:29: error: static declaration of ‘swiotlb_nr_tbl’ follows non-static declaration
/usr/src/linux-headers-3.2.0-4-common/include/linux/swiotlb.h:27:22: note: previous declaration of ‘swiotlb_nr_tbl’ was here
make[8]: *** [/home/reckful/Downloads/backports-3.11-rc3-1/compat/compat-3.3.o] Error 1
make[7]: *** [/home/reckful/Downloads/backports-3.11-rc3-1/compat] Error 2
make[6]: *** [_module_/home/reckful/Downloads/backports-3.11-rc3-1] Error 2
make[5]: *** [sub-make] Error 2
make[4]: *** [all] Error 2
make[3]: *** [modules] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [default] Error 2

```

This is the [Link](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281) that I went too as wel as this [one](https://wiki.debian.org/WiFi/HowToUse#Wicd) and could not get either one of them to work fully. Now please do not drill me to hard, as I did mention that I am a little rusty. If any one can help me out in getting this intalled properly, I would be greatful.

---

