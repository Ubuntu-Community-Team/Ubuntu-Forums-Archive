---
title: "Bluetooth on Acer Laptop"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by angelman99 on 2007-11-08
I have an Acer Aspire 5630 and I am attempting to get it to talk to my 6XXX series Nokia mobile phone, I also have a bluetooth headset.

me@acer:/etc/bluetooth$ dmesg | grep "Bluetooth"
```
[   22.756000] Bluetooth: Core ver 2.11
[   22.756000] Bluetooth: HCI device and connection manager initialized
[   22.756000] Bluetooth: HCI socket layer initialized
[   22.784000] Bluetooth: L2CAP ver 2.8
[   22.784000] Bluetooth: L2CAP socket layer initialized
[   22.884000] Bluetooth: RFCOMM socket layer initialized
[   22.884000] Bluetooth: RFCOMM TTY layer initialized
[   22.884000] Bluetooth: RFCOMM ver 1.8
```

me@acer:/etc/bluetooth$ sudo gedit hcid.conf
me@acer:/etc/bluetooth$ sudo hciconfig hci0 reset
Can't get device info: No such device
me@acer:/etc/bluetooth$ hcitool scan
Device is not available: No such device
me@acer:/etc/bluetooth$ hciconfig
me@acer:/etc/bluetooth$ hciconfig -a

I've installed all the bluez and obex packages I can find (and Blueman Bluetooth Manager - reports "no adapters found").

I couldn't get the Hot Keys to install using [http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/)
(the blue light beside the switch to show Bluetooth is not on).
If someone really clever could package this utility so it opens with the Synaptic Package Manager it would be great, I would imagine there are a lot of Acer laptops out there.

I've looked in System > Administration > System Log and there is nothing in there indicating an error with bluetooth.
There are only 2 warnings 1 is can't find APM in BIOS - which I assume is power management.
The other is
Nov  8 13:29:04 acer NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Which is odd, because both the cable connection and the wireless network connections work, I'm using the wireless right now.

Can someone give me a helping hand on where to look to diagnose this problem.
I would assume the solution for this may help anyone else with a Series 5XXX Acer.

---

