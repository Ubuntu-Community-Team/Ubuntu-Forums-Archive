---
title: "UBUNTU 17.04 Bluetooth Cant Find Headset, Won't Stop Searching for Devices"
date: 2017-06-04
forum: Networking &amp; Wireless
---

### Post by mrlnagstn on 2017-06-04
So, it's actually my first time using the bluetooth in my laptop and I want to connect a bluetooth headset to it, but when i tried to find the headset the bluetooth program won't stop searching for devices even though I've already set the headset to pairing mode.
It also can't detect my phone (bluetooth visibility turned on).

Also there was one instance where the laptop actually detected the headset, but it failed to pair with it, even when the headset was already in pairing mode.

what should i do guys? thanks in advance!

---

### Post by jeremy31 on 2017-06-04
Post results from terminal for
```
lspci -nnk | grep -iA3 net; lsusb; hciconfig -a; rfkill list all; dmesg | egrep -i 'blue|firm'
```

---

### Post by mrlnagstn on 2017-06-04
here are the results for [COLOR=#000000][FONT=&amp]lspci -nnk | grep -iA3 net[/FONT][/COLOR]
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lite-On Communications Inc RTL8723BE PCIe Wireless Network Adapter [11ad:1724]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be



```
and this one's for [COLOR=#000000][FONT=&amp]lsusb[/FONT][/COLOR] 
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b719 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04f2:b52b Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Result for[COLOR=#000000][FONT=&amp]hciconfig -a[/FONT][/COLOR]   
```

hci0:    Type: Primary  Bus: USB
    BD Address: B8:86:87:F7:6F:60  ACL MTU: 820:8  SCO MTU: 255:16
    DOWN 
    RX bytes:1225 acl:0 sco:0 events:122 errors:0
    TX bytes:23230 acl:0 sco:0 commands:132 errors:0
    Features: 0xff 0xff 0xff 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT

```
and the results for [COLOR=#000000][FONT=&amp]rfkill list all[/FONT][/COLOR]  are:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
and finally for [COLOR=#000000][FONT=&amp]dmesg | egrep -i 'blue|firm'[/FONT][/COLOR] :
```

[    0.173237] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.155955] [drm] GuC firmware load skipped
[    2.095480] usb 1-8: Product: Bluetooth Radio 
[   19.980781] Bluetooth: Core ver 2.22
[   19.980797] Bluetooth: HCI device and connection manager initialized
[   19.980809] Bluetooth: HCI socket layer initialized
[   19.980810] Bluetooth: L2CAP socket layer initialized
[   19.980814] Bluetooth: SCO socket layer initialized
[   20.135560] Bluetooth: HCI UART driver ver 2.3
[   20.135561] Bluetooth: HCI UART protocol H4 registered
[   20.135561] Bluetooth: HCI UART protocol BCSP registered
[   20.135562] Bluetooth: HCI UART protocol LL registered
[   20.135562] Bluetooth: HCI UART protocol ATH3K registered
[   20.135563] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   20.135580] Bluetooth: HCI UART protocol Intel registered
[   20.135592] Bluetooth: HCI UART protocol Broadcom registered
[   20.135593] Bluetooth: HCI UART protocol QCA registered
[   20.135593] Bluetooth: HCI UART protocol AG6XX registered
[   20.135594] Bluetooth: HCI UART protocol Marvell registered
[   21.685716] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   22.906802] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   22.906803] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   22.980159] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   22.980161] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   22.980164] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   22.986782] Bluetooth: hci0: rom_version status=0 version=1
[   22.986788] Bluetooth: cfg_sz 0, total size 22496
[   23.531527] elan_i2c i2c-ELAN1000:00: Elan Touchpad: Module ID: 0x0005, Firmware: 0x0004, Sample: 0x000d, IAP: 0x000e
[   26.338462] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.338463] Bluetooth: BNEP filters: protocol multicast
[   26.338466] Bluetooth: BNEP socket layer initialized
[   48.941457] Bluetooth: RFCOMM TTY layer initialized
[   48.941471] Bluetooth: RFCOMM socket layer initialized
[   48.941486] Bluetooth: RFCOMM ver 1.11
[   92.898751] Bluetooth: hci0 urb ffff92b67a6fda80 failed to resubmit (113)
[  274.852456] Bluetooth: hci0 urb ffff92b6170540c0 failed to resubmit (113)
[  284.907389] Bluetooth: hci0 urb ffff92b605f20840 failed to resubmit (113)
[  288.868605] Bluetooth: hci0 urb ffff92b605c6b9c0 failed to resubmit (113)
[  299.742297] Bluetooth: hci0 urb ffff92b610f41780 failed to resubmit (113)
[  307.745319] Bluetooth: hci0 urb ffff92b6298589c0 failed to resubmit (113)
[  317.853349] Bluetooth: hci0 urb ffff92b625bbbb40 failed to resubmit (113)
[  498.792512] Bluetooth: hci0 urb ffff92b6242169c0 failed to resubmit (113)
[  512.919439] Bluetooth: hci0 urb ffff92b605f38840 failed to resubmit (113)
[  641.939744] Bluetooth: hci0 urb ffff92b532849180 failed to resubmit (113)

``` 
[COLOR=#000000][FONT=&amp]
do u have any idea what's wrong with it? thanks for the help mate :)
[/FONT][/COLOR]

---

### Post by mrlnagstn on 2017-06-04
PS It says the bluetooth is disabled now. I might have done something to it. :))

---

### Post by jeremy31 on 2017-06-04
Do you have tlp installed?

---

### Post by mrlnagstn on 2017-06-04
Nope, but I just installed it.

---

### Post by jeremy31 on 2017-06-04
I didn't want you to install it as tlp has been known to cause issues similar to yours with that bluetooth chip but since it is installed we can try the fix for tlp
```
sudo sed -i 's/#USB_BLACKLIST="1111:2222 3333:4444"/USB_BLACKLIST="0bda:b719"/' /etc/default/tlp
```
Shutdown and restart

---

