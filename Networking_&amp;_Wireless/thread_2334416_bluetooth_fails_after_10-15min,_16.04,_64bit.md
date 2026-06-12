---
title: "bluetooth fails after 10-15min, 16.04, 64bit"
date: 2016-08-19
forum: Networking &amp; Wireless
---

### Post by oh my on 2016-08-19
Hi,

I'm running 16.04.1 64bit  Kubuntu on a samsung ativ 9 book. The samsung book has an integrated bluetooth device. I've been pairing my bluetooth headphones with this device. This will work fine for 10-15min at which point the bluetooth connection will be severed and Ubuntu will no longer be able to see the bluetooth device. After a reboot everything is back to normal and I can reconnect my headphones to the bluetooth receiver. However, I don't want to reboot every 10min. 

The dmesg output after the bluetooth connection is severed is:
```

[   52.750298] Bluetooth: hci0 SCO packet for unknown connection handle 0
[   52.750303] Bluetooth: hci0 SCO packet for unknown connection handle 0
[   52.760306] Bluetooth: hci0 SCO packet for unknown connection handle 0
[   55.422505] input: 00:08:2A:F0:3D:99 as /devices/virtual/input/input16
[   58.007712] Bluetooth: hci0 SCO packet for unknown connection handle 257
[   58.007718] Bluetooth: hci0 SCO packet for unknown connection handle 257
[   58.007721] Bluetooth: hci0 SCO packet for unknown connection handle 257
[   77.597516] Bluetooth: hci0 SCO packet for unknown connection handle 0
[   77.607475] Bluetooth: hci0 SCO packet for unknown connection handle 0
[  243.868798] ACPI Error: [^^^PEG0.PEGP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[  243.868808] ACPI Error: Method parse/execution failed [\_SB.PCI0.LPCB.H_EC._Q51] (Node ffff88011b0c2690), AE_NOT_FOUND (20150930/psparse-542)
[  706.899895] usb 2-4: USB disconnect, device number 2
[  706.917502] Bluetooth: hci0 setting interface failed (19)
[  707.206702] usb 2-4: new full-speed USB device number 6 using xhci_hcd
[  707.335844] usb 2-4: New USB device found, idVendor=8087, idProduct=07dc
[  707.335849] usb 2-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  709.350761] Bluetooth: hci0 command 0xfc05 tx timeout
[  717.346834] Bluetooth: hci0 reading Intel fw version command failed (-110)
[  717.361975] Bluetooth: hci0: read Intel version: 370710018002030d55
[  717.361982] Bluetooth: hci0: Intel device is already patched. patch num: 55


```

hci0tool dev shows that the device is still detected:
```
my@mytree:~/Documents/$ hcitool dev
Devices:
        hci0    5C:51:4F:22:30:34

```

Is there a way to fix this? Or even just to reenable the bluetooth recevier so that I can pair the headphones with the laptop again?

---

### Post by john-sweeney on 2016-09-30
I have exactly the same problem, my bluetooth headset was working, samsung level, and then no more device detected in bluetoothctl

---

