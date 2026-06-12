---
title: "Ubuntu 19.04 bluetooth not working (OptiPlex 5060)"
date: 2019-09-17
forum: Networking &amp; Wireless
---

### Post by tianbuntu on 2019-09-17
[COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit][COLOR=#242729][FONT=inherit]I am using a Dell OptiPlex 5060 which is supposed to have an inbuilt bluetooth; Atheros Communications 0cf3:e009, however Ubuntu 19.04 is unable to detect it, unable the bluetooth settings it states "No Bluetooth Found. Plug in a dongle to use Bluetooth".
[/FONT][/COLOR][/FONT][/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit]Here are some useful outputs:[/FONT]
```
[FONT=inherit]lspci -knn | grep Net -A2; lsusb:[/FONT]
Bus 001 Device 004: ID 0bc2:ab26 Seagate RSS LLC Backup Plus Slim Portable Drive 1 TB
Bus 001 Device 003: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 001 Device 002: ID 17ef:600e Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
[FONT=inherit]rfkill list; dmesg | grep -i blue :[/FONT]
[ 9303.303950] audit: type=1107 audit(1568626728.176:55): pid=1016 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=16976 label="snap.mailspring.mailspring"
[ 9365.700889] audit: type=1107 audit(1568626790.576:57): pid=1016 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=17394 label="snap.whatsdesk.whatsdesk"
[ 9780.379121] audit: type=1107 audit(1568627205.252:63): pid=1016 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=18250 label="snap.whatsdesk.whatsdesk"
[ 9787.980691] audit: type=1107 audit(1568627212.856:64): pid=1016 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=18406 label="snap.whatsdesk.whatsdesk"
[ 9857.254783] audit: type=1107 audit(1568627282.128:65): pid=1016 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=18617 label="snap.whatsdesk.whatsdesh"
```[/FONT][/COLOR]

---

### Post by slickymaster on 2019-09-17
Thread moved to **Networking & Wireless** for a better fit

---

### Post by tianbuntu on 2019-10-03
I have recently bought a CSR8510 bluetooth adapter. Upon connecting it to my machine, the bluetooth settings now says "Bluetooth Turned Off, Turn on to connect devices and receive file transfers".
When I turn on the switch at the top which makes it green, the bluetooth still remains off.

Here are the new outputs:

```
lspci -knn | grep Net -A2; lsusb

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 001 Device 003: ID 17ef:600e Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````

rfkill list; dmesg | grep -i blue


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[   14.085740] Bluetooth: Core ver 2.22
[   14.085751] Bluetooth: HCI device and connection manager initialized
[   14.085753] Bluetooth: HCI socket layer initialized
[   14.085754] Bluetooth: L2CAP socket layer initialized
[   14.085755] Bluetooth: SCO socket layer initialized
[   25.178240] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.178243] Bluetooth: BNEP filters: protocol multicast
[   25.178250] Bluetooth: BNEP socket layer initialized
[  115.458160] audit: type=1107 audit(1570155813.454:57): pid=1114 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2202 label="snap.whatsdesk.whatsdesk" peer_pid=1116 peer_label="unconfined"
[  117.536839] audit: type=1107 audit(1570155815.530:64): pid=1114 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2218 label="snap.mailspring.mailspring" peer_pid=1116 peer_label="unconfined"
```
```

bluetoothctl
Agent registered
[bluetooth]# power on
No default controller available
```

---

### Post by tianbuntu on 2019-10-15
Managed to get the bluetooth working. One of my colleagues has a bluetooth adapter which looks exactly the same,  he bought it from the same online shop as me as well. He too could not get his adapter to work on his PC machine (in his case he could connect to his bluetooth earphones but could not hear any sound when he played a video/music). We just did a swap of our bluetooth adapters for the fun of it, and surprise surprise the bluetooth works for both of us right now!!

So I guess I'll mark this thread as solved. Life is a mystery.

---

