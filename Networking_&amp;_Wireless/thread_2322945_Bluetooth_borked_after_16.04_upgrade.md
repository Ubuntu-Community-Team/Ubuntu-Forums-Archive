---
title: "Bluetooth borked after 16.04 upgrade"
date: 2016-05-01
forum: Networking &amp; Wireless
---

### Post by Evil Wayz on 2016-05-01
Just upgraded to 16.04, and had to add a module to make my wifi work.   Then my bluetooth didn't work.  So I am using CInnamon 3.0 and blueberry.  I don't know if anyone can help me with this, but I can't get all of my bluetooth devices to connect.  Blueberry sees some of them and their status, but there is no tray icon, and its hit or miss what category they are in.  My mouse and one headset are connected but my keyboard and the other headset are not. 

heres the bluetooth info I remember:
```
wolf@shaitan:~$ dmesg | grep -i blue 
[   17.327797] Bluetooth: Core ver 2.21
[   17.327829] Bluetooth: HCI device and connection manager initialized
[   17.327837] Bluetooth: HCI socket layer initialized
[   17.327843] Bluetooth: L2CAP socket layer initialized
[   17.327853] Bluetooth: SCO socket layer initialized
[   26.017023] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.017029] Bluetooth: BNEP filters: protocol multicast
[   26.017037] Bluetooth: BNEP socket layer initialized
[   49.217084] Bluetooth: RFCOMM TTY layer initialized
[   49.217098] Bluetooth: RFCOMM socket layer initialized
[   49.217107] Bluetooth: RFCOMM ver 1.11
[  568.416143] Bluetooth: hci0 SCO packet for unknown connection handle 43
[  568.416151] Bluetooth: hci0 SCO packet for unknown connection handle 43
[  568.416154] Bluetooth: hci0 SCO packet for unknown connection handle 43
```

---

### Post by jeremy31 on 2016-05-01
Post the result of ```
lsusb
``` and I will see if there are any fixes for those errors

---

### Post by Evil Wayz on 2016-05-01
```
wolf@shaitan:~$ lsusb
Bus 001 Device 008: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 007: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 005 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by jeremy31 on 2016-05-01
Post the result of ```
hciconfig -a
``` as it looks like you have 2 bluetooth adapters and one of them might not work correctly

---

### Post by Evil Wayz on 2016-05-02
Ok I tried from command line and this is what I got:

```
wolf@shaitan:~$ bluetoothctl
[NEW] Controller 00:15:83:12:13:FC ChromeLinux_E9AB [default]
[NEW] Device 00:00:00:00:14:31 HBS-760
[NEW] Device 00:11:B1:0A:DD:58 Dacom stereo
[NEW] Device CC:C5:0A:20:7B:88 Bluetooth Keyboard
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[CHG] Controller 00:15:83:12:13:FC Discovering: yes
[bluetooth]# agent on
Agent registered
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# pair
Missing device address argument
[bluetooth]# pair CC:C5:0A:20:7B:88
Attempting to pair with CC:C5:0A:20:7B:88
Failed to pair: org.bluez.Error.ConnectionAttemptFailed

```

---

### Post by Evil Wayz on 2016-05-02
> **jeremy31 said:**
> Post the result of ```
hciconfig -a
``` as it looks like you have 2 bluetooth adapters and one of them might not work correctly


Looks like just one to me.  The Ralink adapter is Wireless N.

```
wolf@shaitan:~$ hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:15:83:12:13:FC  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:725447 acl:78 sco:1766 events:88089 errors:0
	TX bytes:36551412 acl:125897 sco:1680 commands:2950 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0xdb 0xff 0x5b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'ChromeLinux_E9AB'
	Class: 0x0c0104
	Service Classes: Rendering, Capturing
	Device Class: Computer, Desktop workstation
	HCI Version: 4.0 (0x6)  Revision: 0x1d86
	LMP Version: 4.0 (0x6)  Subversion: 0x1d86
	Manufacturer: Cambridge Silicon Radio (10)

