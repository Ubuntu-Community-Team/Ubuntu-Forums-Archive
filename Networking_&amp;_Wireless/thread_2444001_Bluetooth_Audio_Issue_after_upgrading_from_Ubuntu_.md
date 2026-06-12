---
title: "Bluetooth Audio Issue after upgrading from Ubuntu 18.04 to Ubuntu 20.04"
date: 2020-05-23
forum: Networking &amp; Wireless
---

### Post by abhimanyudwivedi on 2020-05-23
[COLOR=#242729][FONT=inherit]I upgraded my machine from Ubuntu 18.04 to Ubuntu 20.04. After upgrade, the audio playback on my Bluetooth Headphone stopped. Any streaming video on browser get barred automatically.[/FONT][/COLOR][COLOR=#242729][FONT=Arial][FONT=inherit]When I looked at status, it said -
[/FONT]
[/FONT][/COLOR]```
anton@anton-X510UNR:~$ sudo /etc/init.d/bluetooth status
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2020-05-23 11:39:55 IST; 1h 25min ago
       Docs: man:bluetoothd(8)
   Main PID: 1076 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 9350)
     Memory: 2.6M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1076 /usr/lib/bluetooth/bluetoothd

May 23 11:39:55 anton-X510UNR bluetoothd[1076]: Bluetooth daemon 5.53
May 23 11:39:55 anton-X510UNR systemd[1]: Started Bluetooth service.
May 23 11:39:55 anton-X510UNR bluetoothd[1076]: Starting SDP server
May 23 11:39:55 anton-X510UNR bluetoothd[1076]: Bluetooth management interface 1.14 initialized
May 23 11:40:15 anton-X510UNR bluetoothd[1076]: Endpoint registered: sender=:1.81 path=/MediaEndpoint/A2DPSink/sbc
May 23 11:40:15 anton-X510UNR bluetoothd[1076]: Endpoint registered: sender=:1.81 path=/MediaEndpoint/A2DPSource/sbc
May 23 11:40:42 anton-X510UNR bluetoothd[1076]: Endpoint registered: sender=:1.139 path=/MediaEndpoint/A2DPSink/sbc
May 23 11:40:42 anton-X510UNR bluetoothd[1076]: Endpoint registered: sender=:1.139 path=/MediaEndpoint/A2DPSource/sbc
May 23 11:40:42 anton-X510UNR bluetoothd[1076]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
May 23 11:40:42 anton-X510UNR bluetoothd[1076]: RFCOMM server failed for :1.139/Profile/HSPHSProfile/00001108-0000-1000-8000-00805f9b34fb: rfcomm_bind: Address already in use (98)
```

[COLOR=#242729][FONT=Arial]Looking at the error logs it seems more like a pulseaudio issue. I tried to correct this by -

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]snap install pulseaudio[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]but it didn't helped me. Here is the log-

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]anton@anton-X510UNR:~$ snap install pulseaudio[/FONT][/COLOR]
pulseaudio 8.0-3 from Canonical* installed
anton@anton-X510UNR:~$ snap interfaces pulseaudio
Slot                Plug
:home               pulseaudio
:network            pulseaudio
pulseaudio:service  pulseaudio:client

'snap interfaces' is deprecated; use 'snap connections'.
anton@anton-X510UNR:~$ sudo /etc/init.d/bluetooth status
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2020-05-23 13:27:48 IST; 1h 32min ago
       Docs: man:bluetoothd(8)
   Main PID: 1097 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 9350)
     Memory: 3.1M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1097 /usr/lib/bluetooth/bluetoothd

May 23 14:52:03 anton-X510UNR bluetoothd[1097]: Endpoint unregistered: sender=:1.139 path=/MediaEndpoint/A2DPSink/sbc
May 23 14:52:03 anton-X510UNR bluetoothd[1097]: Endpoint unregistered: sender=:1.139 path=/MediaEndpoint/A2DPSource/sbc
May 23 14:52:05 anton-X510UNR bluetoothd[1097]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
May 23 14:52:05 anton-X510UNR bluetoothd[1097]: RFCOMM server failed for :1.139/Profile/HSPHSProfile/00001108-0000-1000-8000-00805f9b34fb: rfcomm_bind: Address already in use (98)
May 23 14:52:05 anton-X510UNR bluetoothd[1097]: Failed to set mode: Blocked through rfkill (0x12)
May 23 14:52:05 anton-X510UNR bluetoothd[1097]: Endpoint registered: sender=:1.80 path=/MediaEndpoint/A2DPSink/sbc
May 23 14:52:05 anton-X510UNR bluetoothd[1097]: Endpoint registered: sender=:1.80 path=/MediaEndpoint/A2DPSource/sbc
May 23 14:52:05 anton-X510UNR bluetoothd[1097]: Endpoint registered: sender=:1.139 path=/MediaEndpoint/A2DPSink/sbc
May 23 14:52:05 anton-X510UNR bluetoothd[1097]: Endpoint registered: sender=:1.139 path=/MediaEndpoint/A2DPSource/sbc [COLOR=#242729][FONT=Consolas]May 23 14:52:05 anton-X510UNR bluetoothd[1097]: Failed to set mode: Blocked through rfkill (0x12)[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]These are the packages I have related to bluetooth on my machine.

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]anton@anton-X510UNR:~$ dpkg -l | grep -i blue[/FONT][/COLOR]
ii  bluez                                      5.53-0ubuntu3                              amd64        Bluetooth tools and daemons
ii  bluez-cups                                 5.53-0ubuntu3                              amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                5.53-0ubuntu3                              amd64        bluez obex daemon
ii  gir1.2-gnomebluetooth-1.0:amd64            3.34.1-1                                   amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth                            3.34.1-1                                   amd64        GNOME Bluetooth tools
ii  libbluetooth3:amd64                        5.53-0ubuntu3                              amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth13:amd64                 3.34.1-1                                   amd64        GNOME Bluetooth tools - support library [COLOR=#242729][FONT=Consolas]ii  pulseaudio-module-bluetooth                1:13.99.1-1ubuntu3.2[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Can someone help to figure this out.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR]

---

