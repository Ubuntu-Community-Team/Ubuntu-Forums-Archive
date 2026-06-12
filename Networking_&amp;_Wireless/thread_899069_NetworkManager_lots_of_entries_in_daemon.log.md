---
title: "NetworkManager: lots of entries in daemon.log"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by brian mcgee on 2008-08-24
As my machine was booting up and settling down after login, I noticed many entries in /var/log/daemon.log by NetworkManager. Any ideas on what's going on?

This is just a sample of the last few seconds of the log. There are **hundreds** of these entries. Once the machine sits for a bit, the entries stop. Is this normal?

```
Aug 23 21:59:36 12345 NetworkManager: <debug> [1219550376.671365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:36 12345 NetworkManager: <debug> [1219550376.829701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:36 12345 NetworkManager: <debug> [1219550376.838034] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:36 12345 NetworkManager: <debug> [1219550376.838153] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:37 12345 NetworkManager: <debug> [1219550377.138719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:37 12345 NetworkManager: <debug> [1219550377.258896] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:37 12345 NetworkManager: <debug> [1219550377.392252] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:37 12345 NetworkManager: <debug> [1219550377.397341] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:37 12345 NetworkManager: <debug> [1219550377.771609] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:37 12345 NetworkManager: <debug> [1219550377.906877] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:38 12345 NetworkManager: <debug> [1219550378.039058] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:38 12345 NetworkManager: <debug> [1219550378.053177] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:38 12345 NetworkManager: <debug> [1219550378.414964] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:38 12345 NetworkManager: <debug> [1219550378.542903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:38 12345 NetworkManager: <debug> [1219550378.668845] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:38 12345 NetworkManager: <debug> [1219550378.679356] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:39 12345 NetworkManager: <debug> [1219550379.057465] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 23 21:59:39 12345 NetworkManager: <debug> [1219550379.190101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 23 21:59:40 12345 NetworkManager: <debug> [1219550380.364407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_hiddev').
```Please let me know what other info is needed.

---

### Post by brian mcgee on 2008-08-24
Okay, more developments. I think this might be related to my APC Smart-UPS. Here is a sample from the latest of today's logs:

```
Aug 24 14:57:43 12345 apcupsd[6423]: Communications with UPS restored.
Aug 24 14:57:44 12345 NetworkManager: <debug> [1219611464.481458] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_hiddev'). 
Aug 24 14:57:51 12345 apcupsd[6423]: Communications with UPS restored.
Aug 24 15:12:24 12345 NetworkManager: <debug> [1219612344.434553] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_hiddev'). 
Aug 24 15:12:24 12345 NetworkManager: <debug> [1219612344.444295] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 24 15:12:24 12345 NetworkManager: <debug> [1219612344.454079] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 24 15:12:24 12345 NetworkManager: <debug> [1219612344.837773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_AS0826141016'). 
Aug 24 15:12:24 12345 NetworkManager: <debug> [1219612344.986871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 24 15:12:26 12345 NetworkManager: <debug> [1219612346.142229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_hiddev'). 
Aug 24 15:12:31 12345 apcupsd[6423]: Communications with UPS restored.
```Regarding the UPS, sometimes apcupsd is running fine, other times not. 

```
apcaccess status
```will either return what it's supposed to, or I get a cannot connect error.

---

