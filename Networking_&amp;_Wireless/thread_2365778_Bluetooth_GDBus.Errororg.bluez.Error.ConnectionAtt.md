---
title: "Bluetooth: GDBus.Error:org.bluez.Error.ConnectionAttemptFaile d: Page Timeout"
date: 2017-07-10
forum: Networking &amp; Wireless
---

### Post by zhangweiwu on 2017-07-10
Using 17.04. The wizard would fail - both the bluetooth applet shipped and blueman wizard would fail the same way.

1. Detected Microsoft Sculpt Touch Mouse
2. Set the mouse to pairing mode (with this model - flash red and green)
2. Click "Connect" to the device. With either app, no pin will be asked (the mouse defaults to 0000 anyway).
3. Both app displays "Failed to add device", with the mouse still flashing red and green.

The relevant syslog has:

```
ul 10 23:31:43 colourful bluetooth-wizar[5675]: Connecting to session manager
Jul 10 23:31:43 colourful bluetooth-wizar[5675]: _fcitx_connection_create_ic
Jul 10 23:31:43 colourful bluetooth-wizar[5675]: _fcitx_connection_connection_finished
Jul 10 23:31:43 colourful bluetooth-wizar[5675]: New Adapter interface added.
Jul 10 23:31:43 colourful bluetooth-wizar[5675]: New Device interface added.
Jul 10 23:31:44 colourful bluetooth-wizar[5675]: New Device interface added.
Jul 10 23:31:44 colourful bluetooth-wizar[5675]: Unhandled UUID 0000fe9f-0000-1000-8000-00805f9b34fb (0xfe9f)
Jul 10 23:31:45 colourful bluetooth-wizar[5675]: New Device interface added.
Jul 10 23:31:45 colourful bluetooth-wizar[5675]: New Device interface added.
Jul 10 23:31:45 colourful bluetooth-wizar[5675]: Unhandled UUID 00000f3e-0000-1000-8000-00805f9b34fb (0xf3e)
Jul 10 23:31:45 colourful bluetooth-wizar[5675]: Unhandled property: ManufacturerData
Jul 10 23:31:56 colourful bluetooth-wizar[5675]: Pair() failed for /org/bluez/hci0/dev_28_18_78_F3_86_A6: GDBus.Error:org.bluez.Error.ConnectionAttemptFailed: Page Timeo
ut
Jul 10 23:31:56 colourful bluetooth-wizar[5675]: Setting up 'Microsoft Sculpt Touch Mouse' (at /org/bluez/hci0/dev_28_18_78_F3_86_A6) failed: GDBus.Error:org.bluez.Error
.ConnectionAttemptFailed: Page Timeout
Jul 10 23:32:03 colourful bluetooth-wizar[5675]: Unhandled property: RSSI
Jul 10 23:32:03 colourful bluetooth-wizar[5675]: New Device interface added.
Jul 10 23:32:29 colourful bluetooth-wizar[5675]: Pair() failed for /org/bluez/hci0/dev_28_18_78_F3_86_A6: Se alcanzó el tiempo de expiración
Jul 10 23:32:29 colourful bluetooth-wizar[5675]: Setting up 'Microsoft Sculpt Touch Mouse' (at /org/bluez/hci0/dev_28_18_78_F3_86_A6) failed: Se alcanzó el tiempo de exp
iración
Jul 10 23:32:53 colourful bluetooth-wizar[5675]: Pair() failed for /org/bluez/hci0/dev_28_18_78_F3_86_A6: GDBus.Error:org.bluez.Error.InProgress: In Progress
Jul 10 23:32:53 colourful bluetooth-wizar[5675]: Setting up 'Microsoft Sculpt Touch Mouse' (at /org/bluez/hci0/dev_28_18_78_F3_86_A6) failed: GDBus.Error:org.bluez.Error
.InProgress: In Progress
Jul 10 23:32:58 colourful bluetooth-wizar[5675]: Got NULL pincode, will not pair with Microsoft Sculpt Touch Mouse
Jul 10 23:33:03 colourful bluetoothd[951]: 28:18:78:F3:86:A6: error updating services: Host is down (112)
Jul 10 23:33:03 colourful bluetooth-wizar[5675]: Connect failed for /org/bluez/hci0/dev_28_18_78_F3_86_A6: GDBus.Error:org.bluez.Error.Failed: Host is down
Jul 10 23:33:03 colourful bluetooth-wizar[5675]: Failed to connect to device /org/bluez/hci0/dev_28_18_78_F3_86_A6

```

In case of blueman, only this:
```

Jul 10 23:57:25 colourful blueman.desktop[2113]: org.bluez.Error.ConnectionAttemptFailed: Page Timeout

```

Any hint where to try from here? Thanks. The device works fine if I dual-boot to Windows.

---

