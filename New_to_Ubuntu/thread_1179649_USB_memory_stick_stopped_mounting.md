---
title: "USB memory stick stopped mounting"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Curvature_Tensor on 2009-06-05
[B]PROBLEM
[/B]Neither of my USB drives will mount on one of my computers.
[B]
BACKGROUND
[/B]the problem started when trying to fix my ethernet connection after entering
sudo ifdown eth0
sudo ifup eth0

after plugging in either stick I see
dustin@Hooke:~$ dmesg | grep -i usb
[ number] usb 1-2: new high speed USB device using ehci_hcd and address 10
[ number] usb 1-2: configuration #1 chosen from 1 choice
[ number] scsi 10: SCSI emulation for USB Mass Storage devices
[ number] usb-storage: device found at 10  //note "10" increments by 1 with each insertion
[ number] usb-storage: waiting for device to settle before scanning
[ number] usb-storage: device scan complete

after removing either stick I see
[ number] usb 1-2: USB disconnect, adderess 10

---

### Post by lynnevan on 2009-06-05
What do you get if you run lsusb?

Does it show up if you run "sudo fdisk -l"?

Can you mount it manually - like "sudo mount /dev/sdb /media/usbstick" (sudo mkdir 'usbstick' in /media first and sdb is yr usb stick)?

---

### Post by Curvature_Tensor on 2009-06-06
I restarted several times (~5) with USB sticks in drives, now they auto-mount correctly.

---

