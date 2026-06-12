---
title: "NDISWrapper Installation fails"
date: 2021-08-29
forum: Networking &amp; Wireless
---

### Post by spider-3b on 2021-08-29
I'm trying to install NDISWrapper to install my Bluetooth drivers but I keep getting errors during MAKE:

```
omar_mustafa@omar-mustafa-HP-Laptop-15-da1xxx:~/Downloads/ndiswrapper-1.63$ sudo make
[sudo] password for omar_mustafa: 
make -C utils
make[1]: Entering directory '/home/omar_mustafa/Downloads/ndiswrapper-1.63/utils'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/omar_mustafa/Downloads/ndiswrapper-1.63/utils'
make -C driver
make[1]: Entering directory '/home/omar_mustafa/Downloads/ndiswrapper-1.63/driver'
make -C /usr/src/linux-headers-5.13.9-051309-generic M=/home/omar_mustafa/Downloads/ndiswrapper-1.63/driver
make[2]: Entering directory '/usr/src/linux-headers-5.13.9-051309-generic'
  CC [M]  /home/omar_mustafa/Downloads/ndiswrapper-1.63/driver/loader.o
/home/omar_mustafa/Downloads/ndiswrapper-1.63/driver/loader.c: In function &#8216;load_sys_files&#8217;:
/home/omar_mustafa/Downloads/ndiswrapper-1.63/driver/loader.c:157:4: error: too many arguments to function &#8216;__vmalloc&#8217;
  157 |    __vmalloc(load_driver->sys_files[i].size,
      |    ^~~~~~~~~
In file included from ./include/asm-generic/io.h:911,
                 from ./arch/x86/include/asm/io.h:375,
                 from ./include/linux/scatterlist.h:9,
                 from ./include/linux/dma-mapping.h:10,
                 from ./include/linux/skbuff.h:31,
                 from ./include/net/net_namespace.h:38,
                 from ./include/linux/netdevice.h:37,
                 from /home/omar_mustafa/Downloads/ndiswrapper-1.63/driver/ntoskernel.h:25,
                 from /home/omar_mustafa/Downloads/ndiswrapper-1.63/driver/ndis.h:19,
                 from /home/omar_mustafa/Downloads/ndiswrapper-1.63/driver/loader.c:16:
./include/linux/vmalloc.h:132:14: note: declared here
  132 | extern void *__vmalloc(unsigned long size, gfp_t gfp_mask);
      |              ^~~~~~~~~
make[3]: *** [scripts/Makefile.build:273: /home/omar_mustafa/Downloads/ndiswrapper-1.63/driver/loader.o] Error 1
make[2]: *** [Makefile:1859: /home/omar_mustafa/Downloads/ndiswrapper-1.63/driver] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-5.13.9-051309-generic'
make[1]: *** [Makefile:183: modules] Error 2
make[1]: Leaving directory '/home/omar_mustafa/Downloads/ndiswrapper-1.63/driver'
make: *** [Makefile:23: driver] Error 2
```

---

### Post by monkeybrain20122 on 2021-08-29
Maybe you need to downgrade your kernel. Which Ubuntu is this? What is the kernel version?

