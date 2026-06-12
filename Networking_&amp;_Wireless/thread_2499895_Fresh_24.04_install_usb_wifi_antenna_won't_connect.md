---
title: "Fresh 24.04 install usb wifi antenna won't connect"
date: 2024-08-14
forum: Networking &amp; Wireless
---

### Post by Rafael_Acurcio on 2024-08-14
Fresh installed dual-boot windows/Ubuntu

Antenna model: TP-link AX1800 dual antenna high gain

Driver source: [https://github.com/lwfinger/rtl8852au](https://github.com/lwfinger/rtl8852au)

Ubuntu recognizes the antenna, I'm able to search for the available networks, but it won't connect...

Here's the output of the wireless script: [https://pastebin.com/UCdAR42m](https://pastebin.com/UCdAR42m)

Here's the journalctl output when trying to connect:

```

Aug 14 14:51:30 user-desktop NetworkManager[23303]: <info>  [1723639890.9570] device (wlx98254a6fcf41): Activation: (wifi) connection 'MY_NETWORK_NAME' has security, and secrets exist.  No new secrets needed.
Aug 14 14:51:30 user-desktop NetworkManager[23303]: <info>  [1723639890.9669] device (wlx98254a6fcf41): supplicant interface state: disconnected -> associating
Aug 14 14:51:37 user-desktop NetworkManager[23303]: <info>  [1723639897.7714] device (wlx98254a6fcf41): supplicant interface state: associating -> disconnected
Aug 14 14:51:37 user-desktop NetworkManager[23303]: <info>  [1723639897.8765] device (wlx98254a6fcf41): supplicant interface state: disconnected -> scanning
Aug 14 14:51:47 user-desktop NetworkManager[23303]: <info>  [1723639907.3879] device (wlx98254a6fcf41): supplicant interface state: scanning -> associating
Aug 14 14:51:48 user-desktop NetworkManager[23303]: <info>  [1723639908.6444] device (wlx98254a6fcf41): state change: config -> deactivating (reason 'new-activation', sys-iface-state: 'managed')
Aug 14 14:51:48 user-desktop NetworkManager[23303]: <info>  [1723639908.6449] device (wlx98254a6fcf41): disconnecting for new activation request.
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1313] device (wlx98254a6fcf41): state change: deactivating -> disconnected (reason 'new-activation', sys-iface-state: 'managed')
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1321] device (wlx98254a6fcf41): Activation: starting connection 'MY_NETWORK_NAME' (1134155a-503d-4ace-8ae3-9449da4d32db)
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1324] device (wlx98254a6fcf41): supplicant interface state: associating -> disconnected
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1326] device (wlx98254a6fcf41): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1329] device (wlx98254a6fcf41): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1330] device (wlx98254a6fcf41): Activation: (wifi) access point 'MY_NETWORK_NAME' has security, but secrets are required.
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1330] device (wlx98254a6fcf41): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1331] sup-iface[808dc8d34ac3970d,1,wlx98254a6fcf41]: wps: type pbc start...
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1337] device (wlx98254a6fcf41): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1338] device (wlx98254a6fcf41): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.1340] device (wlx98254a6fcf41): Activation: (wifi) connection 'MY_NETWORK_NAME' has security, and secrets exist.  No new secrets needed.
Aug 14 14:51:50 user-desktop NetworkManager[23303]: <info>  [1723639910.8085] device (wlx98254a6fcf41): supplicant interface state: disconnected -> associating
Aug 14 14:51:59 user-desktop NetworkManager[23303]: <info>  [1723639919.7875] device (wlx98254a6fcf41): supplicant interface state: associating -> disconnected
Aug 14 14:52:00 user-desktop NetworkManager[23303]: <info>  [1723639920.2929] device (wlx98254a6fcf41): supplicant interface state: disconnected -> scanning
Aug 14 14:52:08 user-desktop NetworkManager[23303]: <info>  [1723639928.6503] device (wlx98254a6fcf41): supplicant interface state: scanning -> associating
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <warn>  [1723639935.0220] device (wlx98254a6fcf41): Activation: (wifi) association took too long
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <info>  [1723639935.0220] device (wlx98254a6fcf41): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <info>  [1723639935.0222] sup-iface[808dc8d34ac3970d,1,wlx98254a6fcf41]: wps: type pbc start...
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <warn>  [1723639935.0223] device (wlx98254a6fcf41): Activation: (wifi) asking for new secrets
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <info>  [1723639935.0227] device (wlx98254a6fcf41): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <info>  [1723639935.0229] device (wlx98254a6fcf41): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <info>  [1723639935.0231] device (wlx98254a6fcf41): Activation: (wifi) connection 'MY_NETWORK_NAME' has security, and secrets exist.  No new secrets needed.
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <info>  [1723639935.3330] device (wlx98254a6fcf41): supplicant interface state: associating -> disconnected
Aug 14 14:52:15 user-desktop NetworkManager[23303]: <info>  [1723639935.3414] device (wlx98254a6fcf41): supplicant interface state: disconnected -> scanning
Aug 14 14:52:18 user-desktop NetworkManager[23303]: <info>  [1723639938.2194] device (wlx98254a6fcf41): supplicant interface state: scanning -> disconnected
Aug 14 14:52:27 user-desktop NetworkManager[23303]: <info>  [1723639947.2172] device (wlx98254a6fcf41): supplicant interface state: disconnected -> associating
Aug 14 14:52:27 user-desktop NetworkManager[23303]: <info>  [1723639947.2173] device (wlx98254a6fcf41): supplicant interface state: associating -> disconnected
Aug 14 14:52:30 user-desktop NetworkManager[23303]: <info>  [1723639950.2493] device (wlx98254a6fcf41): supplicant interface state: disconnected -> associating
Aug 14 14:52:36 user-desktop NetworkManager[23303]: <info>  [1723639956.6513] device (wlx98254a6fcf41): supplicant interface state: associating -> disconnected
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <warn>  [1723639961.0249] device (wlx98254a6fcf41): Activation: (wifi) association took too long
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <info>  [1723639961.0249] device (wlx98254a6fcf41): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <info>  [1723639961.0251] sup-iface[808dc8d34ac3970d,1,wlx98254a6fcf41]: wps: type pbc start...
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <warn>  [1723639961.0252] device (wlx98254a6fcf41): Activation: (wifi) asking for new secrets
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <info>  [1723639961.0258] device (wlx98254a6fcf41): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <info>  [1723639961.0260] device (wlx98254a6fcf41): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <info>  [1723639961.0262] device (wlx98254a6fcf41): Activation: (wifi) connection 'MY_NETWORK_NAME' has security, and secrets exist.  No new secrets needed.
Aug 14 14:52:41 user-desktop NetworkManager[23303]: <info>  [1723639961.0285] device (wlx98254a6fcf41): supplicant interface state: disconnected -> scanning
Aug 14 14:52:49 user-desktop NetworkManager[23303]: <info>  [1723639969.1016] device (wlx98254a6fcf41): supplicant interface state: scanning -> associating
Aug 14 14:52:56 user-desktop NetworkManager[23303]: <info>  [1723639976.1074] device (wlx98254a6fcf41): supplicant interface state: associating -> disconnected
Aug 14 14:53:06 user-desktop NetworkManager[23303]: <warn>  [1723639986.0230] device (wlx98254a6fcf41): Activation: (wifi) association took too long
Aug 14 14:53:06 user-desktop NetworkManager[23303]: <info>  [1723639986.0230] device (wlx98254a6fcf41): state change: config -> failed (reason 'no-secrets', sys-iface-state: 'managed')
Aug 14 14:53:06 user-desktop NetworkManager[23303]: <warn>  [1723639986.0233] device (wlx98254a6fcf41): Activation: failed for connection 'MY_NETWORK_NAME'
Aug 14 14:53:06 user-desktop NetworkManager[23303]: <info>  [1723639986.0234] device (wlx98254a6fcf41): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Aug 14 14:53:14 user-desktop NetworkManager[23303]: <info>  [1723639994.1193] device (wlx98254a6fcf41): supplicant interface state: disconnected -> inactive

```

i've been hitting against this wall for quite some time without solution...

---

### Post by currentshaft on 2024-08-14
>

---

### Post by Rafael_Acurcio on 2024-08-18
I have been playing around with this antenna... and I still don't understand what's wrong. Somewhere deep into some old posts I saw a guy who said that booting into windows, restarting and then booting into linux would help... and indeed it does! It works in I do this login into windows then restart and boot into linux.
When the antenna is non-cooperative if I try to connect using your command it outputs the following

$nmcli device wifi connect <WIFI_SSID> password <PASSWORD>

Error: Connection activation failed: Secrets were required, but not provided.

---

### Post by jeremy31 on 2024-08-18
Can you change the channel the wifi router uses to channel 11?

---

### Post by currentshaft on 2024-08-18
'

---

### Post by Rafael_Acurcio on 2024-08-19
Did you actually replace WIFI_SSID and PASSWORD with the correct values?
- Yes, I used the correct values when trying to connect with the network. 
If so, does the password contain any special characters?
- No, the password contains only letters and numbers.

---

