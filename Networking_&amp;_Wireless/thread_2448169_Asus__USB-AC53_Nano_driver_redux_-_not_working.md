---
title: "Asus  USB-AC53 Nano driver redux - not working"
date: 2020-08-03
forum: Networking &amp; Wireless
---

### Post by szydas on 2020-08-03
I'm (un)lucky owner of WiFi dongle based on RTL8822BU. My system is ```
5.4.0-42-generic
``` lsusb output is 
```
Bus 001 Device 002: ID 0b05:184c ASUSTek Computer, Inc. 802.11ac NIC
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
There is CDROM included in package, even with "linux" folder, but running ready-to-use shell script produces error:

```
/home/szydas/Desktop/RTL88x2BU_WiFi_linux_v5.2.4.3_24934.20171101_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.3_24934.20171101_COEX20171012-5044/include/osdep_service_linux.h:282:8: error: ‘_timer’ {aka ‘struct timer_list’} has no member named ‘data’
  282 |  ptimer->data = (unsigned long)cntx;
      |        ^~
/home/szydas/Desktop/RTL88x2BU_WiFi_linux_v5.2.4.3_24934.20171101_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.3_24934.20171101_COEX20171012-5044/include/osdep_service_linux.h:283:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  283 |  init_timer(ptimer);
      |  ^~~~~~~~~~
      |  _init_timer

```
So i followed steps from that thread [https://ubuntuforums.org/showthread.php?t=2395729&page=2&](https://ubuntuforums.org/showthread.php?t=2395729&page=2&) - unfortunately it produces lot of warnings and ends with an error:```

home/szydas/rtl8822bu/os_dep/osdep_service.c: In function ‘isFileReadable’:
/home/szydas/rtl8822bu/os_dep/osdep_service.c:2022:10: error: implicit declaration of function ‘get_ds’; did you mean ‘get_da’? [-Werror=implicit-function-declaration]
 2022 |   set_fs(get_ds());
      |          ^~~~~~
      |          get_da
/home/szydas/rtl8822bu/os_dep/osdep_service.c:2022:10: error: incompatible type for argument 1 of ‘set_fs’
 2022 |   set_fs(get_ds());
      |          ^~~~~~~~
      |          |
      |          int
In file included from ./include/linux/uaccess.h:11,
                 from ./include/linux/crypto.h:21,
                 from ./include/crypto/hash.h:11,
                 from ./include/linux/uio.h:10,
                 from ./include/linux/socket.h:8,
                 from ./include/linux/compat.h:15,
                 from ./include/linux/ethtool.h:17,
                 from ./include/linux/netdevice.h:37,
                 from /home/szydas/rtl8822bu/include/osdep_service_linux.h:35,
                 from /home/szydas/rtl8822bu/include/osdep_service.h:41,
                 from /home/szydas/rtl8822bu/include/drv_types.h:32,
                 from /home/szydas/rtl8822bu/os_dep/osdep_service.c:24:
./arch/x86/include/asm/uaccess.h:29:40: note: expected ‘mm_segment_t’ {aka ‘struct <anonymous>’} but argument is of type ‘int’
   29 | static inline void set_fs(mm_segment_t fs)
      |                           ~~~~~~~~~~~~~^~
/home/szydas/rtl8822bu/os_dep/osdep_service.c: In function ‘retriveFromFile’:
/home/szydas/rtl8822bu/os_dep/osdep_service.c:2052:11: error: incompatible type for argument 1 of ‘set_fs’
 2052 |    set_fs(get_ds());
      |           ^~~~~~~~
      |           |
      |           int
In file included from ./include/linux/uaccess.h:11,
                 from ./include/linux/crypto.h:21,
                 from ./include/crypto/hash.h:11,
                 from ./include/linux/uio.h:10,
                 from ./include/linux/socket.h:8,
                 from ./include/linux/compat.h:15,
                 from ./include/linux/ethtool.h:17,
                 from ./include/linux/netdevice.h:37,
                 from /home/szydas/rtl8822bu/include/osdep_service_linux.h:35,
                 from /home/szydas/rtl8822bu/include/osdep_service.h:41,
                 from /home/szydas/rtl8822bu/include/drv_types.h:32,
                 from /home/szydas/rtl8822bu/os_dep/osdep_service.c:24:
./arch/x86/include/asm/uaccess.h:29:40: note: expected ‘mm_segment_t’ {aka ‘struct <anonymous>’} but argument is of type ‘int’
   29 | static inline void set_fs(mm_segment_t fs)
      |                           ~~~~~~~~~~~~~^~
/home/szydas/rtl8822bu/os_dep/osdep_service.c: In function ‘storeToFile’:
/home/szydas/rtl8822bu/os_dep/osdep_service.c:2087:11: error: incompatible type for argument 1 of ‘set_fs’
 2087 |    set_fs(get_ds());
      |           ^~~~~~~~
      |           |
      |           int
In file included from ./include/linux/uaccess.h:11,
                 from ./include/linux/crypto.h:21,
                 from ./include/crypto/hash.h:11,
                 from ./include/linux/uio.h:10,
                 from ./include/linux/socket.h:8,
                 from ./include/linux/compat.h:15,
                 from ./include/linux/ethtool.h:17,
                 from ./include/linux/netdevice.h:37,
                 from /home/szydas/rtl8822bu/include/osdep_service_linux.h:35,
                 from /home/szydas/rtl8822bu/include/osdep_service.h:41,
                 from /home/szydas/rtl8822bu/include/drv_types.h:32,
                 from /home/szydas/rtl8822bu/os_dep/osdep_service.c:24:
./arch/x86/include/asm/uaccess.h:29:40: note: expected ‘mm_segment_t’ {aka ‘struct <anonymous>’} but argument is of type ‘int’
   29 | static inline void set_fs(mm_segment_t fs)
      |                           ~~~~~~~~~~~~~^~
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:275: /home/szydas/rtl8822bu/os_dep/osdep_service.o] Error 1
make[1]: *** [Makefile:1731: /home/szydas/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-42-generic'
make: *** [Makefile:1318: modules] Error 2
```
I'm not a programmer and probably too old to learn it. Any help appreciated.

---

### Post by szydas on 2020-08-03
UPDATE:
Following suggestion from friend I replaced get_ds() funktion with KERNEL_DS. And it almost solved problem.... almost
```
home/szydas/rtl8822bu/os_dep/linux/os_intfs.c:1170:22: error: initialization of &#8216;u16 (*)(struct net_device *, struct sk_buff *, struct net_device *)&#8217; {aka &#8216;short unsigned int (*)(struct net_device *, struct sk_buff *, struct net_device *)&#8217;} from incompatible pointer type &#8216;u16 (*)(struct net_device *, struct sk_buff *, void *, u16 (*)(struct net_device *, struct sk_buff *, struct net_device *))&#8217; {aka &#8216;short unsigned int (*)(struct net_device *, struct sk_buff *, void *, short unsigned int (*)(struct net_device *, struct sk_buff *, struct net_device *))&#8217;} [-Werror=incompatible-pointer-types]
 1170 |  .ndo_select_queue = rtw_select_queue,
      |                      ^~~~~~~~~~~~~~~~
/home/szydas/rtl8822bu/os_dep/linux/os_intfs.c:1170:22: note: (near initialization for &#8216;rtw_netdev_ops.ndo_select_queue&#8217;)
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:275: /home/szydas/rtl8822bu/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [Makefile:1731: /home/szydas/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-42-generic'
make: *** [Makefile:1318: modules] Error 2
```

---

### Post by chili555 on 2020-08-03
With a temporary working internet connection by ethernet, tethering or whatever means possible, do:

```
sudo apt update
sudo apt install git dkms
git clone https://github.com/jeremyb31/rtl8822bu.git
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```

Reboot.

---

### Post by szydas on 2020-08-04
I did. It tells, that's everything was succesful. I rebooted. Now:
1. lsusb does nothing, i mean after pressing Enter cursor blinks.... and blinks... until next reboot.
2. lsmod gives 
```
szydas@ubunciak:~$ lsmod |grep 8822
8822bu               1781760  1
cfg80211              704512  1 8822bu
```
3. In Network Setings dongle is not visible. Tried every USB slot available. Several reboots - no change.

---

### Post by chili555 on 2020-08-04
> lsusb does nothing, i mean after pressing Enter cursor blinks.... and blinks... until next reboot.It is not supposed to do anything at all except list (ls) the devices that are attached to your USB (usb) ports. Hence, lsusb. Installing a driver or the correct driver or the wrong driver doesn't change whether the device is or is not inserted.

Let's check the log for clues:

```
dmesg | grep -i -e 8822 -e rtl
```

---

### Post by szydas on 2020-08-04
I think that is most revelant part
```
[   20.563725] 8822bu: loading out-of-tree module taints kernel.
[   20.569129] 8822bu: module verification failed: signature and/or required key missing - tainting kernel
[   20.574186] RTW: rtl8822bu v5.1.0-5_17968.20160601_BTCOEX20160411-1400_beta
[   20.574186] RTW: rtl8822bu BT-Coex version = BTCOEX20160411-1400
[   20.574324] RTW: CHIP TYPE: RTL8822B
[   20.576649] RTW: Chip Version Info: CHIP_8822B_Normal_Chip_UMC_D_CUT_2T2R_RomVer(3)
```

---

### Post by chili555 on 2020-08-04
Looks perfect, actually.

Please remove the device and run:

```
tail -f /var/log/syslog
```

Insert the device and tell us what the terminal reports in full related to the device and driver.

Get ot of 'tail' with Ctrl+c.

---

### Post by szydas on 2020-08-05
Well.... nothing happen. No single log entry about inserting something into USB. I found only one entry about removing it.
```
Aug  5 09:29:01 ubunciak kernel: [  858.665662] usb 1-2: USB disconnect, device number 3
```
But, strangely, inserting pendrive also doesn't trigger any action,.. and it worked even few days ago. Maybe my mobo is dying?

---

### Post by chili555 on 2020-08-05
> **szydas said:**
> Well.... nothing happen. No single log entry about inserting something into USB. I found only one entry about removing it.
```
Aug  5 09:29:01 ubunciak kernel: [  858.665662] usb 1-2: USB disconnect, device number 3
```
But, strangely, inserting pendrive also doesn't trigger any action,.. and it worked even few days ago. Maybe my mobo is dying?Perhaps.

Have you tried all the available USB ports? Maybe it is just one port that is dying.

---

### Post by szydas on 2020-08-05
> **chili555 said:**
> Perhaps.

Have you tried all the available USB ports? Maybe it is just one port that is dying.
Yes. I did. But my keyboard an mouse on USB work without problem... even if I change port :confused:

---

### Post by chili555 on 2020-08-05
Perhaps it is the device itself that is defective. Does it work in other computers? Windows??

---

### Post by szydas on 2020-08-05
I got same idea, but on windows machine it installs and works w/o problem. I ordered replacement mobo, a bit hard to buy new after 15 years ;)

---

### Post by szydas on 2020-08-05
Meanwhile i dug out my old HDD with Windows. All USB ports seems to work and dongle installs. Don't know what to think.

---

### Post by chili555 on 2020-08-05
> **szydas said:**
> Meanwhile i dug out my old HDD with Windows. All USB ports seems to work and dongle installs. Don't know what to think.With your Ubuntu HDD back in, insert the device, boot up and show us:

```
lsusb
dmesg | grep usb
```

As the output may be lengthy, psate the result here and give us the link.

---

### Post by szydas on 2020-08-05
lsusb still doesn't work. Dmesg output attached.

---

### Post by chili555 on 2020-08-05
Let's try a newer version of the driver. Remove the device from the USB port. From the terminal:

```
sudo dkms remove 8822bu/1.1
git clone https://github.com/cilynx/rtl88x2bu.git
cd rtl88x2bu/
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER} 
sudo dkms install -m rtl88x2bu -v ${VER}
```

The 'build' step takes a few minutes; please be patient.

Insert the device and show us:

```
iwconfig
dmesg | grep -e 88x2 -e wlx

```

---

### Post by szydas on 2020-08-07
```
sudo dkms remove 8822bu/1.1
``` didn't work, got to ```
sudo dkms remove 8822bu/1.1 --all
```
reboot... and.... tadam!
```
szydas@ubunciak:~$ iwconfig
enp5s12   no wireless extensions.

lo        no wireless extensions.

wlxd45d64920b18  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
dmesg output:
```
[   21.355841] 88x2bu: loading out-of-tree module taints kernel.
[   21.363196] 88x2bu: module verification failed: signature and/or required key missing - tainting kernel
[   22.427486] usbcore: registered new interface driver rtl88x2bu
[   22.664762] rtl88x2bu 1-4:1.0 wlxd45d64920b18: renamed from wlan0
[  211.504562] IPv6: ADDRCONF(NETDEV_CHANGE): wlxd45d64920b18: link becomes ready

```
now connected to WiFi and moving machine to my workshop :)

---

### Post by mapst on 2020-12-03
Hi, how to solve this problem

---

### Post by wildmanne39 on 2020-12-03
Hi mapst and welcome to the forum, if you have a question please state the issue in your own thread and do not post in someone else's asking for help, it gets confusing for everyone involved.

Thanks

---

