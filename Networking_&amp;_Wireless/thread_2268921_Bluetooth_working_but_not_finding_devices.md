---
title: "Bluetooth working but not finding devices"
date: 2015-03-12
forum: Networking &amp; Wireless
---

### Post by danny44 on 2015-03-12
Bluetooth appears to be up and running but when i scan for devices it sits at "searching for devices" indefinitely without finding anything. strangely I can pair with my phone when I initiate the connection from my phone. but obviously I cant pair devices like headsets and mice that cant initiate the pairing

I get the same result when running "hcitool scan" but it times out after about 5 seconds

also installed blueman as the bt manager and it also scanned indefinitely

the bluetooh daemon appears to be showing an error. the BT is part of a dual intel 7260 bt/wi-fi card. Could it be that the BT sw doesnt like the fact that the device id is being used already as wlan?

```

sudo bluetoothd -nd
bluetoothd[2766]: Bluetooth daemon 4.101
bluetoothd[2766]: src/main.c:parse_config() parsing main.conf
bluetoothd[2766]: src/main.c:parse_config() discovto=0
bluetoothd[2766]: src/main.c:parse_config() pairto=0
bluetoothd[2766]: src/main.c:parse_config() pageto=8192
bluetoothd[2766]: src/main.c:parse_config() auto_to=60
bluetoothd[2766]: src/main.c:parse_config() name=%h-%d
bluetoothd[2766]: src/main.c:parse_config() class=0x000100
bluetoothd[2766]: src/main.c:parse_config() Key file does not have key 'DeviceID'
D-Bus setup failed: Name already in use
bluetoothd[2766]: Unable to get on D-Bus

```


everything else looks good:
```

hcitool dev
Devices:
    hci0    FC:F8:AE:5F:4F:87

```

```

rfkill list
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```

sudo /etc/init.d/bluetooth status
 * bluetooth is running

```

```

sudo service bluetooth status
bluetooth start/running, process 5762

```

```

hciconfig -a
hci0:    Type: BR/EDR  Bus: USB
    BD Address: FC:F8:AE:5F:4F:87  ACL MTU: 1021:5  SCO MTU: 96:5
    UP RUNNING PSCAN ISCAN INQUIRY
    RX bytes:2220 acl:0 sco:0 events:283 errors:0
    TX bytes:2778 acl:0 sco:0 commands:234 errors:0
    Features: 0xff 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
    Link policy: RSWITCH HOLD SNIFF
    Link mode: SLAVE ACCEPT
    Name: 'ubuntu-0'
    Class: 0x6c0100
    Service Classes: Rendering, Capturing, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 4.0 (0x6)  Revision: 0x500
    LMP Version: 4.0 (0x6)  Subversion: 0x500
    Manufacturer: Intel Corp. (2)

```

```

Bus 001 Device 006: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 004: ID 8087:07dc Intel Corp.
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 8087:8000 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0c45:649d Microdia
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

bt card: Intel 7260 dual wi-fi/bt
system: dell e5540
os: 14.04.2 LTS
kernel: 3.13.0-46-generic

---

### Post by jeremy31 on 2015-03-12
Is linux-firmware installed? ```
sudo apt-get install linux-firmware
``` I wish I had more ideas as I just tested the only laptop I have that can use my 7260 card and it picked up my android phone and my laptop with an Atheros wifi/bluetooth chip.  I tried a kernel older than yours and 3.16.0-31

---

