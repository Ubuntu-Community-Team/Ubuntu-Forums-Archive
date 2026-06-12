---
title: "Internet keeps going on and off..."
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by SWGraphics291 on 2014-01-01
I am using Ubuntu 12.04 LTS and my internet keeps going on and off.

I am using wireless, so here are my settings:
```
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Lite-On Communications Inc Device 6617
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d2400000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at d1400000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k
```

Can you please tell me how to fix this problem. Thank you.

---

### Post by SWGraphics291 on 2014-01-01
If you need more information please ask me...

---

### Post by wildmanne39 on 2014-01-01
Please try:
```
sudo ifconfig wlan0 down
sudo modprobe -rv ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
if it works we will need to make it permanent so do not reboot until you have tested in for a little while.
Thanks

---

### Post by SWGraphics291 on 2014-01-02
It works!!! Now how do I make it permanent?

Thank you so much.

---

### Post by SWGraphics291 on 2014-01-02
Also, can you explain what the commands do to fix my problem? (I like finding out new things)

---

### Post by wildmanne39 on 2014-01-02
Please run:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
it changes encryption from hardware to software.

---

