---
title: "Bluetooth doesn't connect"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by Strikeiron on 2014-03-16
Hello,
I've recently updated to saucy salamander but neither with ringtail bluetooth it did work. I have a smartphone and the computer is able to see it (by command in terminal) but there's no connection and I can't send files between computer and phone or viceversa.
I've got a Lenovo, with kernel 3.11.0-19-generic.
Here you are the results of certain commands:

[PHP]lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:029c Acer, Inc 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07da Intel Corp. 
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/PHP]

[PHP]root@samuele-Lenovo-IdeaPad-S400u:/home/samuele# dmesg | grep Blue
[   15.483211] Bluetooth: Core ver 2.16
[   15.483233] Bluetooth: HCI device and connection manager initialized
[   15.483240] Bluetooth: HCI socket layer initialized
[   15.483244] Bluetooth: L2CAP socket layer initialized
[   15.483248] Bluetooth: SCO socket layer initialized
[   23.838254] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.838258] Bluetooth: BNEP filters: protocol multicast
[   23.838267] Bluetooth: BNEP socket layer initialized
[   23.850696] Bluetooth: RFCOMM TTY layer initialized
[   23.850721] Bluetooth: RFCOMM socket layer initialized
[   23.850726] Bluetooth: RFCOMM ver 1.11
[/PHP]

[PHP]root@samuele-Lenovo-IdeaPad-S400u:/home/samuele# hciconfig -a
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 60:36:DD:85:4E:76  ACL MTU: 310:10  SCO MTU: 64:8
    UP RUNNING PSCAN ISCAN 
    RX bytes:25800 acl:0 sco:0 events:741 errors:0
    TX bytes:4256 acl:0 sco:0 commands:267 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0xdb 0xff 0x5b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'ubuntu-0'
    Class: 0x6e0100
    Service Classes: Networking, Rendering, Capturing, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 4.0 (0x6)  Revision: 0x1ebd
    LMP Version: 4.0 (0x6)  Subversion: 0xfc00
    Manufacturer: Intel Corp. (2)
[/PHP]

[PHP]root@samuele-Lenovo-IdeaPad-S400u:/home/samuele# hcitool scan
Scanning ...
    E6:68:46:56:78:5E    NGM Polaris
root@samuele-Lenovo-IdeaPad-S400u:/home/samuele# 

[/PHP]

Any idea there?
Thanks in advance 
(Ps I've got the same problem with an old Xubuntu.. so I'm trying to solve the problem for both...).
Bye

---

### Post by Strikeiron on 2014-03-17
I suppose that part of the problem lies here:

> root@samuele-Lenovo-IdeaPad-S400u:/etc/default# dmesg | grep Blue[   14.158985] Bluetooth: Core ver 2.16
[   14.159009] Bluetooth: HCI device and connection manager initialized
[   14.159017] Bluetooth: HCI socket layer initialized
[   14.159021] Bluetooth: L2CAP socket layer initialized
[   14.159028] Bluetooth: SCO socket layer initialized
[   36.618747] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.618752] Bluetooth: BNEP filters: protocol multicast
[   36.618763] Bluetooth: BNEP socket layer initialized
[   36.623337] Bluetooth: RFCOMM TTY layer initialized
[   36.623352] Bluetooth: RFCOMM socket layer initialized
[   36.623354] Bluetooth: RFCOMM ver 1.11
[ 2270.896564] Bluetooth: Failed to start inquiry: status 12
[ 2276.022917] Bluetooth: Failed to start inquiry: status 12
[ 7960.229124] Bluetooth: Failed to start inquiry: status 12
[ 7965.367419] Bluetooth: Failed to start inquiry: status 12
[ 7970.498793] Bluetooth: Failed to start inquiry: status 12
root@samuele-Lenovo-IdeaPad-S400u:/etc/default# 


---

### Post by Strikeiron on 2014-03-17
I've been looking for the problem in internet, but no solution anywhere. Is it possible that on linux bluetooth doesn't work? It' s a pity!

---

### Post by Strikeiron on 2014-03-18
Thanks in advance in case anybody would give me some advice.

---

### Post by Strikeiron on 2014-03-24
I suppose here everybody uses bluetooth with her computer and It works! :)

---

### Post by Strikeiron on 2014-03-24
Well in case... the bluetooth pairing is done through python and when it doesn't work here it is the error message...

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "<string>", line 2, in CreateDevice
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/DBusService.py", line 141, in CreateDevice
    agent = TempAgent(self.Applet.Plugins.StatusIcon, agent_path, time)
  File "/usr/lib/python2.7/dist-packages/blueman/main/applet/BluezAgent.py", line 255, in __init__
    CommonAgent.__init__(self, status_icon, path)
  File "/usr/lib/python2.7/dist-packages/blueman/main/applet/BluezAgent.py", line 52, in __init__
    Agent.__init__(self, path)
  File "/usr/lib/python2.7/dist-packages/blueman/bluez/Agent.py", line 68, in __init__
    dbus.service.Object.__init__(self, dbus.SystemBus(), obj_path)
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 485, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 576, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/blueman/agent/temp/E6684656785E': there is already a handler"



Anybody could help?

---

