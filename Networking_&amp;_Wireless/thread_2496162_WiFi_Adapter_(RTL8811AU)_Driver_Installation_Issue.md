---
title: "WiFi Adapter (RTL8811AU) Driver Installation Issue on Raspberry Pi 4 (Ubuntu"
date: 2024-03-16
forum: Networking &amp; Wireless
---

### Post by cyberrobotic on 2024-03-16
I have a network adapter with RTL8811AU chip, when I type following command the kernel is

```

uname -r
5.15.0-1048-raspi

```

My device is recognized as 
```

lsusb
Bus 001 Device 005: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC

``` 

I have tried to install following drivers with from github with no success
[https://github.com/morrownr/8821au-20210708.git](https://github.com/morrownr/8821au-20210708.git)
[https://github.com/aircrack-ng/rtl8812au.git](https://github.com/aircrack-ng/rtl8812au.git)

Any suggestion to a RTL8811AU driver that work with my kernel

---

### Post by jeremy31 on 2024-03-16
You may have to edit the Makefile in the source to allow the driver to build for raspi
What result from terminal for ```
dpkg --print-architecture
```

---

### Post by cyberrobotic on 2024-03-16
When I type your command it comes 
```

dpkg --print-architecture
arm64

```

I saw in the Make file 
[https://github.com/aircrack-ng/rtl8812au.git](https://github.com/aircrack-ng/rtl8812au.git)
that it stands 
```

CONFIG_PLATFORM_ARM64_RPI = n

```
Is this stands RPI for rasberry pi and should it be like this
```

CONFIG_PLATFORM_ARM64_RPI = y

```

---

### Post by jeremy31 on 2024-03-16
Try [https://github.com/morrownr/8821cu-20210916](https://github.com/morrownr/8821cu-20210916)

---

### Post by cyberrobotic on 2024-03-16
I have tried with no success

---

### Post by jeremy31 on 2024-03-16
See the wireless script link in my signature and post results

---

### Post by cyberrobotic on 2024-03-16
It is to large to paste here

---

### Post by jeremy31 on 2024-03-16
Do a ```
cat wireless-info.txt|nc termbin.com 9999
```
Paste URL from terminal

---

### Post by cyberrobotic on 2024-03-16
I have done it and this is the url

[https://termbin.com/fn7n](https://termbin.com/fn7n)

---

### Post by jeremy31 on 2024-03-16
Unplug the wifi, open terminal and run ```
sudo dmesg -w
```
Plug in the wifi wait 20 seconds, then paste terminal output here along with result for ```
modprobe -c | grep -i c811
```

The internal may function better after ```
sudo iwconfig wlan0 power off
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by cyberrobotic on 2024-03-16
The output was
```

modprobe -c | grep -i c811
alias usb:v0403pC811d*dc*dsc*dp*ic*isc*ip*in* ftdi_sio

```

---

### Post by jeremy31 on 2024-03-16
So what is happening when you try to compile the modules from the source code on github?

---

### Post by cyberrobotic on 2024-03-16
The driver get installed but can not recognize my wifi usb adapter

---

### Post by jeremy31 on 2024-03-16
Try ```
sudo depmod -a
```
Then reboot

---

### Post by cyberrobotic on 2024-03-16
I will try it tomorrow thnx for help

---

### Post by morrownr on 2024-04-01
> ID 0bda:c811

That ID tells us that the chipset in your adapter is a rtl8821cu, not the rtl8821au.

You said the following driver did not work:

[https://github.com/morrownr/8821au-20210708.git](https://github.com/morrownr/8821au-20210708.git)

The reason it did not work is between you did not read the README:

"Note: Please read the file "supported-device-IDs" for information about how to confirm that this is the correct driver for your adapter."

That statement is right up near the top of the README. Had you read it and followed the instructions, you would have known you were looking at the wrong driver.

The correct driver for your adapter is:

[https://github.com/morrownr/8821cu-20210916](https://github.com/morrownr/8821cu-20210916)

---