[https://www.reddit.com/r/pop_os/comments/jwn24q/wifi_not_working_cant_install_driver/](https://www.reddit.com/r/pop_os/comments/jwn24q/wifi_not_working_cant_install_driver/)
[https://github.com/openzfs/zfs/issues/10862](https://github.com/openzfs/zfs/issues/10862)

ndiswrapper is kind of obsolete, are you sure there is no Linux solution for your bluetooth, maybe you can ask a question about that in a new thread.

PS: you don't need 'sudo' in make. it is only when you install into the system file system (make install) that you need sudo. Abuse of sudo is widespread and it should be avoided. The reason you have sudo is precisely because under most circumstances you shouldn't use it therefore the extra step.

---

### Post by jeremy31 on 2021-08-29
Moved to Networking and wireless 
NDISwrapper will not work for Bluetooth 
Please post results from terminal  for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by chili555 on 2021-08-29
> ndiswrapper is kind of obsoletendiswrapper is VERY obsolete. I haven't seen it work successfully in many years.

---

### Post by spider-3b on 2021-08-31
My kernel is 5.13.9-Generic

---

### Post by spider-3b on 2021-08-31
> **monkeybrain20122 said:**
> Maybe you need to downgrade your kernel. Which Ubuntu is this? What is the kernel version?

[https://www.reddit.com/r/pop_os/comments/jwn24q/wifi_not_working_cant_install_driver/](https://www.reddit.com/r/pop_os/comments/jwn24q/wifi_not_working_cant_install_driver/)
[https://github.com/openzfs/zfs/issues/10862](https://github.com/openzfs/zfs/issues/10862)

ndiswrapper is kind of obsolete, are you sure there is no Linux solution for your bluetooth, maybe you can ask a question about that in a new thread.

PS: you don't need 'sudo' in make. it is only when you install into the system file system (make install) that you need sudo. Abuse of sudo is widespread and it should be avoided. The reason you have sudo is precisely because under most circumstances you shouldn't use it therefore the extra step.

My kernel version is 5.13.9-Generic and I have seen patches up to 5.10 online but none for 5.13

---

### Post by spider-3b on 2021-08-31
> **jeremy31 said:**
> Moved to Networking and wireless 
NDISwrapper will not work for Bluetooth 
Please post results from terminal  for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

sorry for being late but:
```
omar_mustafa@omar-mustafa-HP-Laptop-15-da1xxx:~$ lsusb; dmesg | egrep -i 'blue|firm'Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 05c8:0238 Cheng Uei Precision Industry Co., Ltd (Foxlink) HP Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dmesg: read kernel buffer failed: Operation not permitted



```

it's supposed to be the buggy RTL8822BE

---

### Post by jeremy31 on 2021-09-01
It doesn't find a Bluetooth adapter 
Post results for ```
sudo dmesg | egrep -i 'blue|firm'
```

---

### Post by spider-3b on 2021-09-02
> **jeremy31 said:**
> It doesn't find a Bluetooth adapter 
Post results for ```
sudo dmesg | egrep -i 'blue|firm'
```

hi
```
omar_mustafa@omar-mustafa-HP-Laptop-15-da1xxx:~$ sudo dmesg | egrep -i 'blue|firm'[sudo] password for omar_mustafa: 
[    0.141825] Spectre V2 : Enabling Restricted Speculation for firmware calls
[   73.270521] rtw_8822be 0000:03:00.0: Firmware version 27.2.0, H2C version 13
[  152.875947] Bluetooth: Core ver 2.22
[  152.875986] Bluetooth: HCI device and connection manager initialized
[  152.875990] Bluetooth: HCI socket layer initialized
[  152.875992] Bluetooth: L2CAP socket layer initialized
[  152.875995] Bluetooth: SCO socket layer initialized
[  152.876242] audit: type=1400 audit(1630559882.481:377): apparmor="DENIED" operation="capable" profile="snap.bluetooth-autostart.autostart-bluetooth" pid=9040 comm="hciconfig" capability=12  capname="net_admin"
[  205.862540] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  205.862542] Bluetooth: BNEP filters: protocol multicast
[  205.862545] Bluetooth: BNEP socket layer initialized
[ 1171.046444] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 2504.130923] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 3849.987148] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4070.978107] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4252.000803] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4305.984411] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4316.000346] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4333.984217] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4378.047919] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4421.983635] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4425.983602] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4472.031316] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4514.015043] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4519.999018] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4531.998934] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4553.982821] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4584.990594] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4619.038385] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4621.058343] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4743.997642] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4806.013301] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4818.045217] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4820.061199] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4825.981174] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4831.997136] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4888.988807] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4895.164771] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4901.052738] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4910.972684] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4963.004391] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 4979.004302] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5036.988010] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5073.979747] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5077.979773] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5087.963721] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5122.011485] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5123.995511] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5143.003402] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5170.971226] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5188.987159] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5201.019089] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5237.178911] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5252.986817] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 5336.058374] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 8297.952880] rtw_8822be 0000:03:00.0: firmware failed to leave lps state
[ 8318.016816] rtw_8822be 0000:03:00.0: firmware failed to leave lps state



```

---

### Post by praseodym on 2021-09-04
[https://ubuntuforums.org/showthread.php?t=2383787&p=13739449#post13739449](https://ubuntuforums.org/showthread.php?t=2383787&p=13739449#post13739449)

Try this BT approach. You may need the other one as well  and blacklist this one

---

