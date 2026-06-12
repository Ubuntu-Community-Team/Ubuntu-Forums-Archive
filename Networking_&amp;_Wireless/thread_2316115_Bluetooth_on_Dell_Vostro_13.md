---
title: "Bluetooth on Dell Vostro 13"
date: 2016-03-05
forum: Networking &amp; Wireless
---

### Post by martin193 on 2016-03-05
Hi,
I have Kubuntu 15.10 installed on my notebook Dell Vostro 13 (new instalation) and I have problem with bluetooth. Manager of bluetooth devices is writing me "No bluetooth devices have been found" wifi is working fine but bluetooth don't work and I can't find some driver or manual which can help me.

root@ubuntu:/home/martin# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
09:00.0 Network controller: Intel Corporation WiFi Link 5100
root@ubuntu:/home/martin# lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 10f1:1a1e Importek Laptop Integrated Webcam 1.3M
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@ubuntu:/home/martin# lsusb | grep Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
root@ubuntu:/home/martin# 
                                                                                                                                                 Thanks

---

### Post by jeremy31 on 2016-03-05
```
cat /lib/udev/rules.d/97-hid2hci.rules
```

These Dell devices can be a pain

---

### Post by martin193 on 2016-03-05
Thanks a lot for a answer I done only reorganization of my systems, because Windows 10 isn't for me as well all new versions of Windows, but Windows XP was super. Kubuntu looks fine and works very quickly than Windows. I'm only surprised how fine and complexly. Bluetooth for phones isn't almost necessary. My main system is Crunchbang but sometimes I'm afraid that I'm lost in stream of deb packages but support is very similar one more time Thanks for a answer.
Sorry for my English but English isn't my native language.
                                                                                                                  Martin

---

### Post by jeremy31 on 2016-03-05
I actually want to see what terminal shows after pasting the command in.  Some of the broadcom chips used by dell need hid2hci to switch a device reported by lsusb as a mouse or touchpad to HCI mode for it to work as a bluetooth.

It is common for Dell 365 and some of there other standalone modules to have this issue in Linux

---

### Post by martin193 on 2016-03-06
martin@ubuntu:~$ sudo cat /lib/udev/rules.d/97-hid2hci.rules
[sudo] password for martin: 
# do not edit this file, it will be overwritten on update

ACTION=="remove", GOTO="hid2hci_end"
SUBSYSTEM!="usb*", GOTO="hid2hci_end"

# Variety of Dell Bluetooth devices - match on a mouse device that is
# self powered and where a HID report needs to be sent to switch modes
# Known supported devices: 413c:8154, 413c:8158, 413c:8162
ATTR{bInterfaceClass}=="03", ATTR{bInterfaceSubClass}=="01", ATTR{bInterfaceProtocol}=="02", \
  ATTRS{bDeviceClass}=="00", ATTRS{idVendor}=="413c", ATTRS{bmAttributes}=="e0", \
  RUN+="hid2hci --method=dell --devpath=%p", ENV{HID2HCI_SWITCH}="1"

# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[3bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
# Logitech, Inc. diNovo Edge Keyboard
KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c714", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

ENV{DEVTYPE}!="usb_device", GOTO="hid2hci_end"

# When a Dell device recovers from S3, the mouse child needs to be repoked
# Unfortunately the only event seen is the BT device disappearing, so the mouse
# device needs to be chased down on the USB bus.
ATTR{bDeviceClass}=="e0", ATTR{bDeviceSubClass}=="01", ATTR{bDeviceProtocol}=="01", ATTR{idVendor}=="413c", \
  ENV{REMOVE_CMD}="/sbin/udevadm trigger --action=change --subsystem-match=usb --property-match=HID2HCI_SWITCH=1"

# CSR devices
ATTR{idVendor}=="0a12|0458|05ac", ATTR{idProduct}=="1000", RUN+="hid2hci --method=csr --devpath=%p"

LABEL="hid2hci_end"
martin@ubuntu:~$ 
Thanks

---

### Post by jeremy31 on 2016-03-06
Post results for
```
udevadm trigger --dry-run --subsystem-match=usb --attr-match=idVendor=413c --attr-match=idProduct=8162 --verbose
```

And ```
usb-devices | awk '/8162/' RS=
```

---

### Post by martin193 on 2016-03-06
martin@ubuntu:~$ sudo su
[sudo] password for martin: 
root@ubuntu:/home/martin# sudo udevadm trigger --dry-run --subsystem-match=usb --attr-match=idVendor=413c --attr-match=idProduct=8162 --verbose
/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
root@ubuntu:/home/martin# sudo usb-devices | awk '/8162/' RS=
T:  Bus=03 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=8162 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
root@ubuntu:/home/martin#

---

### Post by martin193 on 2016-03-06
I find only this [http://askubuntu.com/questions/296703/ubuntu-13-04-audio-and-bluetooth-issue](http://askubuntu.com/questions/296703/ubuntu-13-04-audio-and-bluetooth-issue)

---

### Post by jeremy31 on 2016-03-06
```
/lib/udev/[COLOR=#000000]hid2hci --method=dell --devpath=/devices/[/COLOR][COLOR=#000000]pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2 --mode=hci
```
Post any output[/COLOR]

---

### Post by martin193 on 2016-03-06
root@ubuntu:/home/martin# /lib/udev/hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2 --mode=hci
error: switching device '/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2' failed.
root@ubuntu:/home/martin#

---

### Post by jeremy31 on 2016-03-06
Are you dual booted with windows?  You should be able to enable the bluetooth in Windows and be able to use it with Ubuntu

You could check ```
dmesg | grep usb3
``` to see what else may be going on

---