```

---

### Post by jeremy31 on 2016-05-02
I wonder if this isn't one of the Cambridge chips that they finally fixed, post results for ```
lsusb -v | grep -A25 0001
```

---

### Post by Evil Wayz on 2016-05-02
> **jeremy31 said:**
> I wonder if this isn't one of the Cambridge chips that they finally fixed, post results for ```
lsusb -v | grep -A25 0001
```

```
wolf@shaitan:~$ lsusb -v | grep -A25 0001
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255

Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x05e3 Genesys Logic, Inc.
  idProduct          0x0606 USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
  bcdDevice            7.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
--
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255

Bus 005 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a12 Cambridge Silicon Radio, Ltd
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
  bcdDevice           75.58
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
--
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
--
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
--
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
Couldn't open device, some information will be missing
--
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
```

Incidentally, every time I restart my computer I have to load the module for that ralink adapter.  I've had trouble with bluetooth and wireless that were solved by one solution before.

---

### Post by jeremy31 on 2016-05-02
Reload the driver?  post ```
modprobe -c | grep 7601
```

---

### Post by Evil Wayz on 2016-05-02
> **jeremy31 said:**
> Reload the driver?  post ```
modprobe -c | grep 7601
```


```
wolf@shaitan:~$ modprobe -c | grep 7601
blacklist mt7601u
alias usb:v0AF0p7601d*dc*dsc*dp*ic*isc*ip*in* hso
alias usb:v0B05p17D3d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v0E8Dp760Ad*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v0E8Dp760Bd*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v13D3p3431d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v13D3p3434d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v148Fp7601d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v148Fp760Ad*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v148Fp760Bd*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v148Fp760Cd*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v148Fp760Dd*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v2001p3D04d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v2717p4106d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v2955p0001d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v2955p1001d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v2A5Fp1000d*dc*dsc*dp*ic*isc*ip*in* mt7601u
alias usb:v7392p7710d*dc*dsc*dp*ic*isc*ip*in* mt7601u

```

---

### Post by Evil Wayz on 2016-05-02
THis is what I type to get my wifi running anytime I reboot.  I realize the second command is just showing me is output.
```
sudo modprobe mt7601u && dmesg | grep mt76
```

---

### Post by jeremy31 on 2016-05-02
See if running ```
sudo depmod -a
```
I am unsure what is happening with bluetooth..will likely have to look at changes in the source code

---

### Post by Evil Wayz on 2016-05-02
> **jeremy31 said:**
> See if running ```
sudo depmod -a
```
I am unsure what is happening with bluetooth..will likely have to look at changes in the source code

command yields no output.

---

### Post by jeremy31 on 2016-05-02
Reboot and see if you need to load the module for wireless manually

---

### Post by Evil Wayz on 2016-05-02
I did and i had to load the module again.  I was told that as of 15.10 this adapter worked automatically.  I have another bluetooth adapter but its got a broadcom chip, and so it needs a patch I can't get to work.

They really need to fix the bluetooth stack.

---

### Post by jeremy31 on 2016-05-02
> **Evil Wayz said:**
> I did and i had to load the module again.  I was told that as of 15.10 this adapter worked automatically.  I have another bluetooth adapter but its got a broadcom chip, and so it needs a patch I can't get to work.

They really need to fix the bluetooth stack.

Another way is to ```
echo mt7601u | sudo tee -a /etc/modules
```

I supposed I had helped in the past with the broadcom but there is a chance I missed it.  What does ```
lsusb; dmesg | egrep -i 'blue|firm'
``` show with the broadcom plugged in?

I use an IOGear GBU521 that has a broadcom chipset for BT, it wants a firmware file but it works for everything but HSP/HFP without it, I have used a mouse/keyboard/and a headset in A2DP with no issue in 15.10.  I haven't taken the time to play with it in 16.10 but I doubt anything has changed with it.  I know some broadcom BT chips won't even scan without the firmware load

---

### Post by Evil Wayz on 2016-05-02
Massive output, but ends with patch not found:

```
wolf@shaitan:~$ lsusb; dmesg | egrep -i 'blue|firm'
Bus 001 Device 008: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 010: ID 1871:01f0 Aveo Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 007: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 005 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 011: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    0.154330] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
[   15.009033] intel_rng: Firmware space is locked read-only. If you can't or
               intel_rng: don't want to disable this in firmware setup, and if
