---
title: "Bluetooth not working (16.04, ThinkPad L450)"
date: 2017-09-06
forum: Networking &amp; Wireless
---

### Post by alfred-bez on 2017-09-06
Hi there,

I can't connect to my bluetooth Headset (Bose QuietComfort 35) and hope someone can help me.

```

$ uname -a
Linux abez-ThinkPad-L450 4.4.0-93-generic #116-Ubuntu SMP Fri Aug 11 21:17:51 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


$ dpkg -l | grep blue
ii  blueman                                              2.0.4-1ubuntu2                               amd64        Graphical bluetooth manager
ii  bluez                                                5.37-0ubuntu5                                amd64        Bluetooth tools and daemons
ii  bluez-cups                                           5.37-0ubuntu5                                amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                          5.37-0ubuntu5                                amd64        bluez obex daemon
ii  gir1.2-gnomebluetooth-1.0:amd64                      3.18.2-1ubuntu2                              amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth                                      3.18.2-1ubuntu2                              amd64        GNOME Bluetooth tools
ii  indicator-bluetooth                                  0.0.6+16.04.20160526-0ubuntu1                amd64        System bluetooth indicator.
ii  libbluetooth3:amd64                                  5.37-0ubuntu5                                amd64        Library to use the BlueZ Linux Bluetooth stack
rc  libgnome-bluetooth11                                 3.8.2.1-0ubuntu12                            amd64        GNOME Bluetooth tools - support library
ii  libgnome-bluetooth13:amd64                           3.18.2-1ubuntu2                              amd64        GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth                          1:8.0-0ubuntu3.3                             amd64        Bluetooth module for PulseAudio sound server
[FONT=monospace]
[/FONT]$ sudo service bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Mi 2017-09-06 12:18:00 CEST; 23min ago
     Docs: man:bluetoothd(8)
 Main PID: 4923 (bluetoothd)
   Status: "Running"
    Tasks: 1
   Memory: 532.0K
      CPU: 33ms
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;4923 /usr/lib/bluetooth/bluetoothd


Sep 06 12:18:00 abez-ThinkPad-L450 bluetoothd[4923]: Not enough free handles to register service
Sep 06 12:18:00 abez-ThinkPad-L450 bluetoothd[4923]: Not enough free handles to register service
Sep 06 12:18:00 abez-ThinkPad-L450 bluetoothd[4923]: Sap driver initialization failed.
Sep 06 12:18:00 abez-ThinkPad-L450 bluetoothd[4923]: sap-server: Operation not permitted (1)
Sep 06 12:18:00 abez-ThinkPad-L450 bluetoothd[4923]: Failed to set mode: Not Supported (0x0c)
Sep 06 12:18:00 abez-ThinkPad-L450 bluetoothd[4923]: Endpoint registered: sender=:1.56 path=/MediaEndpoint/A2DPSource
Sep 06 12:18:00 abez-ThinkPad-L450 bluetoothd[4923]: Endpoint registered: sender=:1.56 path=/MediaEndpoint/A2DPSink
Sep 06 12:18:55 abez-ThinkPad-L450 bluetoothd[4923]: Unable to get Headset Voice gateway SDP record: Device or resource busy
Sep 06 12:18:55 abez-ThinkPad-L450 bluetoothd[4923]: connect error: Device or resource busy (16)
Sep 06 12:18:57 abez-ThinkPad-L450 bluetoothd[4923]: connect error: Device or resource busy (16)


$ sudo bluetoothctl
[NEW] Controller 5C:E0:C5:C2:3B:47 Thinkpad_ab [default]
[NEW] Device C8:84:47:01:9F:AD (AD)Logitech Adapter
[NEW] Device 04:52:C7:0B:CF:E7 Bose QuietComfort 35
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# connect 04:52:C7:0B:CF:E7 
Attempting to connect to 04:52:C7:0B:CF:E7
Failed to connect: org.bluez.Error.Failed
[bluetooth]# exit
[DEL] Controller 5C:E0:C5:C2:3B:47 Thinkpad_ab [default]


$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: tpacpi_wwan_sw: Wireless WAN
        Soft blocked: yes
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```[FONT=monospace]
[/FONT]

---

### Post by alfred-bez on 2017-09-06
I solved the problem by removing the device from the Bluetooth paired list in Ubuntu. I paired again and it works now.

---

### Post by bungler2 on 2018-04-28
> **alfred-bez said:**
> I solved the problem by removing the device from the Bluetooth paired list in Ubuntu. I paired again and it works now.

This fixed it for me. Thanks! Still doesn't tell us exactly what went wrong... but I'm able to let that go. ;)

This was the first hit on Google for the error in syslog and I'm running Linux Mint 18. Nonetheless, Linux being Linux, this still worked.

---

