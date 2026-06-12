---
title: "USB Bluetooth DBT 120"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by damichi on 2007-02-26
HI I am trying to integrate my DBT 120 USB- Bluetooth Dongle by D-Link

I found:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

sudo /etc/init.d/bluez-utils restart didnt work so I tried 

/etc/init.d/bluetooth restart

and it did return

* Restarting Bluetooth services                                         [ ok ] 

the lsusb returned 
Bus 005 Device 016: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

but when I try hcitool dev it returns nothing even if I restart the bluetooth service again!

Any ideas?

THX A LOT

---