[   17.327797] Bluetooth: Core ver 2.21
[   17.327829] Bluetooth: HCI device and connection manager initialized
[   17.327837] Bluetooth: HCI socket layer initialized
[   17.327843] Bluetooth: L2CAP socket layer initialized
[   17.327853] Bluetooth: SCO socket layer initialized
[   26.017023] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.017029] Bluetooth: BNEP filters: protocol multicast
[   26.017037] Bluetooth: BNEP socket layer initialized
[   49.217084] Bluetooth: RFCOMM TTY layer initialized
[   49.217098] Bluetooth: RFCOMM socket layer initialized
[   49.217107] Bluetooth: RFCOMM ver 1.11
[  244.866443] mt7601u 5-2.4.1:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  568.416143] Bluetooth: hci0 SCO packet for unknown connection handle 43
[  568.416151] Bluetooth: hci0 SCO packet for unknown connection handle 43
[  568.416154] Bluetooth: hci0 SCO packet for unknown connection handle 43
[25742.751378] Bluetooth: hci0: BCM: chip id 63
[25742.783379] Bluetooth: hci0: BCM20702A
[25742.785385] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[25742.884946] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[25742.884956] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found
[25951.088157] Bluetooth: hci0 SCO packet for unknown connection handle 43
[25951.088167] Bluetooth: hci0 SCO packet for unknown connection handle 43
[25951.088172] Bluetooth: hci0 SCO packet for unknown connection handle 43
[28771.224310] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[28771.224329] Bluetooth: HIDP socket layer initialized
[28771.774213] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:45/0005:04E8:7021.0003/input/input19
[28771.780105] hid-generic 0005:04E8:7021.0003: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[29215.799419] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:45/0005:04E8:7021.0004/input/input20
[29215.804108] hid-generic 0005:04E8:7021.0004: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[29428.445412] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0005/input/input21
[29428.449190] hid-generic 0005:04E8:7021.0005: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[29460.684583] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:41/0005:04E8:7021.0006/input/input22
[29460.687692] hid-generic 0005:04E8:7021.0006: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[42839.128160] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0007/input/input23
[42839.130487] hid-generic 0005:04E8:7021.0007: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[87026.181735] Bluetooth: hci0: BCM: chip id 63
[87026.213744] Bluetooth: hci0: BCM20702A
[87026.215734] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[87026.325032] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[87026.325045] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found

```

---

### Post by jeremy31 on 2016-05-02
The ID for this one is the same as my GBU521, except I don't see the ```
 Bluetooth: hci0 SCO packet for unknown connection handle 43
``` error.  What kernel is loaded ```
uname -a
```
I do have the firmware load errors because I haven't loaded the firmware onto this computer as it worked without it.  It works with my mouse, my headset needs charged.  The keyboard works but I bought it to use with my tablet.

You may be drawing too much power on the USB bus.  Do the ```
Bluetooth: hci0 SCO packet for unknown connection handle 43
``` errors disappear with the wifi dongle unplugged?

You have an external hard drive, mouse, keyboard, wifi, and bluetooth connected to USB.  I only have a mouse, bluetooth, and my weather station connected to USB

---

### Post by Evil Wayz on 2016-05-02
> **jeremy31 said:**
> The ID for this one is the same as my GBU521, except I don't see the ```
 Bluetooth: hci0 SCO packet for unknown connection handle 43
