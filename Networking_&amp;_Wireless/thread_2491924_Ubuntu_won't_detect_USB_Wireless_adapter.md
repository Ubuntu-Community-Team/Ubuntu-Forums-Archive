---
title: "Ubuntu won't detect USB Wireless adapter"
date: 2023-10-25
forum: Networking &amp; Wireless
---

### Post by daniell59 on 2023-10-25
Belkin N150 Wireless Adapter
This adapter is detected in lubuntu on another machine.
The adapter is not detected in Ubuntu but. is detected on the same machine in Windows 10.

---

### Post by jeremy31 on 2023-10-25
Any results from terminal in Ubuntu for ```
lsusb
``` when it is plugged in?

---

### Post by daniell59 on 2023-10-25
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 005 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jeremy31 on 2023-10-25
Any results from terminal for ```
rfkill list; sudo dmesg| grep r8712u
```

---

### Post by daniell59 on 2023-10-26
daniel@daniel-P5Q-PRO:~$ rfkill list; sudo dmesg| grep r8712u
[sudo] password for daniel: 
[17945.354309] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[17945.360773] r8712u: register rtl8712_netdev_ops to netdev_ops
[17945.360778] usb 7-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[17945.361324] usb 7-2: r8712u: Boot from EFUSE: Autoload OK
[17945.782389] usb 7-2: r8712u: CustomerID = 0x0000
[17945.782396] usb 7-2: r8712u: MAC Address from efuse = b4:75:0e:23:34:21
[17945.782400] usb 7-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[17945.783711] usbcore: registered new interface driver r8712u
[17945.814950] r8712u 7-2:1.0 wlxb4750e233421: renamed from wlan0
[53505.246584] r8712u: register rtl8712_netdev_ops to netdev_ops
[53505.246589] usb 7-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[53505.247630] usb 7-2: r8712u: Boot from EFUSE: Autoload OK
[53505.629721] usb 7-2: r8712u: CustomerID = 0x0000
[53505.629729] usb 7-2: r8712u: MAC Address from efuse = b4:75:0e:23:34:21
[53505.629733] usb 7-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[53505.720969] r8712u 7-2:1.0 wlxb4750e233421: renamed from wlan0

---

### Post by jeremy31 on 2023-10-26
Moved to Networking
See the wireless script link in my signature and post results

---

### Post by daniell59 on 2023-10-26
Now that I have the wireless script, what do I look for?

---

### Post by chili555 on 2023-10-26
> **daniell59 said:**
> Now that I have the wireless script, what do I look for?
Paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by daniell59 on 2023-10-27
> **chili555 said:**
> Paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Later in the day I will paste the information.

I tried an experiment. I ran the Ubuntu from a flash drive. The wireless adapter was immediately detected. What conclusion can I draw from this?

As always, all assistance is appreciated.

---

### Post by daniell59 on 2023-10-27
[https://pastebin.ubuntu.com/p/CG7957h6cY/](https://pastebin.ubuntu.com/p/CG7957h6cY/)

I hope that I did this correctly.

---

