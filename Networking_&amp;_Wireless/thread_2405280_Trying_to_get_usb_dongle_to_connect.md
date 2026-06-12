---
title: "Trying to get usb dongle to connect"
date: 2018-11-03
forum: Networking &amp; Wireless
---

### Post by mystmaiden on 2018-11-03
Hi all. I'm running Trusty LTS and have a Targus bluetooth dongle which according to some research I did on the ubuntu help pages reportedly works 'very well'. So far I'm not getting it to connect though. It searches and does find the other bluetooth devices nearby but gives me a 'failed to connect' return. dmesg nets ```
00 mBm)
[10869.290864] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10869.290869] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10870.314240] wlan0: authenticate with 00:a0:bc:55:8c:95
[10870.337494] wlan0: send auth to 00:a0:bc:55:8c:95 (try 1/3)
[10870.341709] wlan0: authenticated
[10870.345241] wlan0: associate with 00:a0:bc:55:8c:95 (try 1/3)
[10870.349002] wlan0: RX AssocResp from 00:a0:bc:55:8c:95 (capab=0x411 status=0 aid=1)
[10870.349075] wlan0: associated
[15981.817204] usb 3-4: new full-speed USB device number 68 using ohci-pci
[15981.992246] usb 3-4: New USB device found, idVendor=0a5c, idProduct=21e8
[15981.992262] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[15981.992272] usb 3-4: Product: BCM20702A0
[15981.992281] usb 3-4: Manufacturer: Broadcom Corp
[15981.992289] usb 3-4: SerialNumber: 00190E18C454
[15981.994946] usb 3-4: Direct firmware load failed with error -2
[15981.994958] usb 3-4: Falling back to user helper
[15981.998180] Bluetooth: can't load firmware, may not work correctly
[16371.621638] input: B0:B4:48:87:8F:4F as /devices/virtual/input/input19
[16402.636029] input: B0:B4:48:87:8F:4F as /devices/virtual/input/input20

```

I tried running lsub with the dongle plugged in but I got 'command not found'  I thought lsub would give me all the computer specs. Seems I'm woefully behind the times. Does anyone have suggestions as to what might work? For the present I am music-less. My stereo receiver and wired computer speakers managed to bite the tent at the same time!

Edit - 
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 003 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I'm wondering if this might be posted in the wrong forum. Anyone have suggestions for me please? 

Thank you !

mystmaiden

---

### Post by mystmaiden on 2018-11-05
Giving this a bump. Am I in the wrong forum?

---

### Post by slickymaster on 2018-11-05
*Thread moved to **Networking & Wireless**.*

---

### Post by jeremy31 on 2018-11-05
I would do
```
wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-0a5c-21e8.hcd
sudo cp BCM20702A1-0a5c-21e8.hcd /lib/firmware/brcm/BCM.hcd
```
Shut down and boot it up
The firmware name depends on kernel version, but the dmesg output didn't specify the file name

---

