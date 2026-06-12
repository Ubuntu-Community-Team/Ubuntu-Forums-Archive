---
title: "Network Manager cannot connect to wireless network"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Symmetric on 2008-10-17
Hi all,

I am currently using Ubuntu 8.04. I previously connected to my wireless router using a Netgear wg111v2 usb dongle, and all was working fine.

I just got an internal card, which is not quite working.

Pertinent information:
Laptop is pretty old (hp nx9020), and the NIC uses the ipw2200 driver.

Running ifconfig, I see eth0 and l0, eth0 being my ethernet card.

Running ifconfig -a, I also see eth1, my wireless card.

nm-tool displays both eth0 and eth1; for eth1 the settings read:
Driver: ipw2200
Active: no

Capabilities:
Supported: yes

Wireless Settings
Scanning:yes

Wireless Networks
[empty]


So it seems that NetworkManager knows about my card, and thinks it can use it.

Running the Network Settings wizard, I see icons for both wireless and wired connections, with roaming mode enabled. The checkbox on the left is not selectable; it's fixed to off. If I go to properties for my wireless connection, it says "eth1 properties', so again it looks like the card is known.

/etc/network/interfaces has the following lines:

auto lo
iface lo inet loopback

Roaming mode does not result in a connection. I also tried entering the ESSID and password manually, which then fills out some information to /etc/network/interfaces, specifically

iface eth1 inet dchp
wpa-psk ****
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid *

auto eth1


I've tried "ifup eth1", and separately "ifdown eth0", but this didn't help.

Also, running "sudo iwlist eth1 scan" gives:
No scan results

Any help with this would be greatly appreciated.

P

---

### Post by Symmetric on 2008-10-18
I've had no luck getting the network card to work, so I tried taking it out and using my USB interface instead.

I'm worse off than I was before! NetworkManager can see my network, but won't connect to it. I think NetworkManager must be storing some config somewhere that I don't know about.

Running NetworkManager --no-daemon with roaming mode enabled gives:

NetworkManager: <info>  starting...
NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  wlan0: Device is fully-supported using driver 'rtl8187'.
NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01).
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'.
NetworkManager: <info>  Deactivating device wlan0.
NetworkManager: <info>  Updating allowed wireless network lists.
NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): message arguments were invalid (could not deserialize wireless network security information.


Any insights on this warning? Could this be the problem? If I then configure manually, I can connect, and get this output. 

sudo NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  wlan0: Device is fully-supported using driver 'rtl8187'.
NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01).
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'.
NetworkManager: <info>  Deactivating device wlan0.
NetworkManager: <info>  Updating allowed wireless network lists.
NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list.id (could not deserialize wireless networkNetworkManager: <info>  Removing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  Removing wireless (802.11) device 'wlan0'.
NetworkManager: <info>  Deactivating device wlan0.
NetworkManager: <info>  Recreating the device list.
NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  Device list recreated successfully.
NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list.
NetworkManager: <info>  Removing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  Recreating the device list.
NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <debug> [1224347034.625520] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '007'
NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / 007
NetworkManager: <info>  Deactivating device wlan0.
NetworkManager: <info>  Device wlan0 activation scheduled...
NetworkManager: <info>  Activation (wlan0) started...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  Activation (wlan0/wireless): access point '007' is encrypted, but NO valid key exists.  New key needed.
NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network '007'.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.

And then stalls at stage 2 - nothing more happens.
The line "wlan0: Device is fully-supported using driver 'rtl8187'" worries me; I thought it should be ipw or maybe wext. Any insights?

Thanks,
P

---

### Post by Symmetric on 2008-10-21
Any ideas at all? Anyone?

Thanks,
P

---

