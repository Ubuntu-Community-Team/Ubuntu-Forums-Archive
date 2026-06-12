---
title: "Smart phone will only connect for calls &amp; audio with Bluetooth"
date: 2020-09-04
forum: Networking &amp; Wireless
---

### Post by makem2 on 2020-09-04
I am using a Dell XPS-13-9300 duel booted with Windows 10 and a Samsung Galaxy S8 smart phone.

Today I was able to send files from the laptop via bluetooth to the smart phone. Later, when I rebooted the laptop I got an unable to send error when attempting to send a .ods file.

I have unpaired the phone, removed the phone as a device from the laptop and tried to reconnect. Both pair but only for calls and audio. I can no longer send files either way.

I cannot send files from the laptop to a Samsung Galaxy Tab A (2018, 10.5)

I am able to send files from the S8 to the Tab A

When I check the laptop device manager it has the S8 registered as a smart phone.

With all devices disconnected (shown in devices) the bluetooth panel icon still shows one active connection.

I have the following packages installed on the laptop:

blueman 2.1.2-1
bluez 5.53-0ubuntu3
libbluetooth3 5.53-0ubuntu3
bluez-cups 5.53-0ubuntu3
pulseaudio-module-bluetooth 1:12.99.1-1ubuntu3.6

The S8:

```

public
Galaxy S8 makem
Galaxy S8 makem
0x5a020c
0x0000
Icon: phone
Paired: yes
Trusted: yes
Blocked: no
LegacyPairing: no
Connected: yes
00001105-0000-1000-8000-00805f9b34fb OBEX Object Push
00001108-0000-1000-8000-00805f9b34fb Headset
0000110a-0000-1000-8000-00805f9b34fb Audio Source
0000110c-0000-1000-8000-00805f9b34fb Remote Control Target
0000110d-0000-1000-8000-00805f9b34fb Advanced Audio
0000110e-0000-1000-8000-00805f9b34fb Remote Control
00001112-0000-1000-8000-00805f9b34fb Headset Audio Gateway
00001115-0000-1000-8000-00805f9b34fb PANU
00001116-0000-1000-8000-00805f9b34fb Network Access Point
0000111f-0000-1000-8000-00805f9b34fb Handsfree Audio Gateway
0000112d-0000-1000-8000-00805f9b34fb SIM Access (SAP)
0000112f-0000-1000-8000-00805f9b34fb Phonebook Access (PBAP) - PSE
00001132-0000-1000-8000-00805f9b34fb Message Access Server
00001200-0000-1000-8000-00805f9b34fb PnP Information
00001800-0000-1000-8000-00805f9b34fb Generic Access
00001801-0000-1000-8000-00805f9b34fb Generic Attribute
931c7e8a-540f-4686-b798-e8df0a2ad9f7 Proprietary
bluetooth:v0075p1200d1436
/org/bluez/hci0

```

I have rebooted both machines but still cannot send files.

---

### Post by makem2 on 2020-09-05
Started working again.

---

### Post by SeijiSensei on 2020-09-05
You might find KDE Connect a more reliable method. It will use your network rather than Bluetooth. You can install it on machines that don't use KDE. There's an app for it in the Google Play Store.

---

