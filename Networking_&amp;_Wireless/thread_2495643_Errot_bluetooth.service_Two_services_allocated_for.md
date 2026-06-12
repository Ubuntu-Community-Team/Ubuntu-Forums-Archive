---
title: "Errot: bluetooth.service: Two services allocated for the same bus name org.bluez"
date: 2024-02-25
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2024-02-25
I have Kubuntu 23.10 with 6.5.0-21-generic kernel, running on a Gigabyte AC520I AC Wifi mobo. This board has a Realtek rtl8821ce PCIe wifi/bluetooth chip, which is supposed to work on linux, using a DKMS install module downloaded from github.com/tomaspinho/rtl8821ce. But, given that I have little experience using DKMS, I couldn't get either wifi or bluetooth working.

So I bought and installed an Intel AX210ngw Desktop PC PCIe Wifi/Bluetooth Network Adapter, which is supposed to work with Linux/23.10. With that, wifi worked out of the box, and I installed bluedevil, blueman, bluemon and bluez, but I can't get Bluetooth working.

There's some diagnostic outputs below, one of which might suggest that the problem is in having two wifi/bruetooth adapters, but I'm unable to disable the onboard Realtek chip either in the BIOS or the OS. I'd appreciate recommendations for further diagnosis and/or how to fix this.

Thx, Gus

Here's some related information:

$ sudo systemctl enable --now bluetooth.service
Synchronizing state of bluetooth.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable bluetooth
Failed to start bluetooth.service: Unit bluetooth.service failed to load properly, please adjust/correct and reload service manager: File exists
See system logs and 'systemctl status bluetooth.service' for details.

$ sudo systemctl status bluetooth.service
&#9675; bluetooth.service - Bluetooth service
     Loaded: error (Reason: Unit bluetooth.service failed to load properly, please adjust/correct and reload service manager: File exists)
     Active: inactive (dead)
       Docs: man:bluetoothd(8)

Feb 24 10:51:49 Gigabyte systemd[1]: bluetooth.service: Two services allocated for the same bus name org.bluez, refusing operation.

$ sudo dmesg ........
.
[  507.329499] Bluetooth: Core ver 2.22
[  507.329523] NET: Registered PF_BLUETOOTH protocol family
[  507.329525] Bluetooth: HCI device and connection manager initialized
[  507.329529] Bluetooth: HCI socket layer initialized
[  507.329532] Bluetooth: L2CAP socket layer initialized
[  507.329538] Bluetooth: SCO socket layer initialized

$ ps -ef | grep blue
2380    1390  0 10:51 ?        00:00:00 /usr/bin/python3 /usr/bin/blueman-applet
2537    1390  0 10:51 ?        00:00:00 /usr/lib/bluetooth/obexd
kubuntu23.10

---

