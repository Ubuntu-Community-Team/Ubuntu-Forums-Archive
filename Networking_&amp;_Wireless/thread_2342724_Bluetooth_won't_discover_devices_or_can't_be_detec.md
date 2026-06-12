---
title: "Bluetooth won't discover devices or can't be detected by other devices."
date: 2016-11-09
forum: Networking &amp; Wireless
---

### Post by timmymorr on 2016-11-09
Hi all,

I have a HP 250 G4 laptop that I am running Ubuntu 16.04 64 alongside Windows 10 in a dual boot. My laptop has a Broadcom B43142 wireless card for Wi-Fi and Bluetooth. My Wi-Fi works fine but my Bluetooth can't ping or discover any devices and it can't be pinged or discovered by other devices. 
Here is the output of hciconfig:
```

hci0:    Type: BR/EDR  Bus: USB
    BD Address: 60:6D:C7:F8:7E:4A  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:980 acl:0 sco:0 events:54 errors:0
    TX bytes:2521 acl:0 sco:0 commands:54 errors:0

rfkill list:

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
15: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

dmesg | grep Blue:

[44494.816632] Bluetooth: hci0 command 0x1001 tx timeout
[44502.811965] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[44504.815715] Bluetooth: hci0 command 0x1001 tx timeout
[44512.814965] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[46144.153400] Bluetooth: hci0: BCM: chip id 70
[46144.169400] Bluetooth: hci0: BCM43142A
[46144.169405] Bluetooth: hci0: BCM (001.001.011) build 0000
[46145.744117] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[46147.746780] Bluetooth: hci0 command 0x1003 tx timeout
[52975.867893] Bluetooth: hci0: BCM: chip id 70
[52975.883904] Bluetooth: hci0: BCM43142A
[52975.883909] Bluetooth: hci0: BCM (001.001.011) build 0000
[52975.887027] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[52977.889767] Bluetooth: hci0 command 0x1003 tx timeout
```

I have read a lot of issues with drivers but I have not seen the same error as mine so any help would be greatly appreciated.

Thanks

---

