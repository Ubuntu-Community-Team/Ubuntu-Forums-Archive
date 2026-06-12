---
title: "RT5370 Firmware"
date: 2015-11-04
forum: Networking &amp; Wireless
---

### Post by david460 on 2015-11-04
Hello,
I am trying to get a USB RT5370 wifi card to work. The module is loading automatically (RT2800), and the device is listed in ifconfig and iwconfig. However when I try to bring it up I get the error: 

SIOCSIFFLAGS: No such file or directory
dmesg reveals this error:

[ 2121.008615] phy2 -> rt2x00lib_request_firmware: Error - Failed to request Firmware ('rt2870.bin').

so I checked in /lib/firmware and rt2870.bin is present, I even changed the permission to 777 (I know not safe) just to see if it would work.

I even removed the kernel module and reinserted it, but this proved to be fruitless.

At this point, I am at a loss of what todo, and any insight would be appreciated.

---

### Post by chili555 on 2015-11-05
> However when I try to bring it up I get the error: 

SIOCSIFFLAGS: No such file or directoryAnd then:> phy2 -> rt2x00lib_request_firmware: Error - Failed to request Firmware ('rt2870.bin').I'm not sure these are the exact same error. Please show us:```
iwconfig
ifconfig wlan0
```...or whatever your wireless interface is, if not wlan0.

What command are you issuing to bring it up? Please show us the exact command and the full, exact result. Also:```
ls -al /lib/firmware | grep rt2
```

---

### Post by david460 on 2015-11-06
the error is caused by ifconfig the device can not go up.
```
[COLOR=#000000]ifconfig wlan1 up
[/COLOR][COLOR=#000000]SIOCSIFFLAGS: No such file or directory[/COLOR]
```

the error in dmesg occurs directly after I issued the ifconfig wlan1 up command

```

 dmesg |grep rt2
[    0.626679] sw_uart_get_devinfo()1503 - uart2 has no uart_regulator.
[    1.311058] uart2: ttyS2 at MMIO 0x1c28800 (irq = 34) is a SUNXI
[   20.567277] Registered led device: rt2800usb-phy0::radio
[   20.567362] Registered led device: rt2800usb-phy0::assoc
[   20.567443] Registered led device: rt2800usb-phy0::quality
[   20.567563] usbcore: registered new interface driver rt2800usb
[   22.219729] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware ('rt2870.bin').
[   71.031377] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware ('rt2870.bin').
[  197.466972] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware ('rt2870.bin').

```

```

iwconfig
gre0      no wireless extensions.


lo        no wireless extensions.


tunl0     no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
sit0      no wireless extensions.


eth0      no wireless extensions.


ip6tnl0   no wireless extensions.

```




```

ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 00:13:ef:b3:02:8a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


```

-rw-r--r--  1 root root    8192 Nov 24  2014 rt2561.bin
-rw-r--r--  1 root root    8192 Nov 24  2014 rt2561s.bin
-rw-r--r--  1 root root    8192 Nov 24  2014 rt2661.bin
-rw-r--r--  1 root root    8192 Nov 24  2014 rt2860.bin
-rwxrwxrwx  1 root root    8192 Nov 24  2014 rt2870.bin
lrwxrwxrwx  1 root root      10 Nov 24  2014 rt3070.bin -> rt2870.bin
lrwxrwxrwx  1 root root      10 Nov 24  2014 rt3090.bin -> rt2860.bin

```


I have gone through the forum and looked at the help you offered others, and nothing seems to work. Thanks for your help.

---

### Post by chili555 on 2015-11-06
> iwconfig
gre0      no wireless extensions.


lo        no wireless extensions.


[COLOR="#FF0000"]tunl0[/COLOR]     no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
[COLOR="#FF0000"]sit0 [/COLOR]     no wireless extensions.


eth0      no wireless extensions.I'm confused. Is this a virtual machine? ARM? Raspberry Pi? Toaster? Or..?? I'm a little suspicious of a udev problem. Anything interesting here?```
ps aux | grep udev
```

Is there any change if you remove and then reload the driver:```
sudo modprobe -r rt2800usb && sudo modprobe rt2800usb
dmesg | grep rt2
```

---

### Post by david460 on 2015-11-06
Yes, it is an ARM, Orange Pi.

udev is running

```

root       184  1.6  0.1  10496  1468 ?        Ss   00:00   0:00 /lib/systemd/systemd-udevd
root       474  0.0  0.0   3632   676 ttyS0    S+   00:00   0:00 grep --color=auto udev

```


Reloading the module does not help either.


```

[    0.627672] sw_uart_get_devinfo()1503 - uart2 has no uart_regulator.
[    0.850313] uart2: ttyS2 at MMIO 0x1c28800 (irq = 34) is a SUNXI
[   20.187762] Registered led device: rt2800usb-phy0::radio
[   20.187864] Registered led device: rt2800usb-phy0::assoc
[   20.187950] Registered led device: rt2800usb-phy0::quality
[   20.188039] usbcore: registered new interface driver rt2800usb
[   21.252832] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware ('rt2870.bin').
[   55.843265] usbcore: deregistering interface driver rt2800usb
[   56.509229] Registered led device: rt2800usb-phy1::radio
[   56.509548] Registered led device: rt2800usb-phy1::assoc
[   56.509864] Registered led device: rt2800usb-phy1::quality
[   56.510391] usbcore: registered new interface driver rt2800usb
[   56.597808] phy1 -> rt2x00lib_request_firmware: Error - Failed to request Firmware ('rt2870.bin').

```

---

