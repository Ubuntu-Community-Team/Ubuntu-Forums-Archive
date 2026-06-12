---
title: "Bluetooth working, but &quot;No bluetooth found&quot; on GUI"
date: 2017-04-05
forum: Networking &amp; Wireless
---

### Post by Gabor_Botzheim on 2017-04-05
Hello, I have a problem with my bluetooth. The device is recognised and working, but the GUI does not register it (see Pic, plug in dongle to use BT):
[ATTACH=CONFIG]274434[/ATTACH]
As you can see, I connected it to a Microsoft Surface , but I am not offered a send file dialog.
CLI works with bluetooth-sendto, but this is not an alternative for most.
What could be the problem?

```
uname -a
Linux GaborNB 4.4.0-71-generic #92-Ubuntu SMP Fri Mar 24 12:59:01 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

dmesg:
```
dmesg | grep Blue
[    7.010346] Bluetooth: Core ver 2.21
[    7.010396] Bluetooth: HCI device and connection manager initialized
[    7.013795] Bluetooth: HCI socket layer initialized
[    7.013798] Bluetooth: L2CAP socket layer initialized
[    7.013804] Bluetooth: SCO socket layer initialized
[    7.377962] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.377965] Bluetooth: BNEP filters: protocol multicast
[    7.377970] Bluetooth: BNEP socket layer initialized
[   11.935749] Bluetooth: RFCOMM TTY layer initialized
[   11.935757] Bluetooth: RFCOMM socket layer initialized
[   11.935762] Bluetooth: RFCOMM ver 1.11

```

```
bluetoothctl 
[NEW] Controller E0:CA:94:50:DF:D3 GaborNB [default]
[NEW] Device 40:16:3B:48:4E:77 [TV] Samsung 6 Series (40)
[NEW] Device 62:C7:00:00:00:00 HTC_HD2
[NEW] Device 60:02:92:F8:96:E3 DESKTOP-BUNCVV4
[NEW] Device C0:EE:FB:92:20:FB OnePlus2
[NEW] Device FC:58:FA:83:F0:5C Paradies Sound-Box
[bluetooth]# agent on
Agent registered
[CHG] Controller E0:CA:94:50:DF:D3 Discoverable: yes
[CHG] Controller E0:CA:94:50:DF:D3 DiscoverableTimeout: 0x000000
[CHG] Controller E0:CA:94:50:DF:D3 DiscoverableTimeout: 0x000000
[CHG] Controller E0:CA:94:50:DF:D3 Discovering: yes
[CHG] Device 60:02:92:F8:96:E3 RSSI: -39
[bluetooth]# scan on
Discovery started
[DEL] Device 62:C7:00:00:00:00 HTC_HD2
[DEL] Device 40:16:3B:48:4E:77 [TV] Samsung 6 Series (40)
[bluetooth]# scan off
Discovery stopped

```
```
hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: E0:CA:94:50:DF:D3  ACL MTU: 310:10  SCO MTU: 64:8
    UP RUNNING PSCAN ISCAN 
    RX bytes:3984023 acl:16891 sco:0 events:21543 errors:0
    TX bytes:14078708 acl:57169 sco:0 commands:241 errors:0

```

---

### Post by tamashumi on 2017-12-04
@Gabor_Botzheim any luck solving this?
I'm facing the exact same problem, quote annoying.

I've posted a question on [a question on askubuntu.com]("https://askubuntu.com/questions/983053/ubuntu-settings-say-no-bluetooth-found-even-though-i-have-a-device-connected-a"). Nothing there yet either.

---

