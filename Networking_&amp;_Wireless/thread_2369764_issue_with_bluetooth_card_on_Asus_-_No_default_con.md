---
title: "issue with bluetooth card on Asus - No default controller available"
date: 2017-08-26
forum: Networking &amp; Wireless
---

### Post by dmytro.shvets on 2017-08-26
Hi Colleagues,

I have both Win7 and Ubuntu 16.04 on Asus UX... and there is an issue with bluetooth card on Ubuntu. For Win7 it working fine.

I've searched/tried a lot but have no success and and up with outputs below.

=======================================================
dmytro@DS:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 03eb:8a31 Atmel Corp. 
Bus 001 Device 002: ID 064e:9700 Suyin Corp. Asus Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
=======================================================
dmytro@DS:~$ bluetoothctl 
[bluetooth]# power on
No default controller available
=======================================================
dmytro@DS:~$ lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:c160]
	Kernel driver in use: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 03eb:8a31 Atmel Corp. 
Bus 001 Device 002: ID 064e:9700 Suyin Corp. Asus Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   11.958599] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[   12.246215] iwlwifi 0000:02:00.0: loaded firmware version 25.30.14.0 op_mode iwlmvm
[  874.681935] Bluetooth: Core ver 2.21
[  874.681955] Bluetooth: HCI device and connection manager initialized
[  874.681959] Bluetooth: HCI socket layer initialized
[  874.681961] Bluetooth: L2CAP socket layer initialized
[  874.681966] Bluetooth: SCO socket layer initialized
===================================================

The goal is to connent to BT mouse and speaker.

---

### Post by jeremy31 on 2017-08-26
Try a ```
dmesg | grep 8087
```
Resetting BIOS to defaults might help.  It is strange that it works in Windows and it isn't detected at all in Ubuntu and it should have likely been 8087:07dc in the lsusb results

---

### Post by dmytro.shvets on 2017-08-26
i've got the following:

dmytro@DS:~$ dmesg | grep 8087
[    1.380874] usb 1-5: New USB device found, idVendor=064e, idProduct=9700
[    1.380878] usb 1-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2

this error -2 for 
[COLOR=#000000]lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'[/COLOR]
is slightly confuses
[COLOR=#000000][ 11.958599] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2[/COLOR]
[COLOR=#000000][ 12.246215] iwlwifi 0000:02:00.0: loaded firmware version 25.30.14.0 op_mode iwlmvm[/COLOR]

may be something wrong with Intel drivers?

---

### Post by jeremy31 on 2017-08-26
Have you powered off the laptop and cold booted into Ubuntu?  It isn't the iwlwifi module causing any issue as it is just for wifi, btusb and btintel are the bluetooth modules it should use.  Can you disconnect the hard drive and use the Live USB/DVD to boot to?  I have seen a couple posts were users switched completely to Linux(no dual boot Windows) and the device was found and working after and I have no explanation how it is even possible

---

### Post by dmytro.shvets on 2017-08-26
Just have updated bios and physically removed and putted back wireless adapter.
And miracle happened ... bluetooth started working right after Ubuntu starts and automatically connected all my devices ))

Also found description of this bug with my 7260 wireless device:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1209124](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1209124)

where i liked the conclusion:
... [COLOR=#333333][FONT=monospace]thanks to bad design by ASUS, the Bluetooth hardware is poorly integrated on the UX301 models[/FONT][/COLOR]... 

Thank you much Jeremy for your support

---

### Post by jeremy31 on 2017-08-26
Great find!  ASUS must have used some driver as a patch in Windows to make it work until their BIOS update or it was an issue with the connection between the wifi card and motherboard that caused the issue

---

