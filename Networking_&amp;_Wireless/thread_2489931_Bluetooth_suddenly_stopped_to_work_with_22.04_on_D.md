---
title: "Bluetooth suddenly stopped to work with 22.04 on Dell XPS 13 9310"
date: 2023-08-15
forum: Networking &amp; Wireless
---

### Post by nils-vldj on 2023-08-15
I've been using Ubuntu for more than one year without any problem. [But now I'm facing two !]("https://ubuntuforums.org/showthread.php?t=2489932") I was able to normally turn ON/OFF my bluetooth and to connect my computer to any device. But now, if the bluetooth parameter is still available, there is no way I can turn it ON. The switcher switcher, but does not turn orange and the bluetooth stays OFF.
I tried to boot on a flas drive with Ubuntu on it, the problem was the same : the bluetooth did not work (but I didn't face any sleep mode-wake up issue).
I do not understand, since my bluetooth used to work until now...
What can I do to get it back working ?
Thanks in advance for your help, nils This is what I tried without any good result : (My bluetooth device is ON in the BIOS menu)

```
nils@nilsXPS13:~$ rfkill list
0: hci0: Bluetooth Soft blocked: no Hard blocked: no 1: phy0: Wireless LAN Soft blocked: no Hard blocked: no
```

```
nils@nilsXPS13:~$ hcitool dev
Devices:
```

```
nils@nilsXPS13:~$ hcitool inq
Inquiring ... Inquiry failed.: No such device
```
```
nils@nilsXPS13:~$ sudo rfkill unblock bluetooth && rfkill list bluetooth
[sudo] Mot de passe de nils : 0: hci0: Bluetooth Soft blocked: no Hard blocked: no
```
```
nils@nilsXPS13:~$ sudo hciconfig hci0 piscan
Can't set scan mode on hci0: Network is down (100)
```
```
nils@nilsXPS13:~$ sudo service network-manager restart
Failed to restart network-manager.service: Unit network-manager.service not found.
```
```
nils@nilsXPS13:~$ sudo systemctl restart systemd-networkd
```

```
nils@nilsXPS13:~$ sudo reboot
```

---

### Post by nils-vldj on 2023-08-15
And here some others pieces of information :

```
nils@NilsXPS13:~$ uname -a; lspci -nnk | grep -iA3 net; lsusb; sudo dmesg | grep -i bluetooth; sudo dmesg | grep -i firmware; lsmod | grep bluetooth
Linux NilsXPS13 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
00:14.3 Network controller [0280]: Intel Corporation Wi-Fi 6 AX201 [8086:a0f0] (rev 20)
    Subsystem: Rivet Networks Wi-Fi 6 AX201 [1a56:1651]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
00:15.0 Serial bus controller [0c80]: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 [8086:a0e8] (rev 20)
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 009: ID 2109:8817 VIA Labs, Inc. USB Billboard Device   
Bus 003 Device 008: ID 03f0:134a HP, Inc Optical Mouse
Bus 003 Device 007: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 2109:2817 VIA Labs, Inc. USB2.0 Hub             
Bus 003 Device 003: ID 0c45:672a Microdia Integrated_Webcam_HD
Bus 003 Device 002: ID 27c6:533c Shenzhen Goodix Technology Co.,Ltd. FingerPrint
Bus 003 Device 004: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
Bus 002 Device 002: ID 2109:0817 VIA Labs, Inc. USB3.0 Hub             
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[sudo] Mot de passe de nils : 
[   14.304688] Bluetooth: Core ver 2.22
[   14.304707] NET: Registered PF_BLUETOOTH protocol family
[   14.304708] Bluetooth: HCI device and connection manager initialized
[   14.304712] Bluetooth: HCI socket layer initialized
[   14.304714] Bluetooth: L2CAP socket layer initialized
[   14.304719] Bluetooth: SCO socket layer initialized
[   14.458728] Bluetooth: hci0: Bootloader revision 0.4 build 0 week 30 2018
[   14.459801] Bluetooth: hci0: Device revision is 2
[   14.459804] Bluetooth: hci0: Secure boot is enabled
[   14.459805] Bluetooth: hci0: OTP lock is enabled
[   14.459806] Bluetooth: hci0: API lock is enabled
[   14.459806] Bluetooth: hci0: Debug lock is disabled
[   14.459807] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   14.465144] Bluetooth: hci0: Found device firmware: intel/ibt-19-0-4.sfi
[   14.465205] Bluetooth: hci0: Boot Address: 0x24800
[   14.465207] Bluetooth: hci0: Firmware Version: 126-5.22
[   15.084176] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.084180] Bluetooth: BNEP filters: protocol multicast
[   15.084184] Bluetooth: BNEP socket layer initialized
[   16.319980] Bluetooth: hci0: Waiting for firmware download to complete
[   16.320709] Bluetooth: hci0: Firmware loaded in 1812068 usecs
[   16.320760] Bluetooth: hci0: Waiting for device to boot
[   17.329938] Bluetooth: hci0: Device boot timeout
[   17.329975] Bluetooth: hci0: Intel reset sent to retry FW download
[   19.505944] Bluetooth: hci0: Failed to read MSFT supported features (-110)
[   19.505970] Bluetooth: hci0: command 0xfc1e tx timeout
[    1.561309] i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/tgl_dmc_ver2_12.bin (v2.12)
[   14.353516] iwlwifi 0000:00:14.3: loaded firmware version 72.daa05125.0 QuZ-a0-hr-b0-72.ucode op_mode iwlmvm
[   14.459807] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   14.465144] Bluetooth: hci0: Found device firmware: intel/ibt-19-0-4.sfi
[   14.465207] Bluetooth: hci0: Firmware Version: 126-5.22
[   14.809723] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:0:0-b678a
[   14.809726] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:20:0 Kernel ABI 3:23:0
[   14.904988] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:0:0-b678a
[   14.904994] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:20:0 Kernel ABI 3:23:0
[   16.319980] Bluetooth: hci0: Waiting for firmware download to complete
[   16.320709] Bluetooth: hci0: Firmware loaded in 1812068 usecs
bluetooth            1036288  13 btrtl,btmtk,btintel,btbcm,bnep,btusb
ecdh_generic           16384  1 bluetooth
```

```
nils@NilsXPS13:~$ dpkg -l | grep blue
ii  bluez                                      5.64-0ubuntu1                                   amd64        Bluetooth tools and daemons
ii  bluez-cups                                 5.64-0ubuntu1                                   amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                5.64-0ubuntu1                                   amd64        bluez obex daemon
ii  gir1.2-gnomebluetooth-3.0:amd64            42.0-5                                          amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth                            3.34.5-8                                        amd64        GNOME Bluetooth Send To app
ii  gnome-bluetooth-3-common                   42.0-5                                          all          GNOME Bluetooth 3 common files
ii  gnome-bluetooth-common                     3.34.5-8                                        all          GNOME Bluetooth common files
ii  libbluetooth3:amd64                        5.64-0ubuntu1                                   amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth-3.0-13:amd64            42.0-5                                          amd64        GNOME Bluetooth 3 support library
ii  libgnome-bluetooth13:amd64                 3.34.5-8                                        amd64        GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth                1:15.99.1+dfsg1-1ubuntu2.1                      amd64        Bluetooth module for PulseAudio sound server
```

```
nils@NilsXPS13:~$ sudo service bluetooth status | cat
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-08-15 09:02:16 CEST; 3h 53min ago
       Docs: man:bluetoothd(8)
   Main PID: 948 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18674)
     Memory: 1.8M
        CPU: 94ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;948 /usr/lib/bluetooth/bluetoothd

août 15 09:02:15 NilsXPS13 systemd[1]: Starting Bluetooth service...
août 15 09:02:16 NilsXPS13 bluetoothd[948]: Bluetooth daemon 5.64
août 15 09:02:16 NilsXPS13 systemd[1]: Started Bluetooth service.
août 15 09:02:16 NilsXPS13 bluetoothd[948]: Starting SDP server
août 15 09:02:16 NilsXPS13 bluetoothd[948]: Bluetooth management interface 1.22 initialized
```

---

### Post by grayverk on 2023-09-11
I had the same issue on Ubuntu 20.04. Bluetooth just unexpectedly stopped working after the reboot. Then I realized that Ubuntu silently installed some updates (and kernel update among them). So, I just booted from previous kernel version and Bluetooth is working again. So, it seems that it's a recent kernel issue.

---

