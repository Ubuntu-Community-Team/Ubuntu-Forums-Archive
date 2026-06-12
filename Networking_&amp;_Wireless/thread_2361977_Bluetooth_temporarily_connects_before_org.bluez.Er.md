---
title: "Bluetooth temporarily connects before org.bluez.Error.NotAvailable"
date: 2017-05-22
forum: Networking &amp; Wireless
---

### Post by treeofeden on 2017-05-22
I have been trying to connect my laptop with Ubuntu 17.04 to a raspberry pi with Debian. It pairs with the pi, however when I connect it, it immediately gives the error org.bluez.Error.NotAvailable, and then loses connection within seconds. The code that I have used is below.
```
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# agent KeyboardOnly
Agent registered
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# agent on
Agent is already registered
[bluetooth]# scan on
Discovery started
[CHG] Controller 64:5A:04:83:E0:E5 Discovering: yes
[NEW] Device B8:27:EB:5C:13:9C raspberrypi
[bluetooth]# trust B8:27:EB:5C:13:9C
[CHG] Device B8:27:EB:5C:13:9C Trusted: yes
Changing B8:27:EB:5C:13:9C trust succeeded
[CHG] Device B8:27:EB:5C:13:9C RSSI: -60
[bluetooth]# pair B8:27:EB:5C:13:9C 
Attempting to pair with B8:27:EB:5C:13:9C
[CHG] Device B8:27:EB:5C:13:9C Connected: yes
[CHG] Device B8:27:EB:5C:13:9C UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device B8:27:EB:5C:13:9C UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device B8:27:EB:5C:13:9C UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Device B8:27:EB:5C:13:9C UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device B8:27:EB:5C:13:9C UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device B8:27:EB:5C:13:9C ServicesResolved: yes
[CHG] Device B8:27:EB:5C:13:9C Paired: yes
Pairing successful
[CHG] Device B8:27:EB:5C:13:9C ServicesResolved: no
[CHG] Device B8:27:EB:5C:13:9C Connected: no
[bluetooth]# connect B8:27:EB:5C:13:9C
Attempting to connect to B8:27:EB:5C:13:9C
[CHG] Device B8:27:EB:5C:13:9C Connected: yes
[CHG] Device B8:27:EB:5C:13:9C ServicesResolved: yes
Failed to connect: org.bluez.Error.NotAvailable
[CHG] Device B8:27:EB:5C:13:9C ServicesResolved: no
[CHG] Device B8:27:EB:5C:13:9C Connected: no

```

---

### Post by Jason_Hunter on 2017-05-24
what does dmesg -T say after you try this?

---

