---
title: "Unable to connect bluetooth device on ubuntu 20.04"
date: 2020-06-02
forum: Networking &amp; Wireless
---

### Post by gg951x on 2020-06-02
I am unable to connect bluetooth device on newly installed ubuntu 20.04. The device when tried to paired and connect shows as paired and connected but no sound comes. When checking logs getting some errors. 

Below are some configuration and logs

Installed packages

```

mypc@root:/var/log$ sudo dpkg -l |grep -i blue
ii  blueman                                    2.1.2-1                               amd64        Graphical bluetooth manager
ii  bluetooth                                  5.53-0ubuntu3                         all          Bluetooth support
ii  bluez                                      5.53-0ubuntu3                         amd64        Bluetooth tools and daemons
ii  bluez-cups                                 5.53-0ubuntu3                         amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                5.53-0ubuntu3                         amd64        bluez obex daemon
ii  gir1.2-gnomebluetooth-1.0:amd64            3.34.1-1                              amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth                            3.34.1-1                              amd64        GNOME Bluetooth tools
ii  libbluetooth3:amd64                        5.53-0ubuntu3                         amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth13:amd64                 3.34.1-1                              amd64        GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth                1:13.99.1-1ubuntu3.2                  amd64        Bluetooth module for PulseAudio sound server


```

```

mypc@root:/var/log$  service bluetooth status
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-06-02 23:18:20 IST; 56s ago
       Docs: man:bluetoothd(8)
   Main PID: 4012 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 19040)
     Memory: 1.6M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;4012 /usr/lib/bluetooth/bluetoothd

Jun 02 23:18:20 mypc systemd[1]: Starting Bluetooth service...
Jun 02 23:18:20 mypc bluetoothd[4012]: Bluetooth daemon 5.53
Jun 02 23:18:20 mypc bluetoothd[4012]: Starting SDP server
Jun 02 23:18:20 mypc systemd[1]: Started Bluetooth service.
Jun 02 23:18:20 mypc bluetoothd[4012]: Bluetooth management interface 1.14 initialized
Jun 02 23:18:20 mypc bluetoothd[4012]: Endpoint registered: sender=:1.75 path=/MediaEndpoint/A2DPSink/sbc
Jun 02 23:18:20 mypc bluetoothd[4012]: Endpoint registered: sender=:1.75 path=/MediaEndpoint/A2DPSource/sbc
Jun 02 23:19:04 mypc bluetoothd[4012]: B8:69:C2:DE:CB:30: error updating services: Connection timed out (110)


```

Bluetoothctl details

```

[bluetooth]# show
Controller 04:ED:33:C4:11:B0 (public)
    Name: aarav
    Alias: aarav
    Class: 0x001c0104
    Powered: yes
    Discoverable: no
    DiscoverableTimeout: 0x00000000
    Pairable: yes
    UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
    UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
    UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
    UUID: Headset AG                (00001112-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
    UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0535
    Discovering: no
Advertising Features:
    ActiveInstances: 0x00
    SupportedInstances: 0x05
    SupportedIncludes: tx-power
    SupportedIncludes: appearance
    SupportedIncludes: local-name
    SupportedSecondaryChannels: 1M
    SupportedSecondaryChannels: 2M
    SupportedSecondaryChannels: Coded


```

Dmesg

```

mypc@root:/var/log$ dmesg |grep -i bluetooth 
[    3.802462] Bluetooth: Core ver 2.22
[    3.802496] Bluetooth: HCI device and connection manager initialized
[    3.802500] Bluetooth: HCI socket layer initialized
[    3.802502] Bluetooth: L2CAP socket layer initialized
[    3.802505] Bluetooth: SCO socket layer initialized
[    3.814782] Bluetooth: hci0: Firmware revision 0.0 build 128 week 11 2020
[    4.430742] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.430743] Bluetooth: BNEP filters: protocol multicast
[    4.430747] Bluetooth: BNEP socket layer initialized
[   12.351532] Bluetooth: RFCOMM TTY layer initialized
[   12.351538] Bluetooth: RFCOMM socket layer initialized
[   12.351541] Bluetooth: RFCOMM ver 1.11


```

---

### Post by CelticWarrior on 2020-06-02
Welcome.

After pairing did you check whether or not it's selected as the sound device? Please do.

---

### Post by gg951x on 2020-06-02
yes, I did check but unable to see that device in Sound settings. Attaching the screenshot

[IMG]https://i.imgur.com/LUUwRlB.png[/IMG]

[IMG]https://i.imgur.com/GwWhEEO.png[/IMG]
[IMG]https://i.imgur.com/oMR8ItM.png[/IMG]

---

### Post by CelticWarrior on 2020-06-02
Remove, pair again. Test... And, by the way, that's a dropdown menu in the Sound settings, in case you missed it.

Also it's in the same System Settings > Bluetooth that you find, enable/disable, configure (pair) and "forget" (remove) Bluetooth devices. Your "Bluetooth Devices" screenshot is non standard. Have you installed something BT related? If so what?

---

