---
title: "bluetoothctl wont connect to device"
date: 2022-01-29
forum: Networking &amp; Wireless
---

### Post by buill on 2022-01-29
hi i can use bluetooth from gui and works fine but i need to launch from terminal so i run

bluetoothctl scan on
bluetoothctl discoverable on
bluetoothctl pair 98:B6:E9:5C:25:E4
bluetoothctl connect 98:B6:E9:5C:25:E4
bluetoothctl paired-devices
bluetoothctl devices
bluetoothctl trust 98:B6:E9:5C:25:E4

which ouputs

bluetoothctl scan on
bluetoothctl discoverable on
bluetoothctl pair 98:B6:E9:5C:25:E4
bluetoothctl connect 98:B6:E9:5C:25:E4
bluetoothctl paired-devices
bluetoothctl devices
bluetoothctl trust 98:B6:E9:5C:25:E4
Discovery started
[CHG] Controller 9C:B7:0D:AB:58:0D Discovering: yes
[NEW] Device 98:B6:E9:5C:25:E4 Wireless Controller   //stays here and does not connect
[DEL] Device 98:B6:E9:5C:25:E4 Wireless Controller   //this is when the controller sync times out and turns off

any help would be great thanks

---

### Post by buill on 2022-01-29
k so if i dissconnect and remove controller with

bluetoothctl disconnect 98:B6:E9:5C:25:E4
bluetoothctl remove 98:B6:E9:5C:25:E4

i can then scan for device with 

bluetoothctl scan on

but the scan never ends but once device is detected i can open another terminal window and connect with

bluetoothctl connect 98:B6:E9:5C:25:E4

and killall mate-terminal and it stays connected its messy but it works however if anyone knows a better way would love to know i would prefare if once a know mac is found it connects

---

