---
title: "Broke my wirelss or keyring or kernel issue??"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by sn00kst3r on 2010-09-12
Yesterday I did a clean install of 10.04 and all seemed to be well.  Ran quite a few programs late last night while watching streaming media and was very pleased.  Today I booted the system and attempted to change my wireless settings to auto connection when booted.  it dropped my wireless connection immediately and I can no longer connect to my wireless. I thought this might be an issue with the keyring security, but there does not seem to be a keyring manager gui in this version. It attempts to connect but will not accept the correct, known security.  I get an error in the syslog now that is below:
________________________________________________________________

Sep 12 16:46:26 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:26 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:26 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:27 UBUT60 kernel: [ 1103.153787] end_request: I/O error, dev fd0, sector 0
Sep 12 16:46:27 UBUT60 kernel: [ 1103.153801] Buffer I/O error on device fd0, logical block 0
Sep 12 16:46:30 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:30 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:30 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:31 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:31 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:32 UBUT60 dbus-daemon: Reloaded configuration
Sep 12 16:46:33 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:35 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:35 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:37 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:39 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:39 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:40 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:40 UBUT60 kernel: [ 1116.218174] end_request: I/O error, dev fd0, sector 0
Sep 12 16:46:40 UBUT60 kernel: [ 1116.218187] Buffer I/O error on device fd0, logical block 0
Sep 12 16:46:43 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:43 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:43 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:47 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:47 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:47 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:51 UBUT60 wpa_supplicant[783]: Trying to associate with 00:18:4d:9c:1a:30 (SSID='JELSONAIR' freq=2462 MHz)
Sep 12 16:46:51 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:51 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:53 UBUT60 kernel: [ 1129.269990] end_request: I/O error, dev fd0, sector 0
_______________________________________________________________

Thanks for any help I can get on this issue!!

---

