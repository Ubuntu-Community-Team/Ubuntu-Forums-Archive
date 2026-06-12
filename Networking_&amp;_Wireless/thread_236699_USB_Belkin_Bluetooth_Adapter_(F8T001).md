---
title: "USB Belkin Bluetooth Adapter (F8T001)"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by fredmorcos on 2006-08-15
Hi,
I'm having problems with my usb bluetooth adapter, as the name of the topic says, it's a Belkin F8T001... It's not being detected... here are:

```
lsmod|grep blue
bluetooth              54084  5 rfcomm,l2cap,hci_usb
```

```
lsmod|grep usb
hci_usb                18004  0
bluetooth              54084  5 rfcomm,l2cap,hci_usb
usbcore               139076  5 bcm203x,hci_usb,ehci_hcd,uhci_hcd

```

```
dmesg|grep usb
[17179580.968000] usbcore: registered new driver usbfs
[17179580.968000] usbcore: registered new driver hub
[17179582.144000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[17179595.840000] usbcore: registered new driver hci_usb
[17179596.380000] usbcore: registered new driver bcm203x
[17179919.844000] usb 4-1: USB disconnect, address 2
[17179937.012000] usb 3-2: new full speed USB device using uhci_hcd and address 2
```

```
dmesg|grep Blue
[17179595.788000] Bluetooth: Core ver 2.8
[17179595.788000] Bluetooth: HCI device and connection manager initialized
[17179595.788000] Bluetooth: HCI socket layer initialized
[17179595.840000] Bluetooth: HCI USB driver ver 2.9
[17179595.852000] Bluetooth: Broadcom Blutonium firmware driver ver 1.0
[17179613.524000] Bluetooth: L2CAP ver 2.8
[17179613.524000] Bluetooth: L2CAP socket layer initialized
[17179613.552000] Bluetooth: RFCOMM socket layer initialized
[17179613.552000] Bluetooth: RFCOMM TTY layer initialized
[17179613.552000] Bluetooth: RFCOMM ver 1.7

```

```
lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

```
ls /usr/lib/hotplug/firmware/
BCM2033-2.13-FW.bin  BCM2033-2.15-FW.bin  BCM2033-FW.bin  bcm_changeba  bcm_hex2bin
BCM2033-2.14-FW.bin  BCM2033-2.16-FW.bin  BCM2033-MD.hex  bcm_changeid  BCM-LEGAL.txt
```
This was suggested somewhere on the forums, but I think it's useless because I'm not using hotplug...

Anyways, hciconfig shows no output and the /dev nodes for hci aren't there...

Thanks for the help..
-fred

---

### Post by scxtt on 2006-08-15
are you using KDE or Gnome? -- and what do you want to do w/ that adapter? (just curious in case it's something way more elaborate than that i've done w/ mine: xfer pictures/music to my cellphone) ...

---

### Post by fredmorcos on 2006-08-17
I'm using Gnome, but I have the KDELibs installed (KBluetoothD is way more sophisticated than Gnome-Bluetooth-Manager). But actually I get the same problem with Gnome, the device isn't detected.

All I want to do is transfer files between my computer and my phone.

Thanks.

---

### Post by scxtt on 2006-08-17
i've never attempted to xfer files TO my phone in Gnome, but i've always had success getting pictures from my phone to my computer via my Belkin adapter and the b.t. tools for Gnome ...

i did xfer a picture off my phone using KDE a few days ago and it does seem to make much better use of that OBEX *whatever* ... i didn't try sending anything to my phone, to see if it works, but i might (just to make sure) ...

i would think that using KDE tools in Gnome would be the first thing to make things difficult for you ... if it works w/o a hitch for me, i'd recommend you download Kubuntu and try it in Live mode w/ your adapter & phone ...

---

