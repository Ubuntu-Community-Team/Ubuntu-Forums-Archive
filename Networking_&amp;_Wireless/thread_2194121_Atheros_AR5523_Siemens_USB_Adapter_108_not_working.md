---
title: "Atheros AR5523: Siemens USB Adapter 108 not working (Ubuntu 13.10, Linux 3.11.0)"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by sanderj on 2013-12-16
I have got an old Siemens Gigaset USB Adapter 108 which does not work on Ubuntu 13.10 with Linux 3.11.0. Below is some technical info. If anyone has tips, I look forward to them.

lsusb:
```
Bus 002 Device 027: ID 129b:160c CyberTAN Technology Siemens S30853-S1038-R351 802.11g Wireless Adapter [Atheros AR5523]

```

dmesg:
```
[38405.950660] usb 2-1.1: new high-speed USB device number 27 using ehci-pci
[38406.045236] usb 2-1.1: New USB device found, idVendor=129b, idProduct=160c
[38406.045251] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[38406.045257] usb 2-1.1: Product: AR5523
[38406.045262] usb 2-1.1: Manufacturer: Atheros Communications Inc
[38406.045267] usb 2-1.1: SerialNumber: 1.0
[38408.047674] usb 2-1.1: timeout waiting for command 01 reply
[38408.047687] usb 2-1.1: could not initialize adapter
[38408.047904] usb 2-1.1: RX USB error -2.
[38408.047931] usb 2-1.1: error -1 when submitting rx urb
[38408.048062] ar5523: probe of 2-1.1:1.0 failed with error -110
```

lsmod (note: there is also a built-in wifi module in this laptop)
```
$ lsmod | grep ar5523
ar5523                 42073  0 
mac80211              596969  4 ath9k,p54common,ar5523,p54usb
cfg80211              479757  5 ath,ath9k,mac80211,p54common,ar5523
```

Some links I found:

