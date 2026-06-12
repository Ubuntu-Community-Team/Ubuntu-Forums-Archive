---
title: "Can't create virtual monitoring interface"
date: 2017-08-13
forum: Networking &amp; Wireless
---

### Post by zubrowa on 2017-08-13
Hi,

I have installed Ubuntu 16.04 TLS in my Oracle virtual box.

Now I am trying to put my USB WLAN adapter into monitoring mode which however does not work:
```

sudo iwconfig wlx24050fac7ffe mode monitor 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlx24050fac7ffe ; Invalid argument.

```

Also with airmon-ng it does not work:
```

sudo airmon-ng start wlx24050fac7ffe


Interface    Chipset        Driver

```

I don't know why this is not working. The WNIC seems to be installed propoerly:
```

sudo iwconfig
lo        no wireless extensions.

enp0s3    no wireless extensions.

wlx24050fac7ffe  unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It is also recognized by the system:
```

lsusb | grep Real
Bus 001 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
```

Also it is recognized when the WLAN adapter is plugged in:
```

[10761.545983] usb 1-1: new high-speed USB device number 6 using ehci-pci
[10761.964597] usb 1-1: New USB device found, idVendor=0bda, idProduct=8172
[10761.964599] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10761.964600] usb 1-1: Product: RTL8191S WLAN Adapter 
[10761.964603] usb 1-1: Manufacturer: Manufacturer Realtek 
[10761.964603] usb 1-1: SerialNumber: 00e04c000001
[10761.967077] r8712u: register rtl8712_netdev_ops to netdev_ops
[10761.967080] usb 1-1: r8712u: USB_SPEED_HIGH with 4 endpoints
[10761.971350] usb 1-1: r8712u: Boot from EFUSE: Autoload OK
[10768.177582] usb 1-1: r8712u: CustomerID = 0x000a
[10768.177584] usb 1-1: r8712u: MAC Address from efuse = 24:05:0f:ac:7f:fe
[10768.177586] usb 1-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[10769.256838] r8712u 1-1:1.0 wlx24050fac7ffe: renamed from wlan0

```

Do you have any ideas why I can't put the adapter with airmon-ng in virtual monitoring mode?

Thank you.

Chris

---

### Post by ajgreeny on 2017-08-13
Closed.

The forum does not allow any threads which are about cracking of networks.
See the forum code of conduct, section 17 at [https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

---

