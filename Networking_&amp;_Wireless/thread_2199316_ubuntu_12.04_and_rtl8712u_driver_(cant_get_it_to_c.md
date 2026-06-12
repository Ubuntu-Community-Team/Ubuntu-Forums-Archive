---
title: "ubuntu 12.04 and rtl8712u driver (cant get it to compile)"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by paymonkossari on 2014-01-13
hi

i've been trying to get this driver to work for a while now but i havent been successful...., the driver is rtl8712u or i also suppose 8912su

anyways, the system recognizes my usb and i have internet but it is not the correct driver, and i cant get the one from realtek to compile

ake ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-35-generic/build M=/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-35-generic'
  CC [M]  /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
In file included from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:23:0:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h: In function ‘_init_timer’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h:151:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:23:0:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h: In function ‘thread_enter’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h:393:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
In file included from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ht.h:25:0,
                 from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:67,
                 from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h: In function ‘get_da’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:350:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:350:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:353:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:353:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:356:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:356:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:359:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:359:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h: In function ‘get_sa’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:374:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:374:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:377:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:377:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:380:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:380:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:383:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:383:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h: In function ‘get_hdr_bssid’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:397:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:397:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:400:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:400:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:403:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:403:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:70:0,
                 from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h: At top level:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h:107:25: error: field ‘event_tasklet’ has incomplete type
In file included from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:72:0,
                 from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h:355:24: error: field ‘xmit_tasklet’ has incomplete type
In file included from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0,
                 from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:205:24: error: field ‘recv_tasklet’ has incomplete type
In file included from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0,
                 from /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:435:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:435:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c: In function ‘_init_cmd_priv’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:93:75: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:101:60: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c: In function ‘_init_evt_priv’:
/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:135:59: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
cc1: some warnings being treated as errors
make[2]: *** [/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-35-generic'
make: *** [modules] Error 2


i'm sure the reason is because of the kernel difference in the driver... i m not sure waht to do about it. cant get a 8712u.ko to appear for me to insmod 

this is my lsusb

Bus 001 Device 006: ID 05ac:12a8 Apple, Inc. 
Bus 002 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 003: ID 0cf2:6230 ENE Technology, Inc. 
Bus 003 Device 002: ID 1532:002e Razer USA, Ltd 
Bus 008 Device 002: ID 1532:011a Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


dmesg | grep 871
[    1.687163] i8042: PNP: No PS/2 controller found. Probing ports directly.
[   18.197871] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SMRG 2 (20121018/utaddress-251)
[   18.226073] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   18.226637] r8712u: Staging version
[   18.226651] r8712u: register rtl8712_netdev_ops to netdev_ops
[   18.226653] r8712u: USB_SPEED_HIGH with 4 endpoints
[   18.227131] r8712u: Boot from EFUSE: Autoload OK
[   18.687274] r8712u: CustomerID = 0x0000
[   18.687277] r8712u: MAC Address from efuse = 00:1a:ef:25:2e:d1
[   18.687279] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   18.687355] usbcore: registered new interface driver r8712u
[   24.675334] r8712u: 1 RCR=0x153f00e
[   24.676139] r8712u: 2 RCR=0x553f00e
[   36.090915] r8712u: wpa_set_encryption, crypt.alg = WEP
[ 1128.366958] r8712u: Staging version
[ 1128.366996] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1128.367000] r8712u: USB_SPEED_HIGH with 4 endpoints
[ 1128.367369] r8712u: Boot from EFUSE: Autoload OK
[ 1128.795669] r8712u: CustomerID = 0x0000
[ 1128.795676] r8712u: MAC Address from efuse = 00:1a:ef:25:2e:d1
[ 1128.795680] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1129.527150] r8712u: 1 RCR=0x153f00e
[ 1129.527894] r8712u: 2 RCR=0x553f00e
[ 1140.128316] r8712u: wpa_set_encryption, crypt.alg = WEP
[ 1149.965726] r8712u: wpa_set_encryption, crypt.alg = WEP
[ 1213.407240] r8712u: r8711_wx_set_enc: EncryptionDisabled
[ 1234.405962] r8712u: wpa_set_encryption, crypt.alg = WEP
[ 1554.892419] r8712u: wpa_set_encryption, crypt.alg = WEP

---

### Post by tfrue on 2014-01-13
> [COLOR=#000000]Bus 002 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter[/COLOR]

I think you will need the rtl8191 driver. I will link a download to the driver I believe you need.
[http://bit.ly/19pa11x](http://bit.ly/19pa11x)

I bitly the link, but go to the site, and it should be under the first listed driver for Unix. Try and compile, make, and make install that driver and see how you luck goes. There is probably a read me in the .zip file so read through that.

---

### Post by chili555 on 2014-01-13
> **tfrue said:**
> I think you will need the rtl8191 driver. I will link a download to the driver I believe you need.
[http://bit.ly/19pa11x](http://bit.ly/19pa11x)

I bitly the link, but go to the site, and it should be under the first listed driver for Unix. Try and compile, make, and make install that driver and see how you luck goes. There is probably a read me in the .zip file so read through that.Isn't that *exactly* what he tried and failed to compile???> /home/paypay/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.201204 That old-timer isn't going to compile on a 3.8 kernel. We no longer use wooden wheels on our sleek BMWs.

What is the problem with the built-in r8712u? Do you have a wireless interface?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```

---

### Post by paymonkossari on 2014-01-13
iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"N97G6"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:62:A5:4E:D0   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



paypay@ubuntu:~$ sudo iwlist wlan0 scan
[sudo] password for paypay: 
wlan0     Scan completed :
          Cell 01 - Address: 00:26:62:A5:4E:D0
                    ESSID:"N97G6"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=100/100  
          Cell 02 - Address: 00:26:62:73:13:81
                    ESSID:"O5NH4"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=58/100  
          Cell 03 - Address: 00:16:B6:A6:85:11
                    ESSID:"Wahoowa"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20401000050f20401000050f2020000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=56/100  
          Cell 04 - Address: F8:E4:FB:04:E5:7A
                    ESSID:"4L6H2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 05 - Address: 00:26:62:47:CA:A5
                    ESSID:"GCUS2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 06 - Address: 00:1D:CF:9E:4D:C0
                    ESSID:"Rabb"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Signal level=26/100  
          Cell 07 - Address: 02:1D:CF:9E:4D:C0
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=26/100  

paypay@ubuntu:~$

---

### Post by paymonkossari on 2014-01-13
it definately works, and i have a connection. i just dont have the correct driver, as it has an unkonwn chipset

---

### Post by chili555 on 2014-01-13
Sorry, I don't know anything, nor do I intend to learn, about airmon, airhack, aircrack, etc. I don't believe the forum supports it either.

---

### Post by coffeecat on 2014-01-13
Indeed. From the forum [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules"):

> **Cracking**: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

@OP, I notice you edited your post to remove the reference to airmon, but you did this after chili555 posted.

Thread closed.

---

