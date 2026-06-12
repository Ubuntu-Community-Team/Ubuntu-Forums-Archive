---
title: "Wireless 5g USB dongle won't install"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by oliviabw on 2018-02-17
Hello.  New here.  I checked around quite a bit and could not find the specific solution to my problem.  I am attempting to install the driver for my Wi-Fi Nano 11ac adapter.  I run the install.sh file through the terminal and get an error message:
```
cc1: some warnings being treated as errorsscripts/Makefile.build:308: recipe for target '/home/olivia/Documents/Adapter/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o' failed
make[2]: *** [/home/olivia/Documents/Adapter/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 1
Makefile:1550: recipe for target '_module_/home/olivia/Documents/Adapter/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51' failed
make[1]: *** [_module_/home/olivia/Documents/Adapter/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-32-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```

Not sure what the problem is here.  I'm also not sure I know how to properly post terminal messages on here.  Any advice is helpful.. Thanks

-Olivia

---

### Post by jeremy31 on 2018-02-17
Can you post the results from terminal for ```
lsusb
```
We can likely find source code that will work for you

---

### Post by oliviabw on 2018-02-17
```
  Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 016: ID 0cf3:e005 Atheros Communications, Inc. 
Bus 001 Device 004: ID 04f3:24dd Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0bda:5769 Realtek Semiconductor Corp. 
Bus 001 Device 019: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

---

### Post by jeremy31 on 2018-02-17
Try the following and reboot
```
sudo apt-get install dkms git build-essential
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add ./rtl8812au
sudo dkms install -m 8812au -v 4.2.2
```

---

### Post by oliviabw on 2018-02-17
Should I then run install.sh again or is this installing the driver in and of itself?

---

### Post by oliviabw on 2018-02-17
getting the same output for ```
lsusb
``` and same error for the install file.

---

### Post by jeremy31 on 2018-02-17
Just reboot and see if the wifi works, if not see the wireless script link in my signature

---

### Post by oliviabw on 2018-02-17
I have an internal wifi-card as well that does not read 5g signal.  Hence the dongle.  Do I need to do anything to switch between these?

---

### Post by oliviabw on 2018-02-17
It definitely is not reading the 5g signal still.  Not sure what to do to switch to usb wifi, not even sure if the driver is installed

---

### Post by jeremy31 on 2018-02-17
Can you post results from the wireless script link in my signature?  That should help figure this out

---

### Post by oliviabw on 2018-02-17
[http://paste.ubuntu.com/p/Tb3F4dT6RX/](http://paste.ubuntu.com/p/Tb3F4dT6RX/)

---

### Post by oliviabw on 2018-02-17
Here is the network output for lspci -v:
```
 01:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)	Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d1100000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at d1180000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

I attempted to blacklist ath9k, thinking that would force the network to use the other adapter, but it didn't seem to do anything at all.  
```
 rfkill block 0
```
did stop the network adapter, but I simply did not have wifi at all after doing so.

---

### Post by oliviabw on 2018-02-17
[ http://paste.ubuntu.com/p/Tb3F4dT6RX/]("http://paste.ubuntu.com/p/Tb3F4dT6RX/")


***sorry duplicate post

---

### Post by jeremy31 on 2018-02-17
Is Secure Boot disabled in UEFI/BIOS settings?

---

### Post by oliviabw on 2018-02-17
I will check

---

### Post by oliviabw on 2018-02-17
Secure Boot is currently enabled

---

### Post by jeremy31 on 2018-02-17
Disable it and the driver for the USB dongle will be allowed

---

### Post by oliviabw on 2018-02-17
Looks like that accomplished the task.  Thank you so much, Jeremy.

---

