---
title: "Bluetooth issue after upgrading from 18.04 to 20.04"
date: 2021-09-01
forum: Networking &amp; Wireless
---

### Post by tizki on 2021-09-01
Hi,

I upgraded my Ubuntu from 18.04 to 20.04. Since then I cannot use Bluetooth.
It seems that it fails to discover the Bluetooth devices. In 18.04 it paired and worked successfully. (For example sony headphones)
I'm using the same BT dongle as I did on 18.04

I tried re-installing bluez, blueman, pulse modules unloading and loading bluetooth modules, but so far nothing works.

any help with debugging / fixing this issue will be much appreciated.

Thanks!

My system info:
```
Ubuntu 20.04.3 LTS 5.4.0-80-generic
Dell OptiPlex 7040 (Desktop)
```

```
&#10095; lsmod | grep bluetooth
bluetooth             548864  41 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth

```

```
&#10095; rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```
&#10095; hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 00:1A:7D:DA:71:10  ACL MTU: 640:4  SCO MTU: 64:8
    UP RUNNING 
    RX bytes:961 acl:0 sco:0 events:65 errors:0
    TX bytes:4902 acl:0 sco:0 commands:60 errors:0
    Features: 0xff 0xff 0x8f 0xfa 0xdb 0xff 0x5b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'my-ubuntu'
    Class: 0x0005a0
    Service Classes: Unspecified
    Device Class: Peripheral, Pointing device/(reserved)
    HCI Version: 4.0 (0x6)  Revision: 0x3120
    LMP Version: 4.0 (0x6)  Subversion: 0x22bb
    Manufacturer: Cambridge Silicon Radio (10)
```

```
&#10095; dmesg | grep -i blue
[    5.331737] Bluetooth: Core ver 2.22
[    5.331748] Bluetooth: HCI device and connection manager initialized
[    5.331750] Bluetooth: HCI socket layer initialized
[    5.331752] Bluetooth: L2CAP socket layer initialized
[    5.331754] Bluetooth: SCO socket layer initialized
[    9.227332] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.227333] Bluetooth: BNEP filters: protocol multicast
[    9.227336] Bluetooth: BNEP socket layer initialized
[   22.658618] Bluetooth: RFCOMM TTY layer initialized
[   22.658622] Bluetooth: RFCOMM socket layer initialized
[   22.658625] Bluetooth: RFCOMM ver 1.11
[   24.670922] Bluetooth: hci0: command 0x0c24 tx timeout
[   26.682930] Bluetooth: hci0: command 0x0c52 tx timeout
[   31.355221] Bluetooth: hci0: setting interface failed (110)
[  811.912992] Bluetooth: hci0: command 0x0c14 tx timeout
[  951.305268] Bluetooth: hci0: advertising data len corrected
[  982.025282] Bluetooth: hci0: advertising data len corrected
[ 1273.885279] Bluetooth: hci0: Received unexpected HCI Event 00000000
[ 1273.950301] Bluetooth: hci0: advertising data len corrected
[ 1301.126101] Bluetooth: hci0: command 0x200c tx timeout
[ 1303.142130] Bluetooth: hci0: command 0x2005 tx timeout
[ 1305.158149] Bluetooth: hci0: command 0x200b tx timeout
[ 1307.174116] Bluetooth: hci0: command 0x200c tx timeout
[ 1309.190100] Bluetooth: hci0: command 0x0401 tx timeout
[ 1311.206192] Bluetooth: hci0: command 0x200c tx timeout
[ 1313.222017] Bluetooth: hci0: command 0x200b tx timeout
[ 1315.238161] Bluetooth: hci0: command 0x200c tx timeout
[ 1316.823377] Bluetooth: hci0: advertising data len corrected
[ 1332.487262] Bluetooth: hci0: advertising data len corrected
[ 1462.309285] Bluetooth: hci0: command 0x200c tx timeout
[ 1472.092275] Bluetooth: hci0: advertising data len corrected



```

```
journalctl -u bluetooth.service
Sep 01 18:04:21 my-ubuntu systemd[1]: Started Bluetooth service.Sep 01 18:04:21 my-ubuntu bluetoothd[7389]: Starting SDP server
Sep 01 18:04:21 my-ubuntu bluetoothd[7389]: Bluetooth management interface 1.14 initialized
Sep 01 18:04:21 my-ubuntu bluetoothd[7389]: Endpoint registered: sender=:1.155 path=/MediaEndpoint/A2DPSink/sbc
Sep 01 18:04:21 my-ubuntu bluetoothd[7389]: Endpoint registered: sender=:1.155 path=/MediaEndpoint/A2DPSource/sbc
Sep 01 18:04:23 my-ubuntu bluetoothd[7389]: Loading LTKs timed out for hci0
Sep 01 18:04:35 my-ubuntu bluetoothd[7389]: Failed to set mode: Failed (0x03)
Sep 01 18:04:46 my-ubuntu bluetoothd[7389]: Failed to set mode: Failed (0x03)



```

---

### Post by tizki on 2021-09-02
I upgraded the kernel to 5.10.0-051000-generic and now the Bluetooth works

---

