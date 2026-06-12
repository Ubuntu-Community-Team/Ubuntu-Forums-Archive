---
title: "Realtek rtl8821ce bluetooth problem"
date: 2024-03-04
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2024-03-04
I have an AMD PC with a Realtek rtl8821ce wifi/bluetooth chip on the mobo, running Kubuntu 23.10 with kernel 6.7.1-060701-generic. This kernel supports the rtl8821ce chip, and wifi works but bluetooth does not work. Below is the systemctl status for the bluetooth device, including error messages, which messages show up in dmesg as well.

$ sudo systemctl status dbus-org.bluez.service
&#9675; bluetooth.service - Bluetooth service
     Loaded: error (Reason: Unit bluetooth.service failed to load properly, please adjust/correct and reload service manager: File exists)
     Active: inactive (dead)
       Docs: man:bluetoothd(8)
systemd[1]: bluetooth.service: Two services allocated for the same bus name org.bluez, refusing operation.
systemd[1]: bluetooth.service: Cannot add dependency job, ignoring: File exists

I'm including below outputs from other commands for information, and would appreciate recommendations to diagnose and/or fix.

Thx, Gus
-------------------------------------------------------------
$ lshw ..............

 *-usb:3
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 8
                      bus info: usb@1:8
                      version: 1.10
                      serial: 00e04c000001
                      capabilities: bluetooth usb-1.10
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s

$ lsmod | grep bt 
btusb                  77824  0
btrtl                  36864  1 btusb
btintel                57344  1 btusb
btbcm                  24576  1 btusb
btmtk                  16384  1 btusb
bluetooth            1085440  6 btrtl,btmtk,btintel,btbcm,btusb
$ lsmod | grep blu
bluetooth            1085440  6 btrtl,btmtk,btintel,btbcm,btusb
ecdh_generic           16384  1 bluetooth
$ lsmod btlog.txt
| grep 8821
8821ce               2514944  0
cfg80211             1327104  1 8821ce

---

