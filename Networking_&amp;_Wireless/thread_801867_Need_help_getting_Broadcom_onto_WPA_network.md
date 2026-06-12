---
title: "Need help getting Broadcom onto WPA network"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by ddrlord on 2008-05-21
EDIT: Before I can get WPA working, I think it might be beneficial to get unsecured WiFi working 100%. Please read reply below.

Man, Linux sure has come a long way in the user friendly direction since I first gave it a shot some odd years ago. Back then my computer had an unsupported video card, audio card, and wireless card. Yet my TV tuner rocked. Sadly that wasn't good enough for me, and I had to jump back onto Windows 2000.
I just installed Ubuntu 8.04 via Wubi (I didn't want to commit myself to something that might not work. You've broken my heart and my hard drive before, Linux) and everything works great except for my wireless card. I've got a an HP Pavilion dv6000, whose wireless card is a Broadcom 4321AG. I think I managed to install ndiswrapper properly, but no promises. My router is an Apple Airport Extreme, and the wireless network is protected with WPA2. It was WPA, but Ubuntu didn't play nice with that either. I can see the network in Network Manager, and it asks for a key--it even knows if it's WPA or WPA2--but will not connect. Heck, neither of the green lights will even light up in the tray icon. Then it'll just pop up another message asking for a key after a minute or so, until I tell it to stop.
I've followed every tutorial I could find, installed (and subsequently removed) every program I thought might help, but I'm currently stuck.
Keep in mind that I'm completely inexperienced when it comes to Linux, so you'll have to take it slow. Pretend I'm an nine year old that knows what a terminal is.
Anyone have any advice? Personal experience? Step by step I can follow? I'll even rm -rf * if you promise me really hard it'll work.

---

### Post by ddrlord on 2008-05-23
I set the network to no security (temporarily) so see if the problem was the WPA or the router or the planets being misaligned. I can get a connection quickly, and browse the internet for an undetermined (not usually for much longer than 10 minutes) time. After than the connection drops and I have to manually tell it to reconnect. Not exactly something I want to keep doing, especially if I were to ever try and download a large file. The wired network on the same router works perfectly and fast.

I've included a log from NetworkManager, when I ran it with --no-daemon. I'm hoping it'll be useful. The full thing it attached, this is just a snippet of the end of it.

```
NetworkManager: <info>  starting...
NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'.
NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00).
...
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
NetworkManager: <info>  Supplicant state changed: 0
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
...
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one.
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
...
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
NetworkManager: <WARN>  nm_signal_handler(): Caught signal 2, shutting down normally.
NetworkManager: <info>  Caught terminiation signal
NetworkManager: <debug> [1211515651.601745] nm_print_open_socks(): Open Sockets List:
NetworkManager: <debug> [1211515651.601879] nm_print_open_socks():   1: wlan0 fd:18 F:'request_and_convert_scan_results' D:'(null)'
NetworkManager: <debug> [1211515651.601931] nm_print_open_socks(): Open Sockets List Done.
NetworkManager: <info>  Deactivating device wlan0.
CTRL-EVENT-TERMINATING - signal 15 received
sendmsg(CTRL_IFACE monitor): No such file or directory
NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument
NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one.
NetworkManager: <info>  Deactivating device eth0.
```

As extra incentive, if I can't convert to Ubuntu full time I'll be stuck on Vista x64. Do you really want to do that to your fellow man?

---

### Post by ddrlord on 2008-05-24
How disheartening...
I think I'll bump it one more time after this and then just whip out the old "Uninstall" button.

---

