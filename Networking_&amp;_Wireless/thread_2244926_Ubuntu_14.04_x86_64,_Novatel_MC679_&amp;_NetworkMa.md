---
title: "Ubuntu 14.04 x86_64, Novatel MC679 &amp; NetworkManager - what network interface really?"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by axMan5389 on 2014-09-19
Hello,

Hoping to learn what type of network interface the kernel should choose for this Novatel device and how that choice is configured?  My device does not seem to be sensed by the OS correctly, requiring to remove and re-insert before the correct driver choice is made.  So, how can I force the kernel to immediately usb_modeswitch and raise the interface as ppp0 (mobile broadband enabled) when this device is inserted?

Details;
```
3.15.0-999-generic x86_64,  Ubuntu 14.04.1 LTS, trusty
usb-modeswitch		2.1.1+repack0-1ubuntu1
usb-modeswitch-data	20140327-1
network-manager		0.9.8.8-0ubuntu7
modemmanager		1.0.0-2ubuntu1

```
When first inserted, Novatel device is seen by kernel as storage.  Most of the times it is correctly usb_modeswitched.  NetworkManager brings up eth1, what it claims is a second wired network.  There is No mobile broadband choice available in NetworkManager gui..

On first insert
```

181.190575] usb 2-1: New USB device found, idVendor=1410, idProduct=5059

```
After modeswitch
```

Bus 002 Device 010: ID 1410:7031 Novatel Wireless 

```
Driver loads for eth1
```

cdc_ether 2-1:1.6 eth1: register 'cdc_ether' at usb-0000:00:14.0-1, CDC Ethernet Device, 00:a0:c6:00:00:00
[  187.060668] usbcore: registered new interface driver cdc_ether

```
something strange
```

[  187.875237] cdc_ether 2-1:1.6 eth1: CDC: unexpected notification 01!

```
So we "disconnect eth1" in NetworkManager gui and unplug the Novatel device.  Plug Novatel device back in.  NetworkManager again brings up eth1, but this time after a few moments, we get option in gui to "enable mobile broadband."  We select that, and the device registers to mobile network.  We disconnect eth1, and select our mobile network config, and we can then connect to Internet using the Novatel device.

This Novatel device seems to have been supported for a couple of years now, so I don't understand why it is not detected correctly..  I see an entry in /etc/udev/rules.d/70-persistent-net.rules which might explain the continuing re-appearance of eth1 interface, but I do not understand why the kernel tries to enable it..  When the Novatel device is successfuly connected to mobile broadband network, the interface that is active is ppp0.  No IP traffic flows on the eth1 interface that I can see..  Using some kind of physical layer proxy on this eth1 interface?

I just want to force the kernel to immediately usb_modeswitch and raise interface as ppp0 (mobile broadband enabled) when this device is inserted.  Any clues on how to do that are most welcome.

Thanks,

---

