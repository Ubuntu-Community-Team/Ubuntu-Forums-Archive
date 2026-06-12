---
title: "Very Strange Bluetooth Bug, hciconfig hci0 up says &gt; &quot;Device Switched Into Off Mode&quot;"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by neuralzen on 2007-08-08
I have bluez-utils, bluez-gnome, and pretty much all the obex and other bluez stuff installed but cannot get my bluetooth to turn on.

When I issue the console command "sudo hciconfig hci0 up" the Bluetooth Applet 0.6 icon in the upper right makes a bubble popup that says "Switched Device into Off Mode". I have no idea what to do; I have tried uninstalling (complete) and reinstalling all of the bluetooth, bluez, and obex packages and checking out the hcid.conf file and bluetooth config file, but nothing has helped. Here is the output for hciconfig -a hci0

```
nz@computer:~$ sudo hciconfig -a hci0
hci0:   Type: USB
        BD Address: 00:0A:94:02:12:15 ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING
        RX bytes:3790 acl:13 sco:0 events:175 errors:0
        TX bytes:2242 acl:13 sco:0 commands:121 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'aeon-0'
        Class: 0x3e0104
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Desktop workstation
        HCI Ver: 1.1 (0x1) HCI Rev: 0x7a6 LMP Ver: 1.1 (0x1) LMP Subver: 0x7a6
        Manufacturer: Cambridge Silicon Radio (10)
```

Any help on this issue would invaluable as this have plagued me for a long time. Oh, and I can send files FROM my computer to my phone, but my phone does not detect th presence of the computer.  Thanks for your time and thought!

  -NZ

---

### Post by ruibernardo on 2007-08-09
Hi neuralzen,

to make your computer discoverable (visible) you have to do the following  in a terminal (with Gnome):

```
 dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable
```Hope that helps.

---

### Post by neuralzen on 2007-08-09
You deserve a medal. Thank you so very ineffably much!! I owe you one!

  -NZ

---

### Post by anindya_m on 2008-02-11
Just for the record
```
hciconfig hci0 piscan
```
should also enable visibility. Here hci0 is the bluetooth adapter.

---

