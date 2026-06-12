---
title: "HOWTO: Thomson USB Wifi &quot;Loading firmware file isl3887usb&quot; &quot;Firmware not found.&quot;"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by sanderj on 2013-12-14
A FYI / HOWTO:

I have got an old Thomson SPeedtouch 121g Wireless 802.11g USB adapter. 

lsusb
```
Bus 001 Device 005: ID 06b9:0121 Alcatel Telecom SpeedTouch 121g Wireless Dongle

```

I doesn't work on Ubuntu 13.10 and dmesg says:

```
[15928.808008] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[15928.905698] usb 1-1.3: New USB device found, idVendor=06b9, idProduct=0121
[15928.905710] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[15928.905716] usb 1-1.3: Product: 802.11g Wireless USB Adapter
[15928.905720] usb 1-1.3: Manufacturer: BT
[15928.905725] usb 1-1.3: SerialNumber: 06B9-0121
[15929.108324] usb 1-1.3: reset high-speed USB device number 4 using ehci-pci
[15929.202242] usb 1-1.3: Loading firmware file isl3887usb
[15929.202584] usbcore: registered new interface driver p54usb
[15929.205811] usb 1-1.3: Firmware not found.
[15929.205815] usb 1-1.3: failed to initialize device (-2)
```

I solved this with:

```
cd /lib/firmware/
sudo wget http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.25.0.lm87.arm -O isl3887usb
ll isl3887usb 
```

Replugging the device gave:

```
[16616.035326] usb 1-1.3: new high-speed USB device number 5 using ehci-pci
[16616.132901] usb 1-1.3: New USB device found, idVendor=06b9, idProduct=0121
[16616.132913] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[16616.132919] usb 1-1.3: Product: 802.11g Wireless USB Adapter
[16616.132924] usb 1-1.3: Manufacturer: BT
[16616.132929] usb 1-1.3: SerialNumber: 06B9-0121
[16616.207586] usb 1-1.3: reset high-speed USB device number 5 using ehci-pci
[16616.301328] usb 1-1.3: Loading firmware file isl3887usb
[16616.301813] ieee80211 phy2: p54 detected a LM87 firmware
[16616.301824] p54: rx_mtu reduced from 3240 to 2384
[16616.301834] ieee80211 phy2: FW rev 2.13.25.0 - Softmac protocol 5.9
[16616.301845] ieee80211 phy2: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[16617.298187] ieee80211 phy2: hwaddr 00:12:bf:0a:70:f5, MAC:isl3887 RF:Frisbee
[16617.306730] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[16617.307804] usb 1-1.3: is registered as 'phy2'
```

... and the wifi device worked!

---

### Post by varunendra on 2013-12-15
> **sanderj said:**
> 
```
cd /lib/firmware/
sudo wget http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.25.0.lm87.arm -O isl3887usb
ll isl3887usb 
```

Thanks for the link sanderj, it may be the latest one available.

But, just out of curiosity, did you try installing "linux-firmware-nonfree" package before trying above? Because this firmware file (isl3887usb) is present in the "linux-firmware-nonfree-1.14" package under "/linux-firmware-nonfree-1.14/firmware/prism54_softmac/" directory. You seem to have installed it directly under /lib/firmware directory which is an interesting difference, even if the versions might be same. :)

---

### Post by sanderj on 2013-12-16
Hi varunendra,

"linux-firmware-nonfree"?! Oh, I had tried "linux-firmware", which was already installed. And I had searched for "proprietary" in the Dash, but that didn't work.

linux-firmware-nonfree ... works! Thank you!

(In the old Ubuntu days there was a network card icon popping up telling it had some non-free to install)


```
[ 6635.275511] usb 2-1.5: new high-speed USB device number 6 using ehci-pci
[ 6635.372313] usb 2-1.5: New USB device found, idVendor=06b9, idProduct=0121
[ 6635.372319] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6635.372322] usb 2-1.5: Product: 802.11g Wireless USB Adapter
[ 6635.372324] usb 2-1.5: Manufacturer: BT
[ 6635.372326] usb 2-1.5: SerialNumber: 06B9-0121
[ 6635.447053] usb 2-1.5: reset high-speed USB device number 6 using ehci-pci
[ 6635.540366] usb 2-1.5: Loading firmware file isl3887usb
[ 6635.540571] ieee80211 phy2: p54 detected a LM87 firmware
[ 6635.540574] p54: rx_mtu reduced from 3240 to 2384
[ 6635.540577] ieee80211 phy2: FW rev 2.13.24.0 - Softmac protocol 5.9
[ 6635.540581] ieee80211 phy2: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[ 6636.533656] ieee80211 phy2: hwaddr 00:12:bf:0a:70:f5, MAC:isl3887 RF:Frisbee
[ 6636.541806] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[ 6636.542275] usb 2-1.5: is registered as 'phy2'
[ 6636.573287] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6636.575119] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6636.612573] ieee80211 phy2: radar (freq:2412 MHz)
[ 6636.628926] ieee80211 phy2: radar (freq:2412 MHz)
```

```
$ sudo updatedb 
$ locate isl3887usb
/lib/firmware/isl3887usb
```

---

### Post by varunendra on 2013-12-16
Glad to know it works, because now I won't have to remember yet another link or package name. :P

PS:
I was wrong about the firmware file being in "....prism54_softmac/" directory, it was indeed in the /lib/firmware directory in the deb package. the "....prism54_softmac/" path was in a tar.gz package that I initially opened, without noticing that it was not the .deb package.

---