``` error.  What kernel is loaded ```
uname -a
```
I do have the firmware load errors because I haven't loaded the firmware onto this computer as it worked without it.  It works with my mouse, my headset needs charged.  The keyboard works but I bought it to use with my tablet.

You may be drawing too much power on the USB bus.  Do the ```
Bluetooth: hci0 SCO packet for unknown connection handle 43
``` errors disappear with the wifi dongle unplugged?

You have an external hard drive, mouse, keyboard, wifi, and bluetooth connected to USB.  I only have a mouse, bluetooth, and my weather station connected to USB

Ok, kernel:
```
wolf@shaitan:~$ uname -a
Linux shaitan 4.4.0-22-generic #38-Ubuntu SMP Sun Apr 24 20:48:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

and out put of the lsusb command with dongle unplugged:
```
wolf@shaitan:~$ lsusb; dmesg | egrep -i 'blue|firm'
Bus 001 Device 008: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 010: ID 1871:01f0 Aveo Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 007: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 005 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    0.154330] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
[   15.009033] intel_rng: Firmware space is locked read-only. If you can't or
               intel_rng: don't want to disable this in firmware setup, and if
[   17.327797] Bluetooth: Core ver 2.21
[   17.327829] Bluetooth: HCI device and connection manager initialized
[   17.327837] Bluetooth: HCI socket layer initialized
[   17.327843] Bluetooth: L2CAP socket layer initialized
[   17.327853] Bluetooth: SCO socket layer initialized
[   26.017023] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.017029] Bluetooth: BNEP filters: protocol multicast
[   26.017037] Bluetooth: BNEP socket layer initialized
[   49.217084] Bluetooth: RFCOMM TTY layer initialized
[   49.217098] Bluetooth: RFCOMM socket layer initialized
[   49.217107] Bluetooth: RFCOMM ver 1.11
[  244.866443] mt7601u 5-2.4.1:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  568.416143] Bluetooth: hci0 SCO packet for unknown connection handle 43
[  568.416151] Bluetooth: hci0 SCO packet for unknown connection handle 43
[  568.416154] Bluetooth: hci0 SCO packet for unknown connection handle 43
[25742.751378] Bluetooth: hci0: BCM: chip id 63
[25742.783379] Bluetooth: hci0: BCM20702A
[25742.785385] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[25742.884946] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[25742.884956] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found
[25951.088157] Bluetooth: hci0 SCO packet for unknown connection handle 43
[25951.088167] Bluetooth: hci0 SCO packet for unknown connection handle 43
[25951.088172] Bluetooth: hci0 SCO packet for unknown connection handle 43
[28771.224310] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[28771.224329] Bluetooth: HIDP socket layer initialized
[28771.774213] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:45/0005:04E8:7021.0003/input/input19
[28771.780105] hid-generic 0005:04E8:7021.0003: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[29215.799419] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:45/0005:04E8:7021.0004/input/input20
[29215.804108] hid-generic 0005:04E8:7021.0004: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[29428.445412] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0005/input/input21
[29428.449190] hid-generic 0005:04E8:7021.0005: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[29460.684583] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:41/0005:04E8:7021.0006/input/input22
[29460.687692] hid-generic 0005:04E8:7021.0006: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[42839.128160] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0007/input/input23
[42839.130487] hid-generic 0005:04E8:7021.0007: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[87026.181735] Bluetooth: hci0: BCM: chip id 63
[87026.213744] Bluetooth: hci0: BCM20702A
[87026.215734] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[87026.325032] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[87026.325045] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found

```

Im not so much worried about the broadcom bluetooth adapter since the other one works, mostly.

---

### Post by jeremy31 on 2016-05-02
Still not sure what is going on.  I am using 4.4.0-21 and don't have any custom patches in my bluetooth- not yet

Can you also unplug the USB hard drive or is that what you installed Ubuntu on?

---

### Post by Evil Wayz on 2016-05-03
> **jeremy31 said:**
> Another way is to ```
echo mt7601u | sudo tee -a /etc/modules
```



I tried that and it showed it was there, but it didn't work until I did this:

```
sudo modprobe mt7601u && dmesg | grep mt76
```

I notice it says there's an eeprom error?

