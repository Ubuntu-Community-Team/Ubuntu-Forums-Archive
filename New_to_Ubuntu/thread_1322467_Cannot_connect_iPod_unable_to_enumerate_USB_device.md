---
title: "Cannot connect iPod: unable to enumerate USB device on port 2"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-11
hey everyone,

I've been getting some strange ipod behavior ever since upgrading to karmic. My iPod won't connect to my computer. It just shows a charging icon. 

here is dmesg:
```
[90590.320089] usb 5-1: new full speed USB device using uhci_hcd and address 2
[90590.450086] usb 5-1: device descriptor read/64, error -71
[90590.750083] usb 5-1: device descriptor read/64, error -71
[90590.980087] usb 5-1: new full speed USB device using uhci_hcd and address 3
[90591.110094] usb 5-1: device descriptor read/64, error -71
[90591.350086] usb 5-1: device descriptor read/64, error -71
[90591.580089] usb 5-1: new full speed USB device using uhci_hcd and address 4
[90592.000080] usb 5-1: device not accepting address 4, error -71
[90592.120085] usb 5-1: new full speed USB device using uhci_hcd and address 5
[90592.540088] usb 5-1: device not accepting address 5, error -71
[90592.540120] hub 5-0:1.0: unable to enumerate USB device on port 1
[90598.680085] usb 5-1: new full speed USB device using uhci_hcd and address 6
[90598.870083] usb 5-1: device descriptor read/64, error -71
[90599.120086] usb 5-1: device descriptor read/64, error -71
[90599.290134] hub 5-0:1.0: unable to enumerate USB device on port 1
[90600.950108] usb 5-2: new full speed USB device using uhci_hcd and address 8
[90601.080073] usb 5-2: device descriptor read/64, error -71
[90601.320079] usb 5-2: device descriptor read/64, error -71
[90601.490146] hub 5-0:1.0: unable to enumerate USB device on port 2
[90607.320089] usb 6-2: new full speed USB device using uhci_hcd and address 2
[90607.510079] usb 6-2: device descriptor read/64, error -71
[90607.750084] usb 6-2: device descriptor read/64, error -71
[90607.980085] usb 6-2: new full speed USB device using uhci_hcd and address 3
[90608.110089] usb 6-2: device descriptor read/64, error -71
[90608.350092] usb 6-2: device descriptor read/64, error -71
[90608.580082] usb 6-2: new full speed USB device using uhci_hcd and address 4
[90609.000077] usb 6-2: device not accepting address 4, error -71
[90609.120086] usb 6-2: new full speed USB device using uhci_hcd and address 5
[90609.540094] usb 6-2: device not accepting address 5, error -71
[90609.540126] hub 6-0:1.0: unable to enumerate USB device on port 2
[90740.090094] usb 6-2: new full speed USB device using uhci_hcd and address 6
[90740.220081] usb 6-2: device descriptor read/64, error -71
[90740.460080] usb 6-2: device descriptor read/64, error -71
[90740.690102] usb 6-2: new full speed USB device using uhci_hcd and address 7
[90740.820079] usb 6-2: device descriptor read/64, error -71
[90741.120075] usb 6-2: device descriptor read/64, error -71
[90741.350096] usb 6-2: new full speed USB device using uhci_hcd and address 8
[90741.770081] usb 6-2: device not accepting address 8, error -71
[90741.890098] usb 6-2: new full speed USB device using uhci_hcd and address 9
[90742.310082] usb 6-2: device not accepting address 9, error -71
[90742.310118] hub 6-0:1.0: unable to enumerate USB device on port 2
[90745.370089] usb 6-2: new full speed USB device using uhci_hcd and address 10
[90745.500104] usb 6-2: device descriptor read/64, error -71
[90745.740101] usb 6-2: device descriptor read/64, error -71
[90745.970101] usb 6-2: new full speed USB device using uhci_hcd and address 11
[90746.100063] usb 6-2: device descriptor read/64, error -71
[90746.340105] usb 6-2: device descriptor read/64, error -71
[90746.570073] usb 6-2: new full speed USB device using uhci_hcd and address 12
[90746.990097] usb 6-2: device not accepting address 12, error -71
[90747.110108] usb 6-2: new full speed USB device using uhci_hcd and address 13
[90747.530089] usb 6-2: device not accepting address 13, error -71
[90747.530125] hub 6-0:1.0: unable to enumerate USB device on port 2
[90772.250090] usb 6-2: new full speed USB device using uhci_hcd and address 14
[90772.380086] usb 6-2: device descriptor read/64, error -71
[90772.620084] usb 6-2: device descriptor read/64, error -71
[90772.850088] usb 6-2: new full speed USB device using uhci_hcd and address 15
[90772.980093] usb 6-2: device descriptor read/64, error -71
[90773.220082] usb 6-2: device descriptor read/64, error -71
[90773.450084] usb 6-2: new full speed USB device using uhci_hcd and address 16
[90773.870045] usb 6-2: device not accepting address 16, error -71
[90773.990085] usb 6-2: new full speed USB device using uhci_hcd and address 17
[90774.410072] usb 6-2: device not accepting address 17, error -71
[90774.410108] hub 6-0:1.0: unable to enumerate USB device on port 2
[90867.440094] usb 6-2: new full speed USB device using uhci_hcd and address 18
[90867.630176] usb 6-2: device descriptor read/64, error -71
[90867.870087] usb 6-2: device descriptor read/64, error -71
[90868.100429] usb 6-2: new full speed USB device using uhci_hcd and address 19
[90868.230098] usb 6-2: device descriptor read/64, error -71
[90868.470075] usb 6-2: device descriptor read/64, error -71
[90868.760088] usb 6-2: new full speed USB device using uhci_hcd and address 20
[90869.180083] usb 6-2: device not accepting address 20, error -71
[90869.302907] usb 6-2: new full speed USB device using uhci_hcd and address 21
[90869.720080] usb 6-2: device not accepting address 21, error -71
[90869.720115] hub 6-0:1.0: unable to enumerate USB device on port 2

```

Anyone know what's going on here? I'm thinking this is a problem caused by udev. 

Any help would be appreciated :)

---

### Post by asuastrophysics on 2009-11-11
Bump!

---

### Post by asuastrophysics on 2009-11-11
Solved! 

It was a broken wire in the iPod USB cable. 
How did I know? Unpredictability. Sometimes it would connect, sometimes it would charge and not connect, othertimes it would do neither. 

See link below for schematics on USB cables:

[http://pinouts.ru/SerialPortsCables/usb_cable_pinout.shtml](http://pinouts.ru/SerialPortsCables/usb_cable_pinout.shtml)

---

