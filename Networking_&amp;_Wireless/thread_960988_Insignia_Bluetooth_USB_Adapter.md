---
title: "Insignia Bluetooth USB Adapter"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by rjonesx on 2008-10-27
I have attempted to install an Insignia NS-BTHDST Headset and USB Adapter and with no luck so far. I am on an HP Pavilian dv2000 laptop (AMD64) with Hardy Heron.

lsusb shows the following, where Bus

Bus 002 Device 011: ID 0a5c:4503 Broadcom Corp.
Bus 002 Device 010: ID 0a5c:4502 Broadcom Corp.
Bus 002 Device 009: ID 0a5c:4500 Broadcom Corp.
Bus 002 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0c45:62c0 Microdia
Bus 001 Device 001: ID 0000:0000

Where Bus 002 Device 011,010, and 009 are all Bluetooth USB device.

However, if I run hciconfig or hcitool, it shows nothing.

~# hciconfig scan
Can't get device info: No such device

:~# hcitool dev
Devices:

Any ideas? I would really like to get this working.

---

### Post by go_beep_yourself on 2008-10-30
Same problem. Did you ever get it resolved?

---

### Post by kewlpics on 2009-01-01
I am having the same issue.  Please help!

$ lsusb

Bus 001 Device 022: ID 0a5c:2120 Broadcom Corp. 
Bus 001 Device 021: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 020: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 019: ID 0a5c:4500 Broadcom Corp. 


$ hciconfig -a

hci0:	Type: USB
	BD Address: 00:02:76:0D:CD:59 ACL MTU: 1017:8 SCO MTU: 64:0
	UP RUNNING 
	RX bytes:603 acl:0 sco:0 events:85 errors:0
	TX bytes:1367 acl:0 sco:0 commands:85 errors:0
	Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
**Can't read local name on hci0: Input/output error (5)**

$ hcitool scan

Scanning ...
**Inquiry failed: Connection timed out**

---

### Post by rugbeeprop on 2009-03-31
I can't either

---

### Post by rugbeeprop on 2009-04-01
> Some of the bluetooth adapters you buy out there is not bluetooth adapters 
at all, they are just a dumb usb device waiting for firmware to be loaded 
so they can be a bluetooth adapter :-/ 
This is the same shite as the windows modems, half products, hostile to it's owners. From [http://help.lockergnome.com/linux/USB-Bluetooth-dongle-recognized--ftopict490680.html](http://help.lockergnome.com/linux/USB-Bluetooth-dongle-recognized--ftopict490680.html)

In light of this, unless Broadcom/Insignia has driver for Linux, it won't work at all.

Another options that I thought of is to buy a real bluetooth dongle/adapter.

First I am going to test it on my work laptop as it has built-in Bluetooth. If it works, then I will get the adapter.

I will keep you posted.


----
UPDATED: April 2, 2009

Just bought Belkin Mini Bluetooth Adapter ([http://catalog.belkin.com/IWCatProductPage.process?Product_Id=398674](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=398674)).

Plugged it in and Ubuntu recognised the adapter right away as a Bluetooth Adapter. Then it did detect the headset. 

Then I followed the instruction here to get the headset working: [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)


--- UPDATED: May 12, 2009
Found a better solution that automatically detect and connect the bluetooth headset:
[http://blueman-project.org/forum/viewtopic.php?f=5&t=111](http://blueman-project.org/forum/viewtopic.php?f=5&t=111)

---

### Post by smacattack on 2009-05-17
For anyone else with this issue, I got my Insignia Bluetooth USB adapter to work by using the following command

```
sudo hciconfig hci0 reset
```

then i just rightclick on the bluetooth icon in the systray, click 'setup new device', set the headset to pair, it shows up...boom, connected.

By default it doesn't seem to integrate with any programs, but I found a guide which lets you connect it to the 'Movies and Music' section in the sound manager which enables it for Rhythmbox etc. Here's how you do it...

while the device is discoverable, type 
```
hcitool scan
```

which will show you the MAC address of the device (for the headset, mine reads 00:1C:EF:38:AE:F5). replace the XX:XX:XX:XX:XX:XX in the following command with the MAC address of the device:

```
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "sbcenc ! a2dpsink device=XX:XX:XX:XX:XX:XX"
```

and it will link the headset to rhythmbox at the very least.


Now I just need to figure out how to link it to flash (for youtube etc.) and I'll be a happy camper. Best of luck to all.

---

