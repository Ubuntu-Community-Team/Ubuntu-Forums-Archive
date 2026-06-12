---
title: "Bluetooth not working"
date: 2019-04-22
forum: Networking &amp; Wireless
---

### Post by valeriosoldout on 2019-04-22
Hi everybody, couldn't get my bluetooth working in Lubuntu 19.04
here's the service bluetooth status printout: Bluetooth wizard and Bluetooth manager cannot find any adapter, unless the previous version of Lubuntu was working properly at least after a "service bluetooth restart" command in the shell.
Could you kindly help me out with this issue?
Thanks

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre
   Active: active (running) since Mon 2019-04-22 15:57:09 CEST; 15min ago
     Docs: man:bluetoothd(8)
 Main PID: 1633 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4535)
   Memory: 1.4M
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1633 /usr/lib/bluetooth/bluetoothd

apr 22 15:57:08 valerio-pc systemd[1]: Starting Bluetooth service...
apr 22 15:57:09 valerio-pc bluetoothd[1633]: Bluetooth daemon 5.50
apr 22 15:57:09 valerio-pc systemd[1]: Started Bluetooth service.
apr 22 15:57:09 valerio-pc bluetoothd[1633]: Starting SDP server
apr 22 15:57:10 valerio-pc bluetoothd[1633]: Bluetooth management interface

---

### Post by praseodym on 2019-04-22
Please show the outputs of these commands
```

lspci -nnk
lsusb
usb-devices
hciconfig --all
lsmod
dmesg | grep blue
```

---

