---
title: "Kubuntu bluetooth issue | Dell 3543 | Broadcom 802.11bgn bcm43142"
date: 2022-11-14
forum: Networking &amp; Wireless
---

### Post by ysrana05 on 2022-11-14
So, I am using Kubuntu for quite some time. Everything is perfect except the bluetooth. At first, the bluetooth was not working so I did some research and installed the driver BCM43142A0-0a5c-21d7.hcd manually and placed it in location /lib/firmware/brcm/ and rebooted.
After that, it detects the bluetooth device and connects too but the issue is with the audio. It is not working properly and have some hicupps while playing the audio/video file. The audio does some grrrrrrr sound and then again works normally. The audio-video is also not in sync properly.
I've looked for all the solutions available on the internet but still not able to resolve the issue. So at last, I decided to post here about the issue. Hope any of you guys help me to solve the issue.


Here are the other details:
Operating System: Kubuntu 22.04
KDE Plasma Version: 5.24.4
KDE Frameworks Version: 5.92.0
Qt Version: 5.15.3
Kernel Version: 5.15.0-41-generic (64-bit)
Graphics Platform: X11
Processors: 4 × Intel® Core&#8482; i3-5005U CPU @ 2.00GHz
Memory: 7.7 GiB of RAM
Graphics Processor: Mesa Intel® HD Graphics 5500
-------------------------------------------------------------------------
"lsusb" command result:
```
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 004: ID 0c45:670b Microdia Integrated_Webcam_HD
Bus 001 Device 008: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:8001 Intel Corp. Integrated Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
------------------------------------------------------------------------------
"sudo dmesg | grep -i bluetooth"     command result:
```
[    5.762975] Bluetooth: Core ver 2.22
[    5.763867] NET: Registered PF_BLUETOOTH protocol family
[    5.763870] Bluetooth: HCI device and connection manager initialized
[    5.763876] Bluetooth: HCI socket layer initialized
[    5.763880] Bluetooth: L2CAP socket layer initialized
[    5.763889] Bluetooth: SCO socket layer initialized
[    5.980781] Bluetooth: hci0: BCM: chip id 70
[    5.981790] Bluetooth: hci0: BCM: features 0x06
[    5.997796] Bluetooth: hci0: BCM43142A
[    5.997806] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[    6.011123] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0a5c-21d7.hcd' Patch
[    6.803818] Bluetooth: hci0: BCM43142A0 Generic USB Class 2 NonUHE @ 20 MHz
[    6.803828] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0341
[    7.067838] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.067845] Bluetooth: BNEP filters: protocol multicast
[    7.067851] Bluetooth: BNEP socket layer initialized
[    9.705167] Bluetooth: RFCOMM TTY layer initialized
[    9.705183] Bluetooth: RFCOMM socket layer initialized
[    9.705192] Bluetooth: RFCOMM ver 1.11
```




--------------------------------------------------------------------------


"sudo systemctl status bluetooth.service " command result:
```
bluetooth.service - Bluetooth service
    Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2022-07-25 11:40:18 IST; 1h 54min ago
      Docs: man:bluetoothd(8)
  Main PID: 788 (bluetoothd)
    Status: "Running"
     Tasks: 1 (limit: 9307)
    Memory: 2.1M
       CPU: 244ms
    CGroup: /system.slice/bluetooth.service
            &#9492;&#9472;788 /usr/lib/bluetooth/bluetoothd
Jul 25 11:40:31 Revo bluetoothd[788]: Failed to set mode: Blocked through rfkill (0x12)
Jul 25 11:41:00 Revo bluetoothd[788]: src/service.c:btd_service_connect() a2dp-source profile connect failed for F4:4E:FD:28:34:D0: Device or resource busy
Jul 25 11:41:03 Revo bluetoothd[788]: /org/bluez/hci0/dev_F4_4E_FD_28_34_D0/sep1/fd0: fd(42) ready
Jul 25 11:41:12 Revo bluetoothd[788]: src/service.c:btd_service_connect() a2dp-source profile connect failed for F4:4E:FD:28:34:D0: Device or resource busy
Jul 25 11:41:15 Revo bluetoothd[788]: /org/bluez/hci0/dev_F4_4E_FD_28_34_D0/sep1/fd1: fd(42) ready
Jul 25 11:42:30 Revo bluetoothd[788]: src/profile.c:ext_io_disconnected() Unable to get io data for Hands-Free Voice gateway: getpeername: Transport endpoint is not c>
Jul 25 11:42:34 Revo bluetoothd[788]: profiles/audio/avctp.c:avctp_control_confirm() Control: Refusing unexpected connect
Jul 25 11:42:36 Revo bluetoothd[788]: /org/bluez/hci0/dev_F4_4E_FD_28_34_D0/sep1/fd2: fd(42) ready
Jul 25 11:49:05 Revo bluetoothd[788]: src/service.c:btd_service_connect() a2dp-source profile connect failed for F4:4E:FD:28:34:D0: Device or resource busy
Jul 25 11:49:07 Revo bluetoothd[788]: /org/bluez/hci0/dev_F4_4E_FD_28_34_D0/sep1/fd3: fd(42) ready
------------------------------------------------------------------------------------
```

---

### Post by larhan on 2022-11-16
sudo apt-get update


Install broadcom-sta-dkms:
sudo apt-get install broadcom-sta-dkms

---

