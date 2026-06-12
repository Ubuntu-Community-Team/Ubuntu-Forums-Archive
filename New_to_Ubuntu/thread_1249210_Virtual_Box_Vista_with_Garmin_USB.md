---
title: "Virtual Box Vista with Garmin USB"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by RichardCL on 2009-08-25
Hi there,

I'm looking for some tips on Virtual Box with USB. Specifically, I'm trying to make a Garmin eTrex Vista HCX work under Vista Business on Virtual Box r304 in Ubuntu 9.04.

I've installed using the repositories in Ubuntu as per the website. I'm told that I need a non-free version to run USB support. How do I check that I'm on the right virtual box version?

I've checked that I'm added to vboxusers group and added a further "usbusers" group. I'm a member of both but root is not.

I ran chmod -R 777 /etc/udev/

I added a filter for Name: Garmin  Vendor: 091E  Remote: Any, then plugged in the Garmin device. Now I see a range of USB devices in the vbox window but they are all greyed out. Windows doesn't see any devices but my USB mouse works fine.

What I'm missing now is an idiots guide to setting up USB in Virtual box.

Any ideas?


Richard

---

### Post by RichardCL on 2009-08-25
Output lsub

> Bus 002 Device 024: ID 091e:0003 Garmin International GPSmap (various models)
Bus 002 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 006: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
Bus 002 Device 005: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 002 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 012: ID 046d:0a12 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Output VBoxManage list usbhost (also includes other devices)

> UUID:               4f783c1c-31eb-417b-9c2b-8117d519eca5
VendorId:           0x091e (091E)
ProductId:          0x0003 (0003)
Revision:           0.1 (0001)
Address:            sysfs:/sys/devices/pci0000:00/0000:00:06.1/usb2/2-2/2-2.2//device:/dev/bus/usb/002/024
Current State:      Unavailable


---

### Post by RichardCL on 2009-08-25
So the answer was really, really simple. In fact so simple that I didn't reaise it.

When you've edited the fstab and changed the users etc. You have to reboot the Ubuntu system and not only the VM.

---

