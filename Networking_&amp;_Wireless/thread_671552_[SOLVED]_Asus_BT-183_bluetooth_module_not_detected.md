---
title: "[SOLVED] Asus BT-183 bluetooth module not detected"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by con on 2008-01-18
Hi there

I've an Asus U3S laptop with an integrated bluetooth module, called BT-183 on the back of the laptop.

I'm running kubuntu gutsy and kbluetooth doesn't detect the device.

Running hcitool dev comes up with no devices as well.

Running dmesg shows the following;

[   21.444000] apm: BIOS not found.
[   22.700000] Bluetooth: Core ver 2.11
[   22.700000] NET: Registered protocol family 31
[   22.700000] Bluetooth: HCI device and connection manager initialized
[   22.700000] Bluetooth: HCI socket layer initialized
[   22.720000] Bluetooth: L2CAP ver 2.8
[   22.720000] Bluetooth: L2CAP socket layer initialized
[   22.780000] Bluetooth: RFCOMM socket layer initialized
[   22.780000] Bluetooth: RFCOMM TTY layer initialized
[   22.780000] Bluetooth: RFCOMM ver 1.8
[   24.264000] [drm] Initialized drm 1.1.0 20060810
[   24.264000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ
 16
[   24.264000] [drm] Initialized i915 1.6.0 20060119 on minor 0

Any nudge in the right direction would be appreciated.

---

### Post by con on 2008-01-20
Bump!

---

### Post by con on 2008-02-03
Well the problem was very simple really. Under Vista Asus has a utility which turns on and off the bluetooth and wireless and the last time I had used Vista I had the wireless turned on and the bluetooth turned off. I guess the utility turns off the bluetooth in the Bios which is why it couldn't be detected in linux.

Now that that works, everything on the U3S besides the GPS works out of the box without having to install any drivers or get anything from outside the standard Gutsy repositories, very impressive.

---

### Post by oberengu on 2008-02-03
I think I could have the same problem.
How have you solved it?

---

### Post by con on 2008-02-03
Ya, the bluetooth worked fine in Linux once it was turned on under Vista.

---

