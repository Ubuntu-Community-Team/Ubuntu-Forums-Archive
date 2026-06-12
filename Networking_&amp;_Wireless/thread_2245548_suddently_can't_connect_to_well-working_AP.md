---
title: "suddently can't connect to well-working AP"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by ecc2 on 2014-09-24
I'm having trouble connecting to my wifi at home. It has worked fine for half a year, but today all of a sudden it wouldnt connect anymore. My other computers connect to the same AP without any trouble.
 The computer that is causing the trouble connects fine to my phone when I turn it into a AP, so the network-card should be allright. 
I havn't changed anything in any setup anywhere, just shut down my computer as I use to do. I havnt even done any system-updates prior to the network-failure. 
Does anyone have any idear what is causing this and how to fix it? That youd really make my day! :)

Here is the syslog-dump from the connection (I've removed some identifying information thugh).

```

Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0) starting connection 'AP-name'
Sep 24 17:08:40 computer NetworkManager[967]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 24 17:08:40 computer NetworkManager[967]: <info> NetworkManager state is now CONNECTING
Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 24 17:08:40 computer NetworkManager[967]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0/wireless): access point 'AP-name' has security, but secrets are required.
Sep 24 17:08:40 computer NetworkManager[967]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 24 17:08:40 computer NetworkManager[967]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 24 17:08:41 computer dbus[776]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Sep 24 17:08:41 computer kernel: [   79.686417] systemd-hostnamed[2474]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Sep 24 17:08:41 computer dbus[776]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep 24 17:08:45 computer NetworkManager[967]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Sep 24 17:08:45 computer NetworkManager[967]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 17:08:45 computer NetworkManager[967]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 24 17:08:45 computer NetworkManager[967]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 24 17:08:45 computer NetworkManager[967]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 17:08:45 computer NetworkManager[967]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 17:08:45 computer NetworkManager[967]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 24 17:08:45 computer NetworkManager[967]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 24 17:08:45 computer NetworkManager[967]: <info> Activation (wlan0/wireless): connection 'AP-name' has security, and secrets exist.  No new secrets needed.
Sep 24 17:08:45 computer NetworkManager[967]: <info> Config: added 'ssid' value 'AP-name'
Sep 24 17:08:45 computer NetworkManager[967]: <info> Config: added 'scan_ssid' value '1'
Sep 24 17:08:45 computer NetworkManager[967]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 24 17:08:45 computer NetworkManager[967]: <info> Config: added 'auth_alg' value 'OPEN'
Sep 24 17:08:45 computer NetworkManager[967]: <info> Config: added 'psk' value '<omitted>'
Sep 24 17:08:45 computer NetworkManager[967]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 24 17:08:45 computer NetworkManager[967]: <info> Config: set interface ap_scan to 1
Sep 24 17:08:45 computer NetworkManager[967]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep 24 17:08:45 computer wpa_supplicant[1073]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Sep 24 17:08:46 computer wpa_supplicant[1073]: wlan0: SME: Trying to authenticate with 11:22:33:44:55:66 (SSID='AP-name' freq=2462 MHz)
Sep 24 17:08:46 computer kernel: [   84.754997] wlan0: authenticate with 11:22:33:44:55:66
Sep 24 17:08:46 computer NetworkManager[967]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 24 17:08:46 computer kernel: [   84.760466] wlan0: direct probe to 11:22:33:44:55:66 (try 1/3)
Sep 24 17:08:46 computer kernel: [   84.963835] wlan0: direct probe to 11:22:33:44:55:66 (try 2/3)
Sep 24 17:08:46 computer kernel: [   85.168027] wlan0: direct probe to 11:22:33:44:55:66 (try 3/3)
Sep 24 17:08:46 computer kernel: [   85.372158] wlan0: authentication with 11:22:33:44:55:66 timed out
Sep 24 17:08:46 computer NetworkManager[967]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep 24 17:08:47 computer wpa_supplicant[1073]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 24 17:08:47 computer NetworkManager[967]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep 24 17:09:10 computer NetworkManager[967]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Sep 24 17:09:10 computer NetworkManager[967]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep 24 17:09:10 computer NetworkManager[967]: <info> NetworkManager state is now DISCONNECTED
Sep 24 17:09:10 computer NetworkManager[967]: <warn> Activation (wlan0) failed for connection 'AP-name'
Sep 24 17:09:10 computer NetworkManager[967]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 24 17:09:10 computer NetworkManager[967]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 24 17:09:10 computer NetworkManager[967]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep 24 17:09:10 computer NetworkManager[967]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Sep 24 17:09:11 computer NetworkManager[967]: <info> (wlan0): supplicant interface state: scanning -> inactive



```

---

### Post by tgalati4 on 2014-09-24
If you have a smartphone, then use WiFi Analyzer and see what other AP's are in your neighborhood.  It could be a simple matter of interference.  You might have to shift a different frequency, and shut off frequency-hopping.  I had to shift to channel 4 on G band (2.4 GHz) because every cable modem around me was hopping between 1, 6, and 11, as they are programmed to.  Although my signal is strong when line-of-sight, going through walls and outside, the signal level dropped to interference levels of my neighbors.

The phone AP worked probably because it was:  Low power, nearby, and picked a better frequency than what your house AP is using.

---

### Post by praseodym on 2014-09-24
Please run the wireless script from the sticky thread and post the outputs of it.

Thanks.

---

