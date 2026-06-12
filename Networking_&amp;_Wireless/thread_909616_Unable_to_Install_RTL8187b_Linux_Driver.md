---
title: "Unable to Install RTL8187b Linux Driver"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Whorehay on 2008-09-03
After being unable to install my RTL8187b USB dongle I contacted Realtek and they provided me with a driver package specifically for Linux. I have read every single readme and installation instructions, but I cannot get it to work. After doing "sudo make" in the Terminal it gives me several error codes:
> sugeorge@george-desktop:~/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187$ sudo ke
[sudo] password for george:
make -C /lib/modules/2.6.24-19-generic/build M=/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o
In file included from /home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:64:
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function 'rtl8180_proc_module_init':
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: 'proc_net' undeclared (first use in this function)
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: (Each undeclared identifier is reported only once
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: for each function it appears in.)
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function 'rtl8180_proc_module_remove':
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:456: error: 'proc_net' undeclared (first use in this function)
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function 'rtl8187_rx_urbsubmit':
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:730: warning: passing argument 6 of 'usb_fill_bulk_urb' from incompatible pointer type
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function 'rtl8180_tx':
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:1648: warning: passing argument 6 of 'usb_fill_bulk_urb' from incompatible pointer type
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function 'rtl8180_init':
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053: error: 'INIT_WORK' undeclared (first use in this function)
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2054:77: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2055:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2056:80: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2057:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function 'rtl8187_usb_probe':
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2938: error: implicit declaration of function 'SET_MODULE_OWNER'
/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2956: error: 'struct net_device' has no member named 'get_wireless_stats'
make[2]: *** [/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/george/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

I decided to ignore these errors and tried to turn the device on (per instructions), but no luck either.
> george@george-desktop:/media/Backup/Xubuntu ****/rtl8187_linux_26.1025.0328.2007$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device

Am I missing something?  I unpacked everything, but I must be doing something wrong.  I can drag my desktop computer and connect it physically to the router, but this is obviously not practical. I'm on Xubuntu 8.04 (Hardy Heron) which I updated just last night.  I can boot to Windows XP to connect wirelessly.

I have attached the driver package Realtek sent me, since I would prefer to use this instead of the modified drivers out there or even ndiswrapper.

Any help would be greatly appreciated.

---

### Post by darck on 2008-10-08
If lsusb gives:
Bus 007 Device 003: ID 0bda:8198 Realtek Semiconductor Corp.

use driver modified by me. All others doesnt work with ID :8198!
Probably module included with kernel 2.6.27 douesnt work with that id too.
[http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html](http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html)

following installation:
./makedrv
sudo nano /etc/rc.local
add to this file: /change/path/to/correct/wlan0up
sudo apt-get install wicd
after restart chenge in wicd settings wireless interface to correct one (usually wlan0 or wlan1, can be checked by iwconfig)

run wicd, press refresh, APs should be detected. Press connect, vuala :)
&#8212;&#8212;&#8212;-
!?!?!!:
-driver compilation ./makedrv requires libraries: linux-headers- (install if gets fatal error)
-this driver probably doesn&#8217;t work with ID other than: 0bda:8198. If have other ID use one of [http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches](http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches)
OR:
use (in /etc/rc.local) wlan0up in following way:
lsusb gives for example: Bus 007 Device 002: ID 0bda:8198 Realtek Semiconductor Corp., so:
wlan0up force_card=0×8189
-I couldn&#8217;t compile this driver with kernel v. 2.6.27

---

