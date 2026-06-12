---
title: "Realtek 802.11n install not happening for lubuntu 64-bit os"
date: 2022-11-13
forum: Networking &amp; Wireless
---

### Post by elururajesh on 2022-11-13
Realtek 802.11n install not happening for lubuntu 22.04 64 bit os, error is "make command not recognized", so I tried by changing from make with qmake in install.sh file, then it is saying g++ not suitable to build.

---

### Post by VMC on 2022-11-13
Have looked at this driver:
[https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)

---

### Post by chili555 on 2022-11-13
>  "make command not recognized"Please do:

```
sudo apt update
sudo apt install -y build-essential

```
Then try again.

---

### Post by elururajesh on 2022-11-13
Internet is not connecting to execute given sudo commands
Any alternate please

---

### Post by elururajesh on 2022-11-13
i installed successfully rtl8812au driver, after that how to configure to activate wifi please

---

### Post by chili555 on 2022-11-13
Please show us the result of the terminal command:```
 lsusb
```An 8-digit identifier will appear, something like 2357:010e or something similar.

Next, run:

```
modinfo rtl8812au | grep 010E
```Or whatever usb.id you found if not 010e. Let's see if the driver you installed is actually correct for your device.

---

### Post by elururajesh on 2022-11-13
lsusb output shows  0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
modinfo rtl8812au | grep 010E
modinfo: ERROR: Module rtl8812au not found.

---

### Post by chili555 on 2022-11-13
> [COLOR="#FF0000"]0bda:8179[/COLOR] Realtek Semiconductor Corp. RTL8188EUSThe correct driver for your device is r8188eu which is, I believe, already present in Ubuntu 22.04. Let's check:

```
modinfo r8188eu | grep 8179
lsmod | grep 8188
iwconfig
```

---

### Post by elururajesh on 2022-11-13
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.19.0-23-generic/build M=/media/rajeshbabu/New Volume/wifi drivers for 802.11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519  modules
make[1]: Entering directory '/usr/src/linux-headers-5.19.0-23-generic'
make[1]: *** No rule to make target 'Volume/wifi'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-5.19.0-23-generic'
make: *** [Makefile:1318: modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
As I have software for linux, executed install.sh gives above error

---

### Post by elururajesh on 2022-11-13
modinfo r8188eu | grep 8179
alias:          usb:v07B8p8179d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8179d*dc*dsc*dp*ic*isc*ip*in*
root@rajeshbabu-tobefilledbyoem:/media/rajeshbabu/New Volume/wifi drivers for 802.11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519# lsmod | grep 8188
r8188eu               438272  0
libarc4                16384  1 r8188eu
root@rajeshbabu-tobefilledbyoem:/media/rajeshbabu/New Volume/wifi drivers for 802.11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519# iwconfig
lo        no wireless extensions.

enp2s0    no wireless extensions.

wlx488ad201d94a  unassociated  ESSID:""  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enx023b62751e03  no wireless extensions.

---

### Post by chili555 on 2022-11-13
> As I have software for linux, executed install.sh gives above errorPlease stop. You already have a possibly working driver and a wireless interface. Installing some other random driver, especially a moldy antique from 2014, will not help.

When you click the Network Manager icon, do you see networks?

Does it scan?```
nmcli device wifi list
```Are there any clues in the log?```
sudo dmesg | grep -e 8188 -e wlx
```

---

### Post by chili555 on 2022-11-13
> /media/rajeshbabu/New Volume/wifi drivers for 802.11NHere is a little hint for all of you driver dawgs out there. These install scripts do not like spaces in the names of the file. I would rename these directories to:

```
/media/rajeshbabu/NewVolume/wifi_drivers_for_802.11N
```

And then try again.

Nonetheless, the driver being compiled above will probably not work as it's likely too old for kernel version 5.19.

---

### Post by elururajesh on 2022-11-14
Out put after removing spaces in the driver path:
Seems to be lubuntu build using gcc, but must use cc to build, is there any chance to trigger by cc instead of gcc. Thanks

Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.19.0-23-generic/build M=/tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519  modules
make[1]: Entering directory '/usr/src/linux-headers-5.19.0-23-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.2.0-3ubuntu1) 12.2.0
  You are using:           gcc (Ubuntu 12.2.0-3ubuntu1) 12.2.0
  CC [M]  /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/core/rtw_cmd.o
In file included from /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/include/osdep_service.h:41,
                 from /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/include/drv_types.h:32,
                 from /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/core/rtw_cmd.c:22:

---

### Post by chili555 on 2022-11-14
> **elururajesh said:**
> Out put after removing spaces in the driver path:
Seems to be lubuntu build using gcc, but must use cc to build, is there any chance to trigger by cc instead of gcc. Thanks

Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.19.0-23-generic/build M=/tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519  modules
make[1]: Entering directory '/usr/src/linux-headers-5.19.0-23-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.2.0-3ubuntu1) 12.2.0
  You are using:           gcc (Ubuntu 12.2.0-3ubuntu1) 12.2.0
  CC [M]  /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/core/rtw_cmd.o
In file included from /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/include/osdep_service.h:41,
                 from /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/include/drv_types.h:32,
                 from /tmp/wifi_drivers_for_802_11N/LINUX/RTL81888192EUS_linux_v4.3.0.4_11485.20140519/driver/rtl8188EUS_linux_v4.3.0.4_11485.20140519/core/rtw_cmd.c:22:As I said:

```
Nonetheless, the driver being compiled above will probably not work as it's likely too old for kernel version 5.19.
```
When you click the Network Manager icon, do you see networks?

Does it scan?
```
nmcli device wifi list
```
Are there any clues in the log?
```
sudo dmesg | grep -e 8188 -e wlx
```

---

### Post by elururajesh on 2022-11-14
rajeshbabu@rajeshbabu-tobefilledbyoem:~$** nmcli device wifi list**
IN-USE  BSSID              SSID         MODE   CHAN  RATE       SIGNAL  BARS  SECURITY  
        3E:2E:D6:B4:15:9D  VRB          Infra  1     44 Mbit/s  0       ____  WPA2      
        44:95:3B:1A:90:45  KALPANA2.4G  Infra  5     0 Mbit/s   0       ____  WPA1 WPA2 
        34:0A:33:F2:3A:42  Kommana      Infra  13    44 Mbit/s  0       ____  WPA2      
rajeshbabu@rajeshbabu-tobefilledbyoem:~$ **sudo dmesg|grep -e 8188 -e wlx**
[sudo] password for rajeshbabu: 
[    5.107919] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    5.175716] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[    5.232751] usbcore: registered new interface driver r8188eu
[    5.247197] r8188eu 2-1.2:1.0 wlx488ad201d94a: renamed from wlan0
[    6.640895] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1

---

### Post by elururajesh on 2022-11-14
VRB is the HotSpot name in the mobile

---

### Post by elururajesh on 2022-11-14
wifi configuration from Network Connections

---

### Post by elururajesh on 2022-11-14
Now connected wifi from my mobile in lubuntu os. Thank you very much for your help :o

---

### Post by elururajesh on 2022-11-14
you may close the solved thread

---