[http://wireless.kernel.org/en/users/Drivers/ar5523](http://wireless.kernel.org/en/users/Drivers/ar5523) which tells it should work.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1113048](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1113048) which "Expired ... because there has been no activity for 60 days."

EDIT:

... and a hardcore kernel one: [http://www.spinics.net/lists/linux-wireless/msg113604.html](http://www.spinics.net/lists/linux-wireless/msg113604.html)

---

### Post by praseodym on 2013-12-16
The "lsmod" output shows other drivers loaded. Check "lsmod" completely. Did you install the package "linux-firmware-nonfree"?

---

### Post by sanderj on 2013-12-16
> **praseodym said:**
> The "lsmod" output shows other drivers loaded. Check "lsmod" completely. Did you install the package "linux-firmware-nonfree"?

EDIT: To rule out interference with any other Wifi hardware, I connected the Siemens USB dongle to a desktop system (also with Ubuntu 13.10) without any Wifi built-in. Results below.
/EDIT


Without the dongle:

```
sander@MegaTurbo:~$ lsmod | grep cfg
sander@MegaTurbo:~$ 
```

With the dongle:

```
sander@MegaTurbo:~$ lsmod | grep cfg
cfg80211              479757  2 mac80211,ar5523
sander@MegaTurbo:~$ 

sander@MegaTurbo:~$ lsmod | grep ar5523
ar5523                 42073  0 
mac80211              596969  1 ar5523
cfg80211              479757  2 mac80211,ar5523
sander@MegaTurbo:~$
```

and the same (right?) output from dmesg:

```
[  408.424033] usb 2-5: new high-speed USB device number 7 using ehci-pci
[  408.557058] usb 2-5: New USB device found, idVendor=129b, idProduct=160c
[  408.557063] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  408.557067] usb 2-5: Product: AR5523
[  408.557070] usb 2-5: Manufacturer: Atheros Communications Inc
[  408.557074] usb 2-5: SerialNumber: 1.0
[  410.556023] usb 2-5: timeout waiting for command 01 reply
[  410.556029] usb 2-5: could not initialize adapter
[  410.556243] usb 2-5: RX USB error -2.
[  410.556253] usb 2-5: error -1 when submitting rx urb
[  410.556310] ar5523: probe of 2-5:1.0 failed with error -110
```

And, yes, linux-firmware-nonfree is installed.

The info in the thread [http://www.spinics.net/lists/linux-wireless/msg113604.html](http://www.spinics.net/lists/linux-wireless/msg113604.html) from Oct 2013 makes me think there is still a problem in the kernel wireless driver with this device.

Based on [http://www.spinics.net/lists/linux-wireless/msg109680.html](http://www.spinics.net/lists/linux-wireless/msg109680.html) I tried this:

```
root@MegaTurbo:~# modprobe -v ar5523
root@MegaTurbo:~# echo 129b 160c > /sys/bus/usb/drivers/ar5523/new_id
```

but gives the same dmesg:

```
[  944.704027] usb 2-5: timeout waiting for command 01 reply
[  944.704035] usb 2-5: could not initialize adapter
[  944.704238] usb 2-5: RX USB error -2.
[  944.704250] usb 2-5: error -1 when submitting rx urb
[  944.704344] ar5523: probe of 2-5:1.0 failed with error -110
```

---

### Post by praseodym on 2013-12-16
The dongle loads "ath9k" and "p54usb", blacklist them. Update the driver via
```

sudo apt-get install build-essential linux-headers-$(uname -r) linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2013/11/21/backports-20131121.tar.gz
tar -xvf backports-20131121.tar.gz
cd backports-20131121
make defconfig-ar5523
make
sudo make install 
```
Reboot.

---

### Post by sanderj on 2013-12-16
> **praseodym said:**
> The dongle loads "ath9k" and "p54usb", blacklist them. Update the driver via
```

sudo apt-get install build-essential linux-headers-$(uname -r) linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2013/11/21/backports-20131121.tar.gz
tar -xvf backports-20131121.tar.gz
cd backports-20131121
make defconfig-ar5523
make
sudo make install 
```
Reboot.

Tail of the result below. Correct? I will try the hardware tomorrow.

```
  LD [M]  /home/sander/Downloads/AR5523/backports-20131121/net/mac80211/mac80211.ko
  CC      /home/sander/Downloads/AR5523/backports-20131121/net/wireless/cfg80211.mod.o
  LD [M]  /home/sander/Downloads/AR5523/backports-20131121/net/wireless/cfg80211.ko

sander@flappie:~/Downloads/AR5523/backports-20131121$ find . -name ar5523.ko -print
./drivers/net/wireless/ath/ar5523/ar5523.ko

sander@flappie:~/Downloads/AR5523/backports-20131121$ file ./drivers/net/wireless/ath/ar5523/ar5523.ko
./drivers/net/wireless/ath/ar5523/ar5523.ko: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), BuildID[sha1]=0xfd15569f747660c30d33e9453cc7ab7f4c2fe571, not stripped

sander@flappie:~/Downloads/AR5523/backports-20131121$ ll ./drivers/net/wireless/ath/ar5523/ar5523.ko
-rw-rw-r-- 1 sander sander 51616 dec 17 00:07 ./drivers/net/wireless/ath/ar5523/ar5523.ko
sander@flappie:~/Downloads/AR5523/backports-20131121$ 

sander@flappie:~/Downloads/AR5523/backports-20131121$ sudo make install
  Building modules, stage 2.
  MODPOST 5 modules
  INSTALL /home/sander/Downloads/AR5523/backports-20131121/compat/compat.ko
Can't read private key
  INSTALL /home/sander/Downloads/AR5523/backports-20131121/drivers/net/wireless/ath/ar5523/ar5523.ko
Can't read private key
  INSTALL /home/sander/Downloads/AR5523/backports-20131121/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/sander/Downloads/AR5523/backports-20131121/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/sander/Downloads/AR5523/backports-20131121/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.8.0-34-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

sander@flappie:~/Downloads/AR5523/backports-20131121$ 
```

---

### Post by praseodym on 2013-12-17
Looks good until now

---

### Post by sanderj on 2013-12-17
Update:

After your commands, rebooting, and plugging in the usb dongle after a while, I get:

```
[  326.378319] usb 2-5: USB disconnect, device number 5

[  331.560043] usb 2-5: new high-speed USB device number 6 using ehci-pci
[  331.693212] usb 2-5: New USB device found, idVendor=129b, idProduct=160c
[  331.693218] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  331.693222] usb 2-5: Product: AR5523
[  331.693226] usb 2-5: Manufacturer: Atheros Communications Inc
[  331.693229] usb 2-5: SerialNumber: 1.0
[  333.692031] usb 2-5: timeout waiting for command 01 reply
[  333.692040] usb 2-5: could not initialize adapter
[  333.692267] usb 2-5: RX USB error -2.
[  333.692279] usb 2-5: error -1 when submitting rx urb
[  333.692379] ar5523: probe of 2-5:1.0 failed with error -110

```

That looks like the same error as with the standard driver? So: not solved, or is the old driver still in use. FWIW:

```
sander@MegaTurbo:~$ locate ar5523.ko | awk '{ print "ls -al ", $1 }' | /bin/sh
-rw-r--r-- 1 sander sander 438 dec 17 19:16 /home/sander/ar5523/backports-20131121/drivers/net/wireless/ath/ar5523/.ar5523.ko.cmd
-rw-r--r-- 1 sander sander 70753 dec 17 19:16 /home/sander/ar5523/backports-20131121/drivers/net/wireless/ath/ar5523/ar5523.ko
-rw-r--r-- 1 root root 69964 okt  9 18:49 /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ar5523/ar5523.ko
-rw-r--r-- 1 root root 69964 nov 12 18:33 /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/ath/ar5523/ar5523.ko
-rw-r--r-- 1 root root 70753 dec 17 19:18 /lib/modules/3.11.0-14-generic/updates/drivers/net/wireless/ath/ar5523/ar5523.ko
sander@MegaTurbo:~$
```


```
sander@MegaTurbo:~$ dmesg | grep -i backport
[   88.273116] Loading modules backported from Linux version next-20131121-0-gc469e3b
[   88.273120] Backport generated by backports.git backports-20131121-0-g92ad5c2
[   88.310363] RTNL: assertion failed at /home/sander/ar5523/backports-20131121/net/wireless/reg.c (217)
[   88.310493] RTNL: assertion failed at /home/sander/ar5523/backports-20131121/net/wireless/reg.c (1234)
sander@MegaTurbo:~$ 

```


Is that bad? Why is it still pointing to my /home/sander/... ?:confused:

---

### Post by sanderj on 2013-12-17
Wait, there is more ... and it does not look good to me:

Fresh boot, plug in usb dongle after a while:

```
[   98.408056] usb 2-5: new high-speed USB device number 6 using ehci-pci
[   98.541260] usb 2-5: New USB device found, idVendor=129b, idProduct=160c
[   98.541266] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   98.541270] usb 2-5: Product: AR5523
[   98.541274] usb 2-5: Manufacturer: Atheros Communications Inc
[   98.541277] usb 2-5: SerialNumber: 1.0
[   98.620563] Loading modules backported from Linux version next-20131121-0-gc469e3b
[   98.620567] Backport generated by backports.git backports-20131121-0-g92ad5c2
[   98.655781] cfg80211: Calling CRDA to update world regulatory domain
[   98.662513] RTNL: assertion failed at /home/sander/ar5523/backports-20131121/net/wireless/reg.c (217)
[   98.662521] CPU: 1 PID: 2172 Comm: crda Tainted: GF          O 3.11.0-14-generic #21-Ubuntu
[   98.662522] Hardware name: System manufacturer System Product Name/P5B, BIOS 1604    07/13/2007
[   98.662525]  ffff8800a248c840 ffff880097955930 ffffffff816e593a 0000000000000000
[   98.662529]  ffff880097955950 ffffffffa04a9651 ffff8800a248c840 ffff880096f3c524
[   98.662532]  ffff8800979559d0 ffffffffa04aadb8 ffff880097955978 ffff88009bfc5540
[   98.662535] Call Trace:
[   98.662544]  [<ffffffff816e593a>] dump_stack+0x45/0x56
[   98.662564]  [<ffffffffa04a9651>] reset_regdomains+0xd1/0xe0 [cfg80211]
[   98.662574]  [<ffffffffa04aadb8>] set_regdom+0x1a8/0x700 [cfg80211]
[   98.662579]  [<ffffffff8137ccd6>] ? nla_parse+0x96/0xe0
[   98.662590]  [<ffffffffa04bdccb>] nl80211_set_reg+0x13b/0x2b0 [cfg80211]
[   98.662594]  [<ffffffff8161b13c>] genl_family_rcv_msg+0x17c/0x380
[   98.662597]  [<ffffffff8161b340>] ? genl_family_rcv_msg+0x380/0x380
[   98.662600]  [<ffffffff8161b3d1>] genl_rcv_msg+0x91/0xd0
[   98.662603]  [<ffffffff8161a8b9>] netlink_rcv_skb+0xa9/0xc0
[   98.662606]  [<ffffffff8161adb8>] genl_rcv+0x28/0x40
[   98.662608]  [<ffffffff81619f0d>] netlink_unicast+0xdd/0x190
[   98.662612]  [<ffffffff8136d79d>] ? memcpy_fromiovec+0x4d/0x90
[   98.662615]  [<ffffffff8161a2bf>] netlink_sendmsg+0x2ff/0x740
[   98.662618]  [<ffffffff8161703c>] ? netlink_rcv_wake+0x3c/0x50
[   98.662620]  [<ffffffff816182f5>] ? netlink_recvmsg+0x205/0x390
[   98.662624]  [<ffffffff815d7b69>] sock_sendmsg+0x99/0xd0
[   98.662627]  [<ffffffff815d8228>] ? sock_recvmsg+0xa8/0xe0
[   98.662630]  [<ffffffff815d7fa8>] ___sys_sendmsg+0x3b8/0x3d0
[   98.662634]  [<ffffffff816f0b7c>] ? __do_page_fault+0x1dc/0x530
[   98.662637]  [<ffffffff815d6a2f>] ? move_addr_to_user+0xaf/0xd0
[   98.662640]  [<ffffffff815d6b2c>] ? SYSC_getsockname+0xdc/0xf0
[   98.662642]  [<ffffffff815d8da2>] __sys_sendmsg+0x42/0x80
[   98.662645]  [<ffffffff815d8df2>] SyS_sendmsg+0x12/0x20
[   98.662648]  [<ffffffff816f571d>] system_call_fastpath+0x1a/0x1f
[   98.662651] RTNL: assertion failed at /home/sander/ar5523/backports-20131121/net/wireless/reg.c (1234)
[   98.662654] CPU: 1 PID: 2172 Comm: crda Tainted: GF          O 3.11.0-14-generic #21-Ubuntu
[   98.662655] Hardware name: System manufacturer System Product Name/P5B, BIOS 1604    07/13/2007
[   98.662657]  ffff880096f3c524 ffff880097955950 ffffffff816e593a ffff8800a248c840
[   98.662660]  ffff8800979559d0 ffffffffa04ab29d ffff880097955978 ffff88009bfc5540
[   98.662663]  ffff88009bfc5540 0000000000000008 ffff8800a248c840 ffffffffa04e3ec0
[   98.662666] Call Trace:
[   98.662668]  [<ffffffff816e593a>] dump_stack+0x45/0x56
[   98.662678]  [<ffffffffa04ab29d>] set_regdom+0x68d/0x700 [cfg80211]
[   98.662681]  [<ffffffff8137ccd6>] ? nla_parse+0x96/0xe0
[   98.662691]  [<ffffffffa04bdccb>] nl80211_set_reg+0x13b/0x2b0 [cfg80211]
[   98.662694]  [<ffffffff8161b13c>] genl_family_rcv_msg+0x17c/0x380
[   98.662696]  [<ffffffff8161b340>] ? genl_family_rcv_msg+0x380/0x380
[   98.662699]  [<ffffffff8161b3d1>] genl_rcv_msg+0x91/0xd0
[   98.662702]  [<ffffffff8161a8b9>] netlink_rcv_skb+0xa9/0xc0
[   98.662704]  [<ffffffff8161adb8>] genl_rcv+0x28/0x40
[   98.662707]  [<ffffffff81619f0d>] netlink_unicast+0xdd/0x190
[   98.662709]  [<ffffffff8136d79d>] ? memcpy_fromiovec+0x4d/0x90
[   98.662712]  [<ffffffff8161a2bf>] netlink_sendmsg+0x2ff/0x740
[   98.662715]  [<ffffffff8161703c>] ? netlink_rcv_wake+0x3c/0x50
[   98.662718]  [<ffffffff816182f5>] ? netlink_recvmsg+0x205/0x390
[   98.662720]  [<ffffffff815d7b69>] sock_sendmsg+0x99/0xd0
[   98.662723]  [<ffffffff815d8228>] ? sock_recvmsg+0xa8/0xe0
[   98.662726]  [<ffffffff815d7fa8>] ___sys_sendmsg+0x3b8/0x3d0
[   98.662729]  [<ffffffff816f0b7c>] ? __do_page_fault+0x1dc/0x530
[   98.662732]  [<ffffffff815d6a2f>] ? move_addr_to_user+0xaf/0xd0
[   98.662734]  [<ffffffff815d6b2c>] ? SYSC_getsockname+0xdc/0xf0
[   98.662737]  [<ffffffff815d8da2>] __sys_sendmsg+0x42/0x80
[   98.662740]  [<ffffffff815d8df2>] SyS_sendmsg+0x12/0x20
[   98.662742]  [<ffffffff816f571d>] system_call_fastpath+0x1a/0x1f
[   98.662744] cfg80211: World regulatory domain updated:
[   98.662746] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   98.662748] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   98.662750] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   98.662752] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   98.662754] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   98.662756] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  100.716027] usb 2-5: timeout waiting for command 01 reply
[  100.716034] usb 2-5: could not initialize adapter
[  100.716409] usb 2-5: RX USB error -2.
[  100.716422] usb 2-5: error -1 when submitting rx urb
[  100.716496] ar5523: probe of 2-5:1.0 failed with error -110
[  100.717020] usbcore: registered new interface driver ar5523
```

---

### Post by sanderj on 2013-12-17
FWIW:

I downloaded and livebooted Ubuntu tahir daily cd, and that gives the same error message:


```
[  313.420054] usb 1-1.2: new high-speed USB device number 4 using ehci-pci
[  313.513752] usb 1-1.2: New USB device found, idVendor=129b, idProduct=160c
[  313.513760] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  313.513766] usb 1-1.2: Product: AR5523
[  313.513771] usb 1-1.2: Manufacturer: Atheros Communications Inc
[  313.513775] usb 1-1.2: SerialNumber: 1.0
[  315.533358] usb 1-1.2: timeout waiting for command 01 reply
[  315.533366] usb 1-1.2: could not initialize adapter
[  315.533703] usb 1-1.2: RX USB error -2.
[  315.533717] usb 1-1.2: error -1 when submitting rx urb
[  315.533799] ar5523: probe of 1-1.2:1.0 failed with error -110
[  315.533849] usbcore: registered new interface driver ar5523
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.12.0-7-generic #15-Ubuntu SMP Sun Dec 8 23:39:27 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ 

```

I see the kernel's dated Dec 8. 

All the above: FWIW ...

---

### Post by sanderj on 2013-12-17
Oh, more bad news:

My first compile & install was on my laptop. After a reboot, that laptop's built-in wifi is not working anymore. I already did

```
sander@flappie:~/Downloads/AR5523/backports-20131121$ sudo make uninstall
  uninstall /lib/modules/3.8.0-34-generic/updates//home/sander/Downloads/AR5523/backports-20131121/drivers/net/wireless/ath/ar5523/ar5523.ko
  uninstall /lib/modules/3.8.0-34-generic/updates//home/sander/Downloads/AR5523/backports-20131121/drivers/net/wireless/ath/ath.ko
  uninstall /lib/modules/3.8.0-34-generic/updates//home/sander/Downloads/AR5523/backports-20131121/compat/compat.ko
  uninstall /lib/modules/3.8.0-34-generic/updates//home/sander/Downloads/AR5523/backports-20131121/net/mac80211/mac80211.ko
  uninstall /lib/modules/3.8.0-34-generic/updates//home/sander/Downloads/AR5523/backports-20131121/net/wireless/cfg80211.ko
```
Note:

... but the dmesg is still garbage:

```
[    2.304113] Loading modules backported from Linux version next-20131121-0-gc469e3b
[    2.304117] Backport generated by backports.git backports-20131121-0-g92ad5c2
[    2.312786] type=1400 audit(1387308336.147:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=616 comm="apparmor_parser"
[    2.313204] type=1400 audit(1387308336.147:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=616 comm="apparmor_parser"
[    2.313487] type=1400 audit(1387308336.147:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=616 comm="apparmor_parser"
[    2.335699] cfg80211: Calling CRDA to update world regulatory domain
[    2.354957] samsung_laptop: detected SABI interface: SwSmi@
[    2.354962] samsung_laptop: Backlight controlled by ACPI video driver
[    2.416764] ath9k_hw: disagrees about version of symbol ath_hw_setbssidmask
[    2.416771] ath9k_hw: Unknown symbol ath_hw_setbssidmask (err -22)
[    2.416778] ath9k_hw: disagrees about version of symbol ath_hw_cycle_counters_update
[    2.416780] ath9k_hw: Unknown symbol ath_hw_cycle_counters_update (err -22)
[    2.416788] ath9k_hw: disagrees about version of symbol ath_hw_get_listen_time
[    2.416789] ath9k_hw: Unknown symbol ath_hw_get_listen_time (err -22)
[    2.416796] ath9k_hw: disagrees about version of symbol ath_printk
[    2.416798] ath9k_hw: Unknown symbol ath_printk (err -22)
[    2.432329] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[    2.438501] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2
[    2.441048] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2
[    2.444242] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.458102] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[    2.474634] fbcon: inteldrmfb (fb0) is primary device
[    2.485701] Linux video capture interface: v2.00
[    2.490236] RTNL: assertion failed at /home/sander/Downloads/AR5523/backports-20131121/net/wireless/reg.c (217)
[    2.490239] Pid: 785, comm: crda Tainted: GF          O 3.8.0-34-generic #49-Ubuntu
[    2.490240] Call Trace:
[    2.490266]  [<ffffffffa028c722>] reset_regdomains+0xd2/0xe0 [cfg80211]
[    2.490278]  [<ffffffffa028df4d>] set_regdom+0x1ad/0x6f0 [cfg80211]
[    2.490284]  [<ffffffff81365d60>] ? nla_parse+0x90/0xe0
[    2.490296]  [<ffffffffa02a4dfc>] nl80211_set_reg+0x1dc/0x2a0 [cfg80211]
[    2.490301]  [<ffffffff815f4a20>] genl_rcv_msg+0x250/0x2d0
[    2.490303]  [<ffffffff815f47d0>] ? genl_rcv+0x30/0x30
[    2.490306]  [<ffffffff815f43e9>] netlink_rcv_skb+0xa9/0xc0
[    2.490308]  [<ffffffff815f47c1>] genl_rcv+0x21/0x30
[    2.490310]  [<ffffffff815f3d21>] netlink_unicast+0x1a1/0x220
[    2.490312]  [<ffffffff815f4091>] netlink_sendmsg+0x2f1/0x3b0
[    2.490316]  [<ffffffff815b1e10>] sock_sendmsg+0xb0/0xe0
[    2.490321]  [<ffffffff8134cb3e>] ? radix_tree_lookup_slot+0xe/0x10
[    2.490325]  [<ffffffff8112fb0e>] ? find_get_page+0x1e/0xa0
[    2.490328]  [<ffffffff815b389c>] ___sys_sendmsg+0x3ac/0x3c0
[    2.490332]  [<ffffffff81159379>] ? handle_mm_fault+0x299/0x670
[    2.490337]  [<ffffffff816d152c>] ? __do_page_fault+0x27c/0x500
[    2.490339]  [<ffffffff815b24c4>] ? move_addr_to_user+0xc4/0xe0
[    2.490341]  [<ffffffff815b511c>] ? sys_getsockname+0xdc/0xf0
[    2.490343]  [<ffffffff815b5839>] __sys_sendmsg+0x49/0x90
[    2.490345]  [<ffffffff815b5892>] sys_sendmsg+0x12/0x20
[    2.490348]  [<ffffffff816d5ddd>] system_call_fastpath+0x1a/0x1f
[    2.490351] RTNL: assertion failed at /home/sander/Downloads/AR5523/backports-20131121/net/wireless/reg.c (1234)
[    2.490353] Pid: 785, comm: crda Tainted: GF          O 3.8.0-34-generic #49-Ubuntu
[    2.490354] Call Trace:
[    2.490365]  [<ffffffffa028e427>] set_regdom+0x687/0x6f0 [cfg80211]
[    2.490368]  [<ffffffff81365d60>] ? nla_parse+0x90/0xe0
[    2.490379]  [<ffffffffa02a4dfc>] nl80211_set_reg+0x1dc/0x2a0 [cfg80211]
[    2.490382]  [<ffffffff815f4a20>] genl_rcv_msg+0x250/0x2d0
[    2.490384]  [<ffffffff815f47d0>] ? genl_rcv+0x30/0x30
[    2.490386]  [<ffffffff815f43e9>] netlink_rcv_skb+0xa9/0xc0
[    2.490389]  [<ffffffff815f47c1>] genl_rcv+0x21/0x30
[    2.490390]  [<ffffffff815f3d21>] netlink_unicast+0x1a1/0x220
[    2.490392]  [<ffffffff815f4091>] netlink_sendmsg+0x2f1/0x3b0
[    2.490395]  [<ffffffff815b1e10>] sock_sendmsg+0xb0/0xe0
[    2.490398]  [<ffffffff8134cb3e>] ? radix_tree_lookup_slot+0xe/0x10
[    2.490400]  [<ffffffff8112fb0e>] ? find_get_page+0x1e/0xa0
[    2.490402]  [<ffffffff815b389c>] ___sys_sendmsg+0x3ac/0x3c0
[    2.490405]  [<ffffffff81159379>] ? handle_mm_fault+0x299/0x670
[    2.490407]  [<ffffffff816d152c>] ? __do_page_fault+0x27c/0x500
[    2.490409]  [<ffffffff815b24c4>] ? move_addr_to_user+0xc4/0xe0
[    2.490411]  [<ffffffff815b511c>] ? sys_getsockname+0xdc/0xf0
[    2.490413]  [<ffffffff815b5839>] __sys_sendmsg+0x49/0x90
[    2.490415]  [<ffffffff815b5892>] sys_sendmsg+0x12/0x20
[    2.490416]  [<ffffffff816d5ddd>] system_call_fastpath+0x1a/0x1f
[    2.490418] cfg80211: World regulatory domain updated:
[    2.490419] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    2.490420] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.490421] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.490423] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.490424] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.490425] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```


Is this easy to solve, or should I re-install? :-(

---

### Post by varunendra on 2013-12-17
Didn't follow the previous posts very closely but did notice that the backported package praseodym suggested was a 'Development Release', and not the latest one.

And..
```
[    2.416764] ath9k_hw: [COLOR="#FF0000"]disagrees about version of symbol[/COLOR] ath_hw_setbssidmask
```
..with my extremely limited understanding about the log messages you've pasted so far, I can say this for sure that the above quoted kind of messages are indication that the kernel version is not happy with the version of the driver(s).

As such, I would recommend to try the latest 'Stable' version of the backported drivers, which you can download from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/) , and the installation method would be same as post #4 of praseodym.

---

### Post by sanderj on 2013-12-18
> **varunendra said:**
> 

As such, I would recommend to try the latest 'Stable' version of the backported drivers, which you can download from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/) , and the installation method would be same as post #4 of praseodym.

Thanks. It didn't work, but I did a dist upgrade from 13.04 to 13.10, and the built-in wifi is working again and I have my main laptop working again. Pfew!

Now back to the 13.10 desktop ... any chance on getting the AR5523 working? If not, that's OK, but it would still be nice.

---

### Post by varunendra on 2013-12-20
Let's take a look at a detailed report generated by Wild Man's "wireless_script", download link and instructions for which you can find in the "Wireless Script" link in my signature.

Preferably run it immediately after a fresh boot, and plugging in the USB adapter after Ubuntu is completely loaded and ready to work.

---