```
[ 1418.406905] mt7601u 5-2.4.1:1.0: Warning: unsupported EEPROM version 0d
[ 1418.406913] mt7601u 5-2.4.1:1.0: EEPROM ver:0d fae:00
```

---

### Post by jeremy31 on 2016-05-03
I wonder if that module is blacklisted somewhere?

There are some module parameters for bluetooth and btusb.  You can see them with ```
modinfo -p btusb
modinfo -p bluetooth
``` If you have set module parameters before just try the one that mention SCO

---

### Post by Evil Wayz on 2016-05-03
> **jeremy31 said:**
> I wonder if that module is blacklisted somewhere?

There are some module parameters for bluetooth and btusb.  You can see them with ```
modinfo -p btusb
modinfo -p bluetooth
``` If you have set module parameters before just try the one that mention SCO

I'm not sure I know what you want me to do so here's the output of that:

```
wolf@shaitan:~$ modinfo -p btusb
disable_scofix:Disable fixup of wrong SCO buffer size (bool)
force_scofix:Force fixup of wrong SCO buffers size (bool)
reset:Send HCI reset command on initialization (bool)
wolf@shaitan:~$ modinfo -p bluetooth
disable_esco:Disable eSCO connection creation (bool)
disable_ertm:Disable enhanced retransmission mode (bool)
```

---

### Post by jeremy31 on 2016-05-03
A few things we can try with either bluetooth dongle since they have the same issue. ```
sudo modprobe -r btusb
sudo modprobe btusb disable_scofix=Y
```

Try using bluetooth for a while and see if the SCO messages are in the dmesg log

And to see if you wireless module is blacklisted
```
grep [[:alnum:]] /etc/modprobe.d/* | grep mt7601u
```

---

### Post by Evil Wayz on 2016-05-04
> **jeremy31 said:**
> 

Try using bluetooth for a while and see if the SCO messages are in the dmesg log 

I don't know how to do that. 

> And to see if you wireless module is blacklisted
```
grep [[:alnum:]] /etc/modprobe.d/* | grep mt7601u
```

OOUtput:
```
wolf@shaitan:~$ grep [[:alnum:]] /etc/modprobe.d/* | grep mt7601u
/etc/modprobe.d/blacklist-mt7601u.conf:blacklist mt7601u
wolf@shaitan:~$ 

```

Is it blacklisted?  Because when I woke up this morning it had connected to my router on it's own.

---

### Post by jeremy31 on 2016-05-04
```
sudo rm /etc/modprobe.d/blacklist-mt7601u.conf
``` The module should load on its own

And you can check for bluetooth errors ```
dmesg | grep -i bluetooth
```

---

