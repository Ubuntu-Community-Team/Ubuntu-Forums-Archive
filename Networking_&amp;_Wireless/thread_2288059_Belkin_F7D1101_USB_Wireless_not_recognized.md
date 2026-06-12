---
title: "Belkin F7D1101 USB Wireless not recognized"
date: 2015-07-24
forum: Networking &amp; Wireless
---

### Post by bhilmers2 on 2015-07-24
Hello. Last time I used this Wireless USB device was back in Ubuntu 10.10 and [this thread]("http://ubuntuforums.org/showthread.php?t=1522815") worked perfectly. However, I am now running Lubuntu 15.04 and the device is not working. I read that the r8712u driver provides out-of-box support. I have installed linux-firmware & linux-firmware-nonfree, but no luck. I've tried a couple other things, but don't remember what exactly I've done so I've probably broken my system a little. Any help would be greatly appreciated, thanks.

```
$ lsusb
Bus 001 Device 002: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]

$ lsmod
Module                  Size  Used by
r8712u                163840  0
```

Here is what dmesg prints out when I plug it in:
```
[  146.532098] usb 1-2: new full-speed USB device number 2 using uhci_hcd[  146.700094] usb 1-2: New USB device found, idVendor=050d, idProduct=945a
[  146.700108] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  146.700117] usb 1-2: Product: Basic Wireless USB Adapter
[  146.700125] usb 1-2: Manufacturer: Manufacturer Realtek 
[  146.700133] usb 1-2: SerialNumber: 00e04c000001
[  146.860780] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[  146.865325] r8712u: Staging version
[  146.865388] r8712u: register rtl8712_netdev_ops to netdev_ops
[  146.865403] usb 1-2: r8712u: USB_SPEED_LOW with 4 endpoints
[  146.868149] usb 1-2: r8712u: Boot from EFUSE: Autoload OK
[  149.719599] usb 1-2: r8712u: CustomerID = 0x0000
[  149.719616] usb 1-2: r8712u: MAC Address from efuse = 94:44:52:5d:1a:bb
[  149.719625] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  149.723935] usbcore: registered new interface driver r8712u
[  149.785422] r8712u 1-2:1.0 wlan2: renamed from wlan0
```

---

### Post by bhilmers2 on 2015-07-26
This is an update on my problems with a Belkin F7D1101 USB Wireless interface. I am changing the title of this thread since I can now access my wireless network. However, the wireless disconnects almost immediately after connecting.

The issue posted above was never really solved in a meaningful way.I discovered my network was not visible due to a permissions problem I never located, something to do with iwlist and wpa_supplicant. Se [this page]("https://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools") for how I came to this conclusion. Instead, I changed my installation from Lubuntu Minimal to Lubuntu Full. The wireless interface and network become visible immediately. *However*, the wireless goes dead within seconds of connecting.

Hopefully someone will see this issue and lend me a hand.

---

### Post by praseodym on 2015-07-26
Try these module parameters

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```

---

### Post by bhilmers2 on 2015-07-26
Thanks for the reply praseodym, I learned a lot about wireless and kernel modules while researching those commands. Unfortunately, they had no effect. I will add a little more detail as to what I am experiencing. I don't think I am describing the problem correctly.

When I plug the USB interface in I can connect to my wireless network. I can even load web pages for a few seconds, but within 30 seconds or so I can no longer reach my network even though it says I am still connected. The led on the interface remains lit, but blinks irregularly. If I unplug the interface and plug it back in I can connect once again for a few seconds before it stops. Occasionally it will lock up the computer completely and I have to do a hard reset by killing the power.

---

### Post by bhilmers2 on 2015-07-28
I wonder if I should post this as a bug? Here is my kernel.log at the time of crash, just 5 seconds after plugging it in:

```
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.668119] usb 1-2: new full-speed USB device number 6 using uhci_hcd
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.836104] usb 1-2: New USB device found, idVendor=050d, idProduct=945a
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.836118] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.836126] usb 1-2: Product: Basic Wireless USB Adapter
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.836135] usb 1-2: Manufacturer: Manufacturer Realtek 
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.836142] usb 1-2: SerialNumber: 00e04c000001
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.838331] r8712u: Staging version
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.838387] r8712u: register rtl8712_netdev_ops to netdev_ops
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.838401] usb 1-2: r8712u: USB_SPEED_LOW with 4 endpoints
Jul 27 22:34:31 msit450sx4 kernel: [ 2818.844168] usb 1-2: r8712u: Boot from EFUSE: Autoload OK
Jul 27 22:34:34 msit450sx4 kernel: [ 2821.693636] usb 1-2: r8712u: CustomerID = 0x0000
Jul 27 22:34:34 msit450sx4 kernel: [ 2821.693652] usb 1-2: r8712u: MAC Address from efuse = 94:44:52:5d:1a:bb
Jul 27 22:34:34 msit450sx4 kernel: [ 2821.693663] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
Jul 27 22:34:36 msit450sx4 kernel: [ 2823.670314] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
Jul 27 22:34:36 msit450sx4 kernel: [ 2823.674327] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
```

Is there anything unusual here? Is there another place/log I can get information about the crash? The computer is guaranteed to crash while using the wireless, but there doesn't seem to be anything specific that does it.

---

### Post by praseodym on 2015-07-28
Try updating the module rtlwifi

[https://forum.ubuntuusers.de/topic/frage-w-lan-probleme/#post-7252963](https://forum.ubuntuusers.de/topic/frage-w-lan-probleme/#post-7252963)

---

### Post by bhilmers2 on 2015-07-29
No change after updating rtlwifi. At this point I've spent about 20 hours trying to get this to work, and I'm just going to assume that the new Ubuntu kernel has broken this device's functionality. Dozens of threads about this device end in failure, except for the one's that point to the page I linked to in my opening post, which clearly doesn't work for everyone (I even started with a clean install, wow!!!!).

Wish Ubuntu had better wireless support. Seems to have been a problem for many years now. :/

---

