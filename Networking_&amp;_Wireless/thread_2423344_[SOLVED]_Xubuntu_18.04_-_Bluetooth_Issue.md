---
title: "[SOLVED] Xubuntu 18.04 - Bluetooth Issue"
date: 2019-07-21
forum: Networking &amp; Wireless
---

### Post by cashewhunter on 2019-07-21
Hello guys... a little help here!...my bluetooth doesn't work...the bluetooth adapter app opens a very small window with no content at all...the bluetooth manager opens but all toolbar buttons are greyed out except for the view and help buttons.

Here's the result of this command

```
uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
```


```
4.18.0-25-generic
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:8207 Hewlett-Packard FHA-3510 2.4GHz Wireless Optical Mobile Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell 88E8040 PCI-E Fast Ethernet Controller [1028:02aa]
    Kernel driver in use: sky2
    Kernel modules: sky2
0c:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.064205] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.220854] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[   19.747425] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[  505.628709] Bluetooth: Core ver 2.22
[  505.628751] Bluetooth: HCI device and connection manager initialized
[  505.628758] Bluetooth: HCI socket layer initialized
[  505.628761] Bluetooth: L2CAP socket layer initialized
[  505.628774] Bluetooth: SCO socket layer initialized
[ 1016.068509] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 1016.068511] Bluetooth: BNEP filters: protocol multicast
[ 1016.068517] Bluetooth: BNEP socket layer initialized
```

---

### Post by jeremy31 on 2019-07-21
I see no signs of a bluetooth adapter being present from those results

---

### Post by cashewhunter on 2019-07-21
[FONT=arial]that's the problem, i was using older version and the bluetooth was working fine, then i decided to completely get rid of it and install the newest version...sort of starting clean... i don't know what happened...now the bluetooth manager doesn't even open with a msg indicates that bluez daemon is not active...i followed a command to open it manually[/FONT]

```
sudo /etc/init.d/bluetooth start
```

[FONT=arial]after that the bluetooth managment worked fine (but the system still couldn't reconize the adapter)
then after an hour or so it(bluetooth management) went back dead, and no matter how many times i try to restart it, it won't start, just shows the same msg that bluez is not working[/FONT]

```
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:bluetoothd(8)
```

[FONT=arial]i tried to purge the bluez, bluez-tools and reinstalled them but the gui is gone!....the laptop has built-in bluetooth.[/FONT]

---

### Post by cashewhunter on 2019-07-23
So, i tried to uninstall and reinstall bluez, blueman and rfkill...and for some reason it now works....the bluetooth manager can detect devices but pairing always fails.
I noticed something strange in the syslog....

these messages keep appearing endlessly

```
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
Jul 23 15:24:04 magid-lt systemd-udevd[305]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0' failed with exit code 1.
Jul 23 15:24:04 magid-lt upowerd[5877]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
```

udevadm monitor result (endless messages also)

```
KERNEL[2128.001632] bind     /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0 (usb)
KERNEL[2128.003909] unbind   /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0 (usb)
UDEV  [2128.004733] unbind   /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0 (usb)
KERNEL[2128.024831] bind     /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0 (usb)
KERNEL[2128.026934] unbind   /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0 (usb)
UDEV  [2128.027872] bind     /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0 (usb)
```

strace output for systemd-udevd (endless also)

[https://paste.ubuntu.com/p/7HkTqB2kZX/](https://paste.ubuntu.com/p/7HkTqB2kZX/)

and back again

```
uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
4.18.0-25-generic
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:8207 Hewlett-Packard FHA-3510 2.4GHz Wireless Optical Mobile Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell 88E8040 PCI-E Fast Ethernet Controller [1028:02aa]
    Kernel driver in use: sky2
    Kernel modules: sky2
0c:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
hci0:    Type: Primary  Bus: USB
    BD Address: 00:24:2B:F9:93:12  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING 
    RX bytes:1166 acl:0 sco:0 events:70 errors:0
    TX bytes:5363 acl:0 sco:0 commands:70 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'magid-lt'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 2.1 (0x4)  Revision: 0x50ad
    LMP Version: 2.1 (0x4)  Subversion: 0x423d
    Manufacturer: Broadcom Corporation (15)

[    0.064205] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.223181] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[   15.713361] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   15.720931] b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2
[   15.720958] b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2
[   15.720987] b43 ssb0:0: Direct firmware load for b43-open/ucode15.fw failed with error -2
[   15.720999] b43 ssb0:0: Direct firmware load for b43-open/ucode15.fw failed with error -2
[   15.721001] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   15.721006] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   15.721009] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   17.309121] usb 3-1.3: Product: Dell Wireless 365 Bluetooth Module
[   17.478861] Bluetooth: Core ver 2.22
[   17.478901] Bluetooth: HCI device and connection manager initialized
[   17.478906] Bluetooth: HCI socket layer initialized
[   17.478910] Bluetooth: L2CAP socket layer initialized
[   17.478919] Bluetooth: SCO socket layer initialized
[   24.943660] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.943662] Bluetooth: BNEP filters: protocol multicast
[   24.943668] Bluetooth: BNEP socket layer initialized
[   55.027839] Bluetooth: RFCOMM TTY layer initialized
[   55.027848] Bluetooth: RFCOMM socket layer initialized
[   55.027857] Bluetooth: RFCOMM ver 1.11
```

---

### Post by cashewhunter on 2019-07-25
issue resolved following the below steps.

from [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1759836/comments/70](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1759836/comments/70)

 I think I've figured out the answer.


  Run 
  ```
/lib/systemd/systemd-udevd -D
```
  should print garbage in endless loop containing ".../97-hid2hci.rules:"
  If so, edit  /lib/udev/rules.d/97-hid2hci.rules
  and add
  ```
ACTION=="add"
``` 
  in front of line  mentioned by above command.
  It should be something like this (I'm using fedora 28, but the problem looked identical):
  ```
ACTION=="add", ATTR{bInterfaceClass}=="03", ATTR{bInterfaceSubClass}=="01", ATTR{bInterfaceProtocol}=="02", \
  ATTRS{bDeviceClass}=="00", ATTRS{idVendor}=="413c", ATTRS{bmAttributes}=="e0", \
  RUN+="hid2hci --method=dell --devpath=%p", ENV{HID2HCI_SWITCH}="1"
```
  With above fix, everything works perfect on my old Dell. Hope that helps ;)

---