### Post by Evil Wayz on 2016-05-04
Ok this is the log, what am I looking for in here?```
wolf@shaitan:~$ dmesg | grep -i bluetooth
[   14.360284] Bluetooth: Core ver 2.21
[   14.360324] Bluetooth: HCI device and connection manager initialized
[   14.360850] Bluetooth: HCI socket layer initialized
[   14.360860] Bluetooth: L2CAP socket layer initialized
[   14.360876] Bluetooth: SCO socket layer initialized
[   25.497829] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.497835] Bluetooth: BNEP filters: protocol multicast
[   25.497843] Bluetooth: BNEP socket layer initialized
[   59.735467] Bluetooth: RFCOMM TTY layer initialized
[   59.735479] Bluetooth: RFCOMM socket layer initialized
[   59.735487] Bluetooth: RFCOMM ver 1.11
[31588.907929] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[31588.907943] Bluetooth: HIDP socket layer initialized
[31588.910951] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0003/input/input13
[31588.911897] hid-generic 0005:04E8:7021.0003: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[32269.486290] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0004/input/input14
[32269.487863] hid-generic 0005:04E8:7021.0004: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[33165.791396] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0005/input/input15
[33165.793649] hid-generic 0005:04E8:7021.0005: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[34833.916318] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0006/input/input16
[34833.917588] hid-generic 0005:04E8:7021.0006: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[35463.877475] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0007/input/input17
[35463.878090] hid-generic 0005:04E8:7021.0007: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[36501.039669] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0008/input/input18
[36501.040630] hid-generic 0005:04E8:7021.0008: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[37625.574007] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0009/input/input19
[37625.575320] hid-generic 0005:04E8:7021.0009: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[40237.294308] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.000A/input/input20
[40237.294864] hid-generic 0005:04E8:7021.000A: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[40449.742926] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.000B/input/input21
[40449.747514] hid-generic 0005:04E8:7021.000B: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[41468.911639] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.000C/input/input22
[41468.912447] hid-generic 0005:04E8:7021.000C: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[41790.487210] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:43/0005:04E8:7021.000D/input/input23
[41790.493326] hid-generic 0005:04E8:7021.000D: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[43429.174027] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.000E/input/input24
[43429.177068] hid-generic 0005:04E8:7021.000E: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[43558.712519] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.000F/input/input25
[43558.714614] hid-generic 0005:04E8:7021.000F: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[44314.149188] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0010/input/input26
[44314.154186] hid-generic 0005:04E8:7021.0010: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[45403.627759] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0011/input/input27
[45403.645864] hid-generic 0005:04E8:7021.0011: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[45432.111610] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:43/0005:04E8:7021.0012/input/input28
[45432.116133] hid-generic 0005:04E8:7021.0012: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[46351.382944] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0013/input/input29
[46351.391609] hid-generic 0005:04E8:7021.0013: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[46795.774407] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0014/input/input30
[46795.778852] hid-generic 0005:04E8:7021.0014: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[51244.107710] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0015/input/input31
[51244.109338] hid-generic 0005:04E8:7021.0015: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[58097.949398] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:43/0005:04E8:7021.0016/input/input33
[58097.950203] hid-generic 0005:04E8:7021.0016: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
wolf@shaitan:~$ 

```

---

### Post by jeremy31 on 2016-05-04
I don't see any SCO errors anymore.  Does the bluetooth keyboard work properly?

---

### Post by Evil Wayz on 2016-05-04
> **jeremy31 said:**
> I don't see any SCO errors anymore.  Does the bluetooth keyboard work properly?

Both headphones connect, but they no longer say "connected" i Have to go into bluetooth or sound settings to confirm.  The keyboard also connects, but the little battery status icon no longer appears in the panel. Also, I STILL don't have a bluetooth indicator on my panel when bluetooth is enabled and visible.  But It works, so I'll take it.  I probably should have waited for the point release, but I've never stuck with the LTS  version before, I used to upgrade everytime a new release came out.

Hey, is there a way I can disable HSP/HFP or force AD2P?  Every now and again the headset wants to connect as a headset, and when I try to switch it it goes back to speakers.  I have to open and close the sound dialog box for it to decide to work.

---

### Post by jeremy31 on 2016-05-04
The battery and bluetooth icons missing might be a cinnamon bug

I haven't found a way to disable HSP/HFP in 16.04 yet but I haven't installed pavucontrol, a pulse audio control package either

