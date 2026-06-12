---
title: "trying to make edimax dongle work"
date: 2019-03-20
forum: Networking &amp; Wireless
---

### Post by ProDigit on 2019-03-20
i purchased an edimax ew-7611ulb dongle, which is wifi and bluetooth in one.

i downloaded their driver package from here:
[https://www.edimax.com/edimax/download/download/data/edimax/us/download/product/wireless_adapters/wireless_adapters_n150/ew-7611ulb/](https://www.edimax.com/edimax/download/download/data/edimax/us/download/product/wireless_adapters/wireless_adapters_n150/ew-7611ulb/)

i tried the make config without success.
even under sudo su, it appears to do something, but gives loads of errors..

```
$sudo make install -s
Copy RTL8723BU fw/config to /lib/firmware
rmmod: ERROR: Module btusb is not currently loaded
mv: cannot stat '/lib/modules/4.18.0-16-generic/kernel/drivers/bluetooth/btusb.ko': No such file or directory
rmmod: ERROR: Module rtk_btusb is not currently loaded
Makefile:970: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
/home/hb/Downloads/EW-7611ULB_Linux_Bluetooth_Driver_1.0.0.9/bluetooth_usb_driver/rtk_coex.c: In function ‘rtk_check_setup_timer’:
/home/hb/Downloads/EW-7611ULB_Linux_Bluetooth_Driver_1.0.0.9/bluetooth_usb_driver/rtk_coex.c:544:3: error: implicit declaration of function ‘setup_timer’; did you mean ‘sk_stop_timer’? [-Werror=implicit-function-declaration]
   setup_timer(&(btrtl_coex.a2dp_count_timer),
   ^~~~~~~~~~~
   sk_stop_timer
/home/hb/Downloads/EW-7611ULB_Linux_Bluetooth_Driver_1.0.0.9/bluetooth_usb_driver/rtk_coex.c: In function ‘rtk_btcoex_open’:
/home/hb/Downloads/EW-7611ULB_Linux_Bluetooth_Driver_1.0.0.9/bluetooth_usb_driver/rtk_coex.c:2544:2: error: implicit declaration of function ‘init_timer’; did you mean ‘init_timers’? [-Werror=implicit-function-declaration]
  init_timer(&btrtl_coex.polling_timer);
  ^~~~~~~~~~
  init_timers
cc1: some warnings being treated as errors
make[3]: *** [scripts/Makefile.build:327: /home/hb/Downloads/EW-7611ULB_Linux_Bluetooth_Driver_1.0.0.9/bluetooth_usb_driver/rtk_coex.o] Error 1
make[2]: *** [Makefile:1534: _module_/home/hb/Downloads/EW-7611ULB_Linux_Bluetooth_Driver_1.0.0.9/bluetooth_usb_driver] Error 2
make[1]: *** [Makefile:10: all] Error 2
make: *** [Makefile:12: install] Error 2
root@hb-pc:/home/hb/Downloads/EW-7611ULB_Linux_Bluetooth_Driver_1.0.0.9# h
```

---

### Post by jeremy31 on 2019-03-20
Try updated source code @ [https://github.com/lwfinger/rtl8723bu](https://github.com/lwfinger/rtl8723bu)

---

### Post by ProDigit on 2019-04-08
thanks, will try!

---

