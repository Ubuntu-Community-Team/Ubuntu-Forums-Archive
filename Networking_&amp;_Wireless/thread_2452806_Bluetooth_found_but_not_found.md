---
title: "Bluetooth found but not found"
date: 2020-10-28
forum: Networking &amp; Wireless
---

### Post by asearle on 2020-10-28
Hi Everyone,

I am trying to get Bluetooth working on an HP Probook 4540s and have the following strange situation ...

systemctl detects the bluetooth device ...

```
# systemctl | grep -i blue
  sys-devices-pci0000:00-0000:00:1c.3-0000:03:00.0-net-wlo1.device                         loaded active plugged   RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
  sys-subsystem-net-devices-wlo1.device                                                    loaded active plugged   RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
  bluetooth.service                                                                        loaded active running   Bluetooth service 
```

... but BlueMan cannot find an adaptor ...

```
# sudo blueman-manager
blueman-manager version 2.1.2 starting
blueman-manager 20.22.18 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 20.22.18 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting
```

Has anyone got an idea what is happening here?  And how can I fix it?

Many thanks,
Alan in Cologne

---

### Post by jeremy31 on 2020-10-29
That device has been problematic for years, there was a partial fix available in the past if you search for RT3290 bluetooth Ubuntu.  I haven't kept up and don't know if they made progress or gave up

---

### Post by asearle on 2020-10-30
Hallo Jeremy,

Many thanks for that tip!

I will take a look and see what is available and otherwise get hold of an external (USB) bluetooth device.  Does anyone have any tips for a good one of those?

I'll keep you posted on what I find out.

Thanks,
Alan

---

### Post by asearle on 2020-10-30
Jeremy,

Many thanks:  With this link ...

[https://webwiks.com/techcorner/get-ralink-rt3290-bluetooth-work-in-linux/]("https://webwiks.com/techcorner/get-ralink-rt3290-bluetooth-work-in-linux/")

I managed to get the ralink RT3290 working and scanning for devices. I was very pleased.

It found both devices that I needed to test and they worked perfectly.

Excellent, excellent, excellent.

Many thanks,
Alan

---

### Post by asearle on 2020-11-03
Hallo Everyone,

The link above managed to fix the problem but only when Blueman is opened with root (sudo) permissions. Otherwise the standard installation of Blueman still fails to see devices.

I have to do the following ...

```
# sudo modprobe rtbth
# sudo blueman-manager
```

Then the "device browser" appears and I can connect to (for example) a bluetooth speaker.

But that is a lot of extra effort so does anyone know how I could transfer this to make it apply to the normal (non-root) instance of bluetooth?  Maybe I could embed those commands in a configuration file?

Many thanks.

Yours,
Alan

---

### Post by praseodym on 2020-11-03
Try
```

sudo apt-get install --reinstall rtbth-dkms blueman
```

---

