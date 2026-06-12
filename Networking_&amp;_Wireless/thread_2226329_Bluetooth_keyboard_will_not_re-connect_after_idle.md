---
title: "Bluetooth keyboard will not re-connect after idle"
date: 2014-05-26
forum: Networking &amp; Wireless
---

### Post by maxxjr on 2014-05-26
If I leave my PC for a few hours, my bluetooth keyboard will not reconnect.  The mouse continues to work okay.  If I toggle the power button on the keyboard, connection is re-established.

Any ideas about what this issue may be, or what I should look at?

Thanks!

This is running XUbuntu 13.10.  
PC is an Intel NUC, with the Intel wireless card installed.  (I think I have seen this issue on another PC, but did not pursue it then)
The keyboard is a Microsoft 5000-series model.
Mouse is by Logitech.

I have another copy of the keyboard that I use with a Windows PC, and I do not have this connection issue.

---

### Post by tgalati4 on 2014-05-26
You might need a keep-awake script as a work-around.  

First determine what bluetooth tools you have on your system.  Open a terminal:

```
apropos bluetooth
```

Then find out what bluetooth tools are available in your repositories:

```
apt-cache search bluetooth
```

Then search the forums for your model keyboard.

Use the tools to see what is happening to the bluetooth connection.

Take a look at:

bluez-btsco - Bluez Bluetooth SCO tool
bluez-hcidump - Analyses Bluetooth HCI packets
bluez-pcmcia-support - PCMCIA support files for BlueZ 2.0 Bluetooth tools
bluez-tools - Set of tools to manage Bluetooth devices for linux

---

