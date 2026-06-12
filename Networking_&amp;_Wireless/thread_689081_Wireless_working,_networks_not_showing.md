---
title: "Wireless working, networks not showing"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by rune0077 on 2008-02-06
Okay, here's the issue. I finally got Ubuntu to accept that I have a wireless card (wlan0). It detects the card find and I got "wireless" as an option in network-manager. I can't seem to use it for any good though, since I can't connect to my router with it (other computers/devices connects fine with it), and I don't get a list of available wireless networks. Weird!!

When I load up ndiswrapper, syslog gives me this error, which I'm assuming is the root of the problem:

> Feb  6 08:10:27 Central kernel: [  142.737595] usbcore: registered new interface driver ndiswrapper
Feb  6 08:10:27 Central NetworkManager: <debug> [1202281827.796076] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_18_4d_77_8e_44'). 
Feb  6 08:10:28 Central kernel: [  143.864343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  6 08:10:28 Central NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
Feb  6 08:10:28 Central NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Feb  6 08:10:28 Central NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Feb  6 08:10:28 Central NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Feb  6 08:10:28 Central NetworkManager: <info>  Deactivating device wlan0. 
Feb  6 08:10:30 Central NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument

I try to use "sudo iwconfig wlan0 essid <router-essid> but it changes nothing.

Anyone has a clue, 'coz I sure don't?

---

### Post by rune0077 on 2008-02-06
bumping this one

---

