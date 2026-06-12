---
title: "Can't pair bluetooth headphones"
date: 2019-03-23
forum: Networking &amp; Wireless
---

### Post by mirz2 on 2019-03-23
I have Asus PCE-AC55BT wifi + bluetooth adapter. It works fine in Windows but I can't make it work on Linux. I'm trying to pair Bluedio F headphones.

Help me figure this out.

```
$ dmesg | grep Blue
[    2.966351] Bluetooth: Core ver 2.22
[    2.966363] Bluetooth: HCI device and connection manager initialized
[    2.966365] Bluetooth: HCI socket layer initialized
[    2.966368] Bluetooth: L2CAP socket layer initialized
[    2.966371] Bluetooth: SCO socket layer initialized
[    2.976160] Bluetooth: hci0: Firmware revision 0.0 build 16 week 50 2018
[    3.924023] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.924024] Bluetooth: BNEP filters: protocol multicast
[    3.924026] Bluetooth: BNEP socket layer initialized
[   19.510895] Bluetooth: RFCOMM TTY layer initialized
[   19.510899] Bluetooth: RFCOMM socket layer initialized
[   19.510903] Bluetooth: RFCOMM ver 1.11
```

```
$ lspci                                                                                                                                                                                                 
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)                                                                                                                                       
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)                                                                                                             
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)                                                                                          
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)                                                                                                                  
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation B85 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP106 High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
06:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
```

```
$ uname -a
Linux mirz-desktop 4.18.0-16-generic #17~18.04.1-Ubuntu SMP Tue Feb 12 13:35:51 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-03-23 22:12:15 CET; 16min ago
     Docs: man:bluetoothd(8)
 Main PID: 801 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;801 /usr/lib/bluetooth/bluetoothd

mar 23 22:12:15 mirz-desktop systemd[1]: Starting Bluetooth service...
mar 23 22:12:15 mirz-desktop bluetoothd[801]: Bluetooth daemon 5.50
mar 23 22:12:15 mirz-desktop bluetoothd[801]: Starting SDP server
mar 23 22:12:15 mirz-desktop bluetoothd[801]: Version mismatch for sixaxis
mar 23 22:12:15 mirz-desktop bluetoothd[801]: Bluetooth management interface 1.14 initialized
mar 23 22:12:15 mirz-desktop systemd[1]: Started Bluetooth service.
mar 23 22:15:30 mirz-desktop bluetoothd[801]: a2dp-sink profile connect failed for 18:07:20:31:0C:66: Protocol not available
mar 23 22:15:55 mirz-desktop bluetoothd[801]: a2dp-sink profile connect failed for 18:07:20:31:0C:66: Protocol not available
mar 23 22:16:12 mirzz-desktop bluetoothd[801]: a2dp-sink profile connect failed for 18:07:20:31:0C:66: Protocol not available
```

```
$ bluetoothctl 
Agent registered
[bluetooth]# power on 
Changing power on succeeded
[bluetooth]# agent on
Agent is already registered
[bluetooth]# scan on
Discovery started
[CHG] Controller 00:BB:60:48:AC:B9 Discovering: yes
[NEW] Device 41:91:EB:0B:30:86 41-91-EB-0B-30-86
[bluetooth]# devices
Device 18:07:20:31:0C:66 Bluedio F
Device 41:91:EB:0B:30:86 41-91-EB-0B-30-86
[bluetooth]# pair 18:07:20:31:0C:66 
Attempting to pair with 18:07:20:31:0C:66
[CHG] Device 18:07:20:31:0C:66 Connected: yes
[CHG] Device 18:07:20:31:0C:66 Paired: yes
Pairing successful
[CHG] Device 18:07:20:31:0C:66 Connected: no
[bluetooth]# info 18:07:20:31:0C:66 
Device 18:07:20:31:0C:66 (public)
        Name: Bluedio F
        Alias: Bluedio F
        Class: 0x00240404
        Icon: audio-card
        Paired: yes
        Trusted: yes
        Blocked: no
        Connected: no
        LegacyPairing: no
        UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
[CHG] Device 18:07:20:31:0C:66 RSSI: -56
[bluetooth]# connect 18:07:20:31:0C:66 
Attempting to connect to 18:07:20:31:0C:66
Failed to connect: org.bluez.Error.Failed

```

```
$ dpkg -l | grep blue
ii  bluedevil                                       4:5.12.7-0ubuntu0.1                         amd64        KDE Bluetooth stack
ii  blueman                                         2.0.5-1ubuntu1                              amd64        Graphical bluetooth manager
ii  bluetooth                                       5.50-0ubuntu0ppa1                           all          Bluetooth support
ii  bluez                                           5.50-0ubuntu0ppa1                           amd64        Bluetooth tools and daemons
ii  bluez-cups                                      5.50-0ubuntu0ppa1                           amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                     5.50-0ubuntu0ppa1                           amd64        bluez obex daemon
ii  bluez-tools                                     0.2.0~20140808-5build1                      amd64        Set of tools to manage Bluetooth devices for linux
ii  libbluetooth3:amd64                             5.48-0ubuntu3.1                             amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libkf5bluezqt-data                              5.44.0-0ubuntu1                             all          data files for bluez-qt
ii  libkf5bluezqt6:amd64                            5.44.0-0ubuntu1                             amd64        Qt wrapper for bluez
ii  pulseaudio-module-bluetooth                     1:11.1-1ubuntu7.2                           amd64        Bluetooth module for PulseAudio sound server
ii  qml-module-org-kde-bluezqt:amd64                5.44.0-0ubuntu1                             amd64        QML wrapper for bluez
```

---

