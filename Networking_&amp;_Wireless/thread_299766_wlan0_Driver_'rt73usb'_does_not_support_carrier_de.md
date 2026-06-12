---
title: "wlan0: Driver 'rt73usb' does not support carrier detection"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by shaman11 on 2006-11-14
Hello,

I have problems to get my wireless USB stick up and running under Edgy. The interface worked fine in dapper using the ndiswrapper interface. Apparently Edgy included the Ralink driver (rt73usb) but does not work with NetworkManager.

NetworkManager detects the interface however I get the following error message in daemon mode:

NetworkManager: <information> wlan0: Driver 'rt73usb' does not support carrier detection.
You must switch to it manually.
NetworkManager: <information> nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information> nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information> Now managing wired Ethernet (802.3) device 'wlan0'.
NetworkManager: <information> Deactivating device wlan0. 

The Knetworkmanager screen now shows wlan0 as a wired device.

Who can help me with that?

thanks

---

### Post by FrodoB on 2006-11-14
This driver may resolve your issue. It is very stable. I do not know if it fixes your specific issue, but it might be worth a try. These instructions have been used successfully for other rt73 devices other than the Belkin.

Belkin F5D7050 ver 3000 Ralink rt73 Instructions:
[https://help.ubuntu.com/community/Wi...cs%2FDevice%29](https://help.ubuntu.com/community/Wi...cs%2FDevice%29)

---

### Post by shaman11 on 2006-11-17
Thanks for the assistance.

In a first step I used ndiswrapper which workes fine.
However I think I will give the driver you have proposed a try.


Martin

---

