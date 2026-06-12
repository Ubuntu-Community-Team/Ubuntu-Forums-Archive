---
title: "error -71 while connecting USB cable Nokia e50"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by klocek81 on 2008-10-12
Hi all, I found a problem while connecting USB cable to my PB with Ubuntu (it is not a new one, but pen drive can be mounted and works). I can't find any solution to my problem, there is one threat on this forum [http://ubuntuforums.org/showthread.php?t=576925](http://ubuntuforums.org/showthread.php?t=576925)
My mobile is OK, cable is also fine (I can connect to Windows and Ubuntu on my laptor, and everything is fine). When I connect to the one I mentioned, I choose on phone PS Suite, but there is no icon for connection on the mobile's screen. 
lsusb shows nothing:
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

dmesg:
[ 2331.420511] usb 1-2: new full speed USB device using uhci_hcd and address 2
[ 2331.540421] usb 1-2: device descriptor read/64, error -71
[ 2331.764324] usb 1-2: device descriptor read/64, error -71
[ 2331.980219] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 2332.100163] usb 1-2: device descriptor read/64, error -71
[ 2332.324060] usb 1-2: device descriptor read/64, error -71
[ 2332.539966] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 2332.947785] usb 1-2: device not accepting address 4, error -71
[ 2333.059781] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 2333.467549] usb 1-2: device not accepting address 5, error -71
[ 2352.454902] usb 1-2: new full speed USB device using uhci_hcd and address 6
[ 2352.578832] usb 1-2: device descriptor read/64, error -71
[ 2352.806755] usb 1-2: device descriptor read/64, error -71
[ 2353.022638] usb 1-2: new full speed USB device using uhci_hcd and address 7
[ 2353.142585] usb 1-2: device descriptor read/64, error -71
[ 2353.366476] usb 1-2: device descriptor read/64, error -71
[ 2353.582379] usb 1-2: new full speed USB device using uhci_hcd and address 8
[ 2353.990194] usb 1-2: device not accepting address 8, error -71
[ 2354.102147] usb 1-2: new full speed USB device using uhci_hcd and address 9
[ 2354.509965] usb 1-2: device not accepting address 9, error -71
[ 2403.807509] usb 1-2: new full speed USB device using uhci_hcd and address 10
[ 2403.927451] usb 1-2: device descriptor read/64, error -71
[ 2404.151347] usb 1-2: device descriptor read/64, error -71
[ 2404.367244] usb 1-2: new full speed USB device using uhci_hcd and address 11
[ 2404.487200] usb 1-2: device descriptor read/64, error -71
[ 2404.711093] usb 1-2: device descriptor read/64, error -71
[ 2404.927118] usb 1-2: new full speed USB device using uhci_hcd and address 12
[ 2405.342809] usb 1-2: device not accepting address 12, error -71
[ 2405.456552] usb 1-2: new full speed USB device using uhci_hcd and address 13
[ 2405.870568] usb 1-2: device not accepting address 13, error -71
[ 2721.043007] usb 1-2: new full speed USB device using uhci_hcd and address 14
[ 2721.166946] usb 1-2: device descriptor read/64, error -71
[ 2721.390849] usb 1-2: device descriptor read/64, error -71
[ 2721.606742] usb 1-2: new full speed USB device using uhci_hcd and address 15
[ 2721.726687] usb 1-2: device descriptor read/64, error -71
[ 2721.950592] usb 1-2: device descriptor read/64, error -71
[ 2722.166485] usb 1-2: new full speed USB device using uhci_hcd and address 16
[ 2722.574308] usb 1-2: device not accepting address 16, error -71
[ 2722.686249] usb 1-2: new full speed USB device using uhci_hcd and address 17
[ 2723.094074] usb 1-2: device not accepting address 17, error -71

Please find attached lsusb-v.txt for what lsusb -v returns
Thank you for any help!
klocek

---

### Post by asuastrophysics on 2009-11-10
I have the same problem with Karmic.

No ipod support at all. All it does is charge it. 

can someone please tell me why we had to switch to udev? HAL worked just fine. why do we have to fix things that aren't broken? 

who knows when this will be fixed. i've decided i will never upgrade ubuntu again. all it is, is trouble.

---

