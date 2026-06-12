---
title: "How to install Elekele WiFi Adapter 1200Mbps Wireless USB"
date: 2018-01-05
forum: Networking &amp; Wireless
---

### Post by swordf1zh on 2018-01-05
I purchased this adapter recently that was suppossed to work with linux. I am a completely Linux newbie and had spent several hours trying to make it work.

The USB device is identified as 0bda:b812 and I found that this device should be Realtek RTL8822BU Wireless 802.11ac USB NIC.

CD with drivers is worthless as I got errors when trying to execute ```
make
```. Here is the output:

```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.14.0-041400-generic/build M=/home/swordf1zh/Desktop/wifi-adapter-support-files/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333  modules
make[1]: Entering directory '/usr/src/linux-headers-4.14.0-041400-generic'
  CC [M]  /home/swordf1zh/Desktop/wifi-adapter-support-files/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/core/rtw_cmd.o
scripts/Makefile.build:314: recipe for target '/home/swordf1zh/Desktop/wifi-adapter-support-files/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/core/rtw_cmd.o' failed
Makefile:1509: recipe for target '_module_/home/swordf1zh/Desktop/wifi-adapter-support-files/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333' failed
make[1]: Leaving directory '/usr/src/linux-headers-4.14.0-041400-generic'
Makefile:1874: recipe for target 'modules' failed
```

I contacted the seller and he sent me this information, but I think is the same as on the CD:
> Message from 3rd party seller:
[https://share.weiyun.com/9996a987b2232a62e1f567536d20b729](https://share.weiyun.com/9996a987b2232a62e1f567536d20b729)
please click the link, install the driver again, if there is still issue, please feel free to contact us.

I already followed all the steps from [this thread]("https://ubuntuforums.org/showthread.php?t=2378892&page=4") and succesfully executed ```
make
``` and ```
sudo make install
```, but the USB adapter is still not working.

**Here is the wireless-info script result: [http://paste.ubuntu.com/26323538/](http://paste.ubuntu.com/26323538/)**

Thanks for your help.

---

### Post by jeremy31 on 2018-01-05
You can try this, after installing and booting into a 4.4.0 kernel
```
sudo apt-get install git build-essential dkms
git clone https://github.com/jeremyb31/rtl8822bu.git
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1

```
Reboot

---

### Post by liam.gutierrez on 2018-04-30
[FONT=arial]swordf1zh, did you have any success installing? I recommend to disconnect the wifi adapter before installing the driver. Realtek sucks but I got it to work. I used it for RTL8812AU driver and followed this directions [https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)

[/FONT][FONT=courier new][FONT=arial]But I bought a new wifi adapter and made the mistake of buying a Realtek again (OK, I got it free via promotional credit) and have the same problem.[/FONT]
[/FONT][FONT=arial]
[FONT=lucida sans unicode]lsusb[/FONT][/FONT]
[FONT=arial][FONT=lucida sans unicode]Bus 001 Device 003: ID 0bda:b812 Realtek Semiconductor Corp.
[/FONT]
I hope the directions above worked out for you.[/FONT]

---

### Post by jglen4902 on 2018-06-01
> **jeremy31 said:**
> You can try this, after installing and booting into a 4.4.0 kernel
```
sudo apt-get install git build-essential dkms
git clone https://github.com/jeremyb31/rtl8822bu.git
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1

```
Reboot
Thank you jeremy31.  I too bought one of those generic Realtek chipped wifi adapters from Amazon.  Your instructions worked perfectly and the antenna does seem to have brought in a stronger connection.  Kinda awkward just precariously hanging off the front of my PC case, but I may just use a USB extender cord and tape it off on top of the case.  We'll see ...

---

