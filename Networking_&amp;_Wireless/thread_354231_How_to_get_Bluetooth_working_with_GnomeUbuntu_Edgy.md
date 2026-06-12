---
title: "How to get Bluetooth working with Gnome/Ubuntu Edgy"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by cdrom600 on 2007-02-05
I have a Zonet USB Bluetooth dongle which I'd like to use to connect to my mobile phone (Sony Ericsson Z520a).  I've followed the instructions at [this page]("https://help.ubuntu.com/community/BluetoothSetup").  I have the following packages installed:
bluetooth, bluez-cups, bluez-passkey-gnome, bluez-utils, bluez-pin, gnome-bluetooth, libbluetooth2, libbtctl4, libgnomebt0

lsusb shows the device:
```
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp.
```
hcitool dev shows the device:
```
Devices:
        hci0    00:02:72:CD:4D:59

```
However, hidd --search does not find any devices.  hcitool scan finds the phone, though:
```
Scanning ...
        00:16:20:92:F1:B6       Chris's Z520a
```

Using "hciconfig hci0 inqmode 0" as suggested on the aforementioned page does not help.
What's going on?  I want to be able to sync my phone with Evolution and transfer files to/from the phone; how can I do this?

I know that Debian etch has a bluetooth manager applet (or something like that); does Ubuntu have an equivalent?

Any help is appreciated.

Also, uname -r: 2.6.17-10-generic

---

### Post by bls9707 on 2007-02-07
1

---

### Post by bls9707 on 2007-02-07
1

---

### Post by bls9707 on 2007-02-07
1

---

### Post by bls9707 on 2007-02-07
1

---

### Post by bls9707 on 2007-02-07
1

---

### Post by bls9707 on 2007-02-07
You have to make sure that your phone is searching for bluetooth devices.  On my phone (samsung sgh-t619) I had to turn "my visibility" to on.

Then I inquired for remote devices

```
$ hcitool inq
Inquiring ...
        00:0A:21:72:E3:AD       clock offset: 0x25c6    class: 0x10210c
        00:AA:21:B0:2B:72       clock offset: 0x2ed2    class: 0x102104

```

One is my bluetooth dongle, and the other is my phone

Then I scanned for remote device names

```
$ hcitool scan
Scanning ...
        00:0A:21:72:E3:AD       SAMSUNG SGH-T619

```

Now I am trying to figure out why I can't use gnome-bluetooth-manager, or gnome-obex-server.

```
$ gnome-obex-server

** (gnome-obex-server:11429): WARNING **: OBEX server register error: -1

** (gnome-obex-server:11429): WARNING **: Unable to initialize OBEX source

** (gnome-obex-server:11429): WARNING **: Couldn't initialise OBEX listener

```

---

### Post by Possitron on 2007-02-18
I got the same error, but then I realized that server was already running (Bluetooth File Sharing utility was active in tray).

---

### Post by glabouni on 2007-02-23
here's a guide to sync evolution to a phone via bluetooth, not sure this has been tested with ericsson phone though:
[https://help.ubuntu.com/community/NokiaEvolutionBluetoothSyncing](https://help.ubuntu.com/community/NokiaEvolutionBluetoothSyncing)

---

### Post by cdrom600 on 2007-05-03
As an FYI, Feisty seems to have added the Bluetooth config applet that I had in Debian Etch.

---

