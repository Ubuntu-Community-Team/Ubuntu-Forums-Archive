---
title: "broadcom drivers not installing :("
date: 2011-01-19
forum: New to Ubuntu
---

### Post by neil_1 on 2011-01-19
im booting ubuntu x32 on a live usb with 3gb persistance
when i go to hardware drivers ,it shows broadcom sta driver (proprietary) and a ati grafics card (proprietary)
 
but when i try to install the broadcom driver i get a installarchives() fail error
i tried
 
```
sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

```
as well as manually going to [SIZE=1]synaptic and [/SIZE][SIZE=2]completely remove bcmwl-kernel-source and dkms[/SIZE]
 
but i get a
```
 
E: bcmwl-kernel-source: subprocess installed post-removal script returned error exit status 1

```
 as soon as it tries to uninstall bcmwl-kernel-source
any ideas ?

---

### Post by wojox on 2011-01-19
Try these commands in your terminal:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```

---

### Post by wep940 on 2011-01-19
Is the broadcom STA driver enabled?  If not, enable it.  Wait to see if it works for your adapter before getting other things.
 
What is the output of:
 
lspci
 
and
 
lsusb

---

### Post by neil_1 on 2011-01-19
> **wojox said:**
> Try these commands in your terminal:
 
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```
got error at 
sudo dpkg --configure -a
```

Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools

```
:(

---

### Post by neil_1 on 2011-01-19
> **wep940 said:**
> Is the broadcom STA driver enabled? If not, enable it. Wait to see if it works for your adapter before getting other things.
 
What is the output of:
 
lspci
 
and
 
lsusb
cant activate it :(
it gives an installarchives () error
lspci
```
 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```
lsusb
```
 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0718:0639 Imation Corp. 
Bus 002 Device 002: ID 064e:c107 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0718:044e Imation Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
:(
*soz for double post internets stupid slow today dunno wai :O *

---

### Post by wojox on 2011-01-19
Here's a similar [BUG]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023") that might be affecting you.

---

### Post by neil_1 on 2011-01-19
so its just a persistance problem right ?

---

