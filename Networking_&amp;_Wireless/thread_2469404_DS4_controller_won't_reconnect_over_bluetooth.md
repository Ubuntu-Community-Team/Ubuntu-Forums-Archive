---
title: "DS4 controller won't reconnect over bluetooth"
date: 2021-11-28
forum: Networking &amp; Wireless
---

### Post by chapc on 2021-11-28
Hi there!
I've just recently switched my media centre PC from Windows 10 to Lubuntu and am I finding it much faster and am loving the room for customisation. I've worked through my share of issues with success so far, however I'm stuck on this one relating to Bluetooth.

After pairing my PS4 controller using bluetoothctl, it doesn't reconnect to the PC after a reboot. No messages appear in bluetoothctl and the controller eventually times out and switches back off. 

After some troubleshooting I've found that toggling discovery manually always allows the controller to connect. Here's what I mean:

```

tvdesktop@DarthChonkiusTV:/home/tv$ bluetoothctl
Agent registered
[CHG] Controller AC:12:03:EA:E2:31 Pairable: yes
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# show
Controller AC:12:03:EA:E2:31 (public)
        Name: DarthChonkiusTV
        Alias: DarthChonkiusTV
        Class: 0x002c0000
        Powered: yes
        Discoverable: no
        DiscoverableTimeout: 0x000000b4
        Pairable: yes
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
        UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
        UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
        UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
        UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
        UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
        UUID: Headset AG                (00001112-0000-1000-8000-00805f9b34fb)
        Modalias: usb:v1D6Bp0246d0538
        Discovering: no
        Roles: central
        Roles: peripheral
Advertising Features:
        ActiveInstances: 0x00 (0)
        SupportedInstances: 0x05 (5)
        SupportedIncludes: tx-power
        SupportedIncludes: appearance
        SupportedIncludes: local-name
### I turn the DS4 controller on. It attempts to connect for ~20 seconds and will then power off, unless I change discoverable while it's trying to connect ###
[bluetooth]# discoverable on
Changing discoverable on succeeded
[CHG] Controller AC:12:03:EA:E2:31 Discoverable: yes
### The controller then connects immediately ###
[CHG] Device AC:FD:93:76:A8:1D Connected: yes
### I turn the DS4 controller off. ###
[CHG] Device AC:FD:93:76:A8:1D Connected: no
### Wait a few seconds and turn the controller back on. Same story, no connection until I change discoverable ###
[bluetooth]# discoverable off
Changing discoverable off succeeded
[CHG] Controller AC:12:03:EA:E2:31 Discoverable: no
### And again the controller immediately connects when discoverable changes ###
[CHG] Device AC:FD:93:76:A8:1D Connected: yes

```

I followed the following process for pairing, which seems to work fine:
```

tvdesktop@DarthChonkiusTV:/home/tv$ bluetoothctl
Agent registered
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[CHG] Controller AC:12:03:EA:E2:31 Discovering: yes
### Bunch of unrelated devices appear... #
[NEW] Device AC:FD:93:76:A8:1D Wireless Controller
[bluetooth]# pair AC:FD:93:76:A8:1D
Attempting to pair with AC:FD:93:76:A8:1D
[CHG] Device AC:FD:93:76:A8:1D Connected: yes
[CHG] Device AC:FD:93:76:A8:1D Modalias: usb:v054Cp05C4d0100
[CHG] Device AC:FD:93:76:A8:1D UUIDs: 00001124-0000-1000-8000-00805f9b34fb
[CHG] Device AC:FD:93:76:A8:1D UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Device AC:FD:93:76:A8:1D ServicesResolved: yes
[CHG] Device AC:FD:93:76:A8:1D Paired: yes
Pairing successful
[CHG] Device AC:FD:93:76:A8:1D WakeAllowed: yes
Authorize service
[agent] Authorize service 00001124-0000-1000-8000-00805f9b34fb (yes/no): yes
[bluetooth]# trust AC:FD:93:76:A8:1D
[CHG] Device AC:FD:93:76:A8:1D Trusted: yes
Changing AC:FD:93:76:A8:1D trust succeeded

```

The output of wireless-info is at [https://pastebin.ubuntu.com/p/tSQWjhXMPt/](https://pastebin.ubuntu.com/p/tSQWjhXMPt/). Both the DS4 controller and the BT/wifi card (TP-LINK Archer T5E) worked on the previous Windows 10 install.

Any ideas on why I have to manually toggle that setting for the controller to connect? Thanks in advance!

---