And if the change above helped
```
echo "options btusb disable_scofix=Y" | sudo tee /etc/modprobe.d/btusb.conf
```
That way you won't have to  ```
sudo modprobe -r btusb
sudo modprobe btusb disable_scofix=Y
```

After every reboot

---

### Post by Evil Wayz on 2016-05-11
After the newest set of upgrades, two of my three devices could connect.  MY second headset i got to pair and connect using bluetoothctl.  But I can't get audio to send.  It shows up in the sound devices dialog box, and I can even switch between profiles. It just gives me nothing when I test it.

---

### Post by Evil Wayz on 2016-05-20
Latest daily upgrade, bluetooth audio doesn't work.  Headsets remain paired and they show connected.

---

### Post by jeremy31 on 2016-05-20
I would suggest filing a bug report, see [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

File it against package linux as we have no idea what is actually causing the problem, whether it is a kernel issue, bluez, or pulse audio

---

### Post by Evil Wayz on 2016-05-20
Ok I did that.  This is weird, this is the second time bluetooth has crapped the bed and then after the next upgrade was fine.  Hopefully that will happen soon. Headphones with a fifteen foot cord are a PITA>

---

### Post by jeremy31 on 2016-05-20
I have a Logitech wireless headset, H600 according to lsusb results that works well.  It is reported that it uses bluetooth but I suspect that the USB dongle and headset are hard coded to each other.  The dongle or headset can't be used as a normal bluetooth device but it has been plug and play in Ubuntu

Just saw the bug report.  Good description of the issue

---

### Post by Evil Wayz on 2016-05-20
Thanks.  I have two dongles, an iogear and a generic one.  Both worked with my headsets in 14.04.  A day or so ago i had to connect them by hand, setting my devices on discoverable and then hitting connect.  They worked after that, but it was a pain, considering i have a bluetooth mini keyboard specifically so i don't have to get my lazy butt out of bed to pause the video.  Now it connects fine but only the keyboard actually works. I'm at a loss how stuff like this happens.  Again, I should have waited for the point release, and for Cinnamon to be added to the official repos.

---

### Post by Evil Wayz on 2016-05-20
I'm getting those SCO ewrrors again, if that helps.  
```
wolf@shaitan:~$ dmesg | grep -i bluetooth
[   13.127003] Bluetooth: Core ver 2.21
[   13.127032] Bluetooth: HCI device and connection manager initialized
[   13.127039] Bluetooth: HCI socket layer initialized
[   13.127045] Bluetooth: L2CAP socket layer initialized
[   13.127056] Bluetooth: SCO socket layer initialized
[   23.725690] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.725696] Bluetooth: BNEP filters: protocol multicast
[   23.725703] Bluetooth: BNEP socket layer initialized
[   62.816058] Bluetooth: RFCOMM TTY layer initialized
[   62.816097] Bluetooth: RFCOMM socket layer initialized
[   62.816106] Bluetooth: RFCOMM ver 1.11
[15273.444167] Bluetooth: hci0 SCO packet for unknown connection handle 45
[15282.084159] Bluetooth: hci0 SCO packet for unknown connection handle 41
[15282.084167] Bluetooth: hci0 SCO packet for unknown connection handle 41
[15282.084170] Bluetooth: hci0 SCO packet for unknown connection handle 41
[15599.857998] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[15599.858013] Bluetooth: HIDP socket layer initialized
[15599.863401] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0003/input/input16
[15599.870877] hid-generic 0005:04E8:7021.0003: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[15608.662667] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:43/0005:04E8:7021.0004/input/input17
[15608.666362] hid-generic 0005:04E8:7021.0004: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[17352.662809] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0005/input/input19
[17352.665351] hid-generic 0005:04E8:7021.0005: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[21436.508498] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0006/input/input20
[21436.509358] hid-generic 0005:04E8:7021.0006: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[22420.778031] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0007/input/input21
[22420.778761] hid-generic 0005:04E8:7021.0007: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[27935.798830] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0008/input/input23
[27935.809387] hid-generic 0005:04E8:7021.0008: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
[29331.184455] input: Bluetooth Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/bluetooth/hci0/hci0:40/0005:04E8:7021.0009/input/input24
[29331.189625] hid-generic 0005:04E8:7021.0009: input,hidraw2: BLUETOOTH HID v1.1b Keyboard [Bluetooth Keyboard] on 00:15:83:12:13:fc
wolf@shaitan:~$ 
```

---

### Post by jeremy31 on 2016-05-21
Was this a clean install of 16.04?  There might be unneeded files remaining if it wasn't

Does the Live DVD/USB work correctly?

Also see if pavucontrol is installed ```
dpkg -l | grep pavucontrol
```

If it is installed open it with ```
pavucontrol
``` and scroll through to make sure the bluetooth audio isn't muted there

---

### Post by Evil Wayz on 2016-05-28
I deleted both headset profiles and set them up again and now audio works perfectly.

Always try the simplest solution first.

---

