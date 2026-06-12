---
title: "Dell Inspirion 5570 - Ubuntu 19.10 Live unable to connect to 5G WiFi"
date: 2020-03-29
forum: Networking &amp; Wireless
---

### Post by Boris_Bahes on 2020-03-29
Hi!

I'm trying Ubuntu 19.10 Live on my Dell Inspirion 5570. I am unable to connect to 5G WiFi network. However, with 2G everything is fine.
I have included journalctl output when trying to connect to 5G WiFi network. Can anyone suggest what to look for? Driver?

Thanks in advance!

```

Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0186] device (wlp3s0): Activation: starting connection 'BAHES_5g' (99b8acf9-61e4-4df3-b5b0-eab06b723509)
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0187] audit: op="connection-activate" uuid="99b8acf9-61e4-4df3-b5b0-eab06b723509" name="BAHES_5g" pid=2141 uid=999 result="success"
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0189] device (wlp3s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0192] manager: NetworkManager state is now CONNECTING
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0197] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0200] device (wlp3s0): Activation: (wifi) access point 'BAHES_5g' has security, but secrets are required.
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0200] device (wlp3s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0203] sup-iface[0x55ec67c54920,wlp3s0]: wps: type pbc start...
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0230] device (wlp3s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0235] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0239] device (wlp3s0): Activation: (wifi) connection 'BAHES_5g' has security, and secrets exist.  No new secrets needed.
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0239] Config: added 'ssid' value 'BAHES_5g'
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0239] Config: added 'scan_ssid' value '1'
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0239] Config: added 'bgscan' value 'simple:30:-80:86400'
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0240] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK'
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0240] Config: added 'auth_alg' value 'OPEN'
Mar 29 15:39:15 ubuntu NetworkManager[1514]: <info>  [1585496355.0240] Config: added 'psk' value '<hidden>'
Mar 29 15:39:15 ubuntu kernel: pcieport 0000:00:1c.5: AER: Corrected error received: 0000:00:1c.5
Mar 29 15:39:15 ubuntu kernel: pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Mar 29 15:39:15 ubuntu kernel: pcieport 0000:00:1c.5: AER:   device [8086:9d15] error status/mask=00000001/00000000
Mar 29 15:39:15 ubuntu kernel: pcieport 0000:00:1c.5: AER:    [ 0] RxErr                 
Mar 29 15:39:18 ubuntu wpa_supplicant[1512]: wlp3s0: SME: Trying to authenticate with 74:4d:28:0c:da:88 (SSID='BAHES_5g' freq=5785 MHz)
Mar 29 15:39:18 ubuntu kernel: wlp3s0: authenticate with 74:4d:28:0c:da:88
Mar 29 15:39:18 ubuntu kernel: wlp3s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
Mar 29 15:39:18 ubuntu kernel: pcieport 0000:00:1c.5: AER: Corrected error received: 0000:00:1c.5
Mar 29 15:39:18 ubuntu kernel: pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Mar 29 15:39:18 ubuntu kernel: pcieport 0000:00:1c.5: AER:   device [8086:9d15] error status/mask=00000001/00000000
Mar 29 15:39:18 ubuntu kernel: pcieport 0000:00:1c.5: AER:    [ 0] RxErr                 
Mar 29 15:39:18 ubuntu kernel: wlp3s0: send auth to 74:4d:28:0c:da:88 (try 1/3)
Mar 29 15:39:18 ubuntu NetworkManager[1514]: <info>  [1585496358.2345] device (wlp3s0): supplicant interface state: scanning -> authenticating
Mar 29 15:39:18 ubuntu NetworkManager[1514]: <info>  [1585496358.2346] device (p2p-dev-wlp3s0): supplicant management interface state: scanning -> authenticating
Mar 29 15:39:18 ubuntu wpa_supplicant[1512]: wlp3s0: Trying to associate with 74:4d:28:0c:da:88 (SSID='BAHES_5g' freq=5785 MHz)
Mar 29 15:39:18 ubuntu kernel: wlp3s0: authenticated
Mar 29 15:39:18 ubuntu kernel: wlp3s0: associate with 74:4d:28:0c:da:88 (try 1/3)
Mar 29 15:39:18 ubuntu NetworkManager[1514]: <info>  [1585496358.2419] device (wlp3s0): supplicant interface state: authenticating -> associating
Mar 29 15:39:18 ubuntu NetworkManager[1514]: <info>  [1585496358.2419] device (p2p-dev-wlp3s0): supplicant management interface state: authenticating -> associating
Mar 29 15:39:18 ubuntu kernel: wlp3s0: RX AssocResp from 74:4d:28:0c:da:88 (capab=0x431 status=18 aid=16383)
Mar 29 15:39:18 ubuntu kernel: wlp3s0: 74:4d:28:0c:da:88 denied association (code=18)
Mar 29 15:39:18 ubuntu wpa_supplicant[1512]: wlp3s0: CTRL-EVENT-ASSOC-REJECT bssid=74:4d:28:0c:da:88 status_code=18
Mar 29 15:39:18 ubuntu wpa_supplicant[1512]: wlp3s0: SME: Deauth request to the driver failed
Mar 29 15:39:18 ubuntu wpa_supplicant[1512]: wlp3s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BAHES_5g" auth_failures=1 duration=10 reason=CONN_FAILED
Mar 29 15:39:18 ubuntu NetworkManager[1514]: <info>  [1585496358.2846] device (wlp3s0): supplicant interface state: associating -> disconnected
Mar 29 15:39:18 ubuntu NetworkManager[1514]: <info>  [1585496358.2847] device (p2p-dev-wlp3s0): supplicant management interface state: associating -> disconnected
Mar 29 15:39:27 ubuntu systemd[1]: systemd-hostnamed.service: Succeeded.
Mar 29 15:39:28 ubuntu kernel: pcieport 0000:00:1c.5: AER: Corrected error received: 0000:00:1c.5
Mar 29 15:39:28 ubuntu kernel: pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Mar 29 15:39:28 ubuntu kernel: pcieport 0000:00:1c.5: AER:   device [8086:9d15] error status/mask=00000001/00000000
Mar 29 15:39:28 ubuntu kernel: pcieport 0000:00:1c.5: AER:    [ 0] RxErr                 
Mar 29 15:39:28 ubuntu NetworkManager[1514]: <info>  [1585496368.2943] device (wlp3s0): supplicant interface state: disconnected -> scanning
Mar 29 15:39:28 ubuntu NetworkManager[1514]: <info>  [1585496368.2944] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> scanning
Mar 29 15:39:29 ubuntu wpa_supplicant[1512]: wlp3s0: CTRL-EVENT-SSID-REENABLED id=0 ssid="BAHES_5g"
Mar 29 15:39:29 ubuntu wpa_supplicant[1512]: wlp3s0: SME: Trying to authenticate with 74:4d:28:0c:da:88 (SSID='BAHES_5g' freq=5785 MHz)
Mar 29 15:39:29 ubuntu kernel: wlp3s0: authenticate with 74:4d:28:0c:da:88
Mar 29 15:39:29 ubuntu kernel: wlp3s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
Mar 29 15:39:29 ubuntu kernel: pcieport 0000:00:1c.5: AER: Corrected error received: 0000:00:1c.5
Mar 29 15:39:29 ubuntu kernel: pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Mar 29 15:39:29 ubuntu kernel: pcieport 0000:00:1c.5: AER:   device [8086:9d15] error status/mask=00000001/00000000
Mar 29 15:39:29 ubuntu kernel: pcieport 0000:00:1c.5: AER:    [ 0] RxErr                 
Mar 29 15:39:29 ubuntu kernel: wlp3s0: send auth to 74:4d:28:0c:da:88 (try 1/3)
Mar 29 15:39:29 ubuntu wpa_supplicant[1512]: wlp3s0: Trying to associate with 74:4d:28:0c:da:88 (SSID='BAHES_5g' freq=5785 MHz)
Mar 29 15:39:29 ubuntu NetworkManager[1514]: <info>  [1585496369.4198] device (wlp3s0): supplicant interface state: scanning -> authenticating
Mar 29 15:39:29 ubuntu NetworkManager[1514]: <info>  [1585496369.4198] device (p2p-dev-wlp3s0): supplicant management interface state: scanning -> authenticating
Mar 29 15:39:29 ubuntu NetworkManager[1514]: <info>  [1585496369.4214] device (wlp3s0): supplicant interface state: authenticating -> associating
Mar 29 15:39:29 ubuntu NetworkManager[1514]: <info>  [1585496369.4214] device (p2p-dev-wlp3s0): supplicant management interface state: authenticating -> associating
Mar 29 15:39:29 ubuntu kernel: wlp3s0: authenticated
Mar 29 15:39:29 ubuntu kernel: wlp3s0: associate with 74:4d:28:0c:da:88 (try 1/3)
Mar 29 15:39:29 ubuntu kernel: wlp3s0: RX AssocResp from 74:4d:28:0c:da:88 (capab=0x431 status=18 aid=16383)
Mar 29 15:39:29 ubuntu kernel: wlp3s0: 74:4d:28:0c:da:88 denied association (code=18)
Mar 29 15:39:29 ubuntu wpa_supplicant[1512]: wlp3s0: CTRL-EVENT-ASSOC-REJECT bssid=74:4d:28:0c:da:88 status_code=18
Mar 29 15:39:29 ubuntu wpa_supplicant[1512]: wlp3s0: SME: Deauth request to the driver failed
Mar 29 15:39:29 ubuntu wpa_supplicant[1512]: wlp3s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BAHES_5g" auth_failures=2 duration=20 reason=CONN_FAILED
Mar 29 15:39:29 ubuntu NetworkManager[1514]: <info>  [1585496369.4609] device (wlp3s0): supplicant interface state: associating -> disconnected
Mar 29 15:39:29 ubuntu NetworkManager[1514]: <info>  [1585496369.4610] device (p2p-dev-wlp3s0): supplicant management interface state: associating -> disconnected
Mar 29 15:39:35 ubuntu xdg-desktop-por[2130]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: App introspection not allowed
Mar 29 15:39:39 ubuntu kernel: pcieport 0000:00:1c.5: AER: Corrected error received: 0000:00:1c.5
Mar 29 15:39:39 ubuntu kernel: pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Mar 29 15:39:39 ubuntu kernel: pcieport 0000:00:1c.5: AER:   device [8086:9d15] error status/mask=00000001/00000000
Mar 29 15:39:39 ubuntu kernel: pcieport 0000:00:1c.5: AER:    [ 0] RxErr                 
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <info>  [1585496379.4617] device (wlp3s0): supplicant interface state: disconnected -> scanning
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <info>  [1585496379.4619] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> scanning
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <warn>  [1585496379.8770] device (wlp3s0): Activation: (wifi) association took too long
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <info>  [1585496379.8771] device (wlp3s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <info>  [1585496379.8782] sup-iface[0x55ec67c54920,wlp3s0]: wps: type pbc start...
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <warn>  [1585496379.8811] device (wlp3s0): Activation: (wifi) asking for new secrets
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <info>  [1585496379.8813] device (wlp3s0): supplicant interface state: scanning -> disconnected
Mar 29 15:39:39 ubuntu NetworkManager[1514]: <info>  [1585496379.8813] device (p2p-dev-wlp3s0): supplicant management interface state: scanning -> disconnected
Mar 29 15:39:39 ubuntu wpa_supplicant[1512]: wlp3s0: WPS-PBC-ACTIVE
Mar 29 15:39:39 ubuntu wpa_supplicant[1512]: wlp3s0: Reject scan trigger since one is already pending
Mar 29 15:39:39 ubuntu wpa_supplicant[1512]: wlp3s0: Failed to initiate AP scan
Mar 29 15:39:40 ubuntu NetworkManager[1514]: <info>  [1585496380.8930] device (wlp3s0): supplicant interface state: disconnected -> scanning
Mar 29 15:39:40 ubuntu NetworkManager[1514]: <info>  [1585496380.8931] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> scanning
Mar 29 15:39:42 ubuntu NetworkManager[1514]: <warn>  [1585496382.2489] device (wlp3s0): no secrets: User canceled the secrets request.
Mar 29 15:39:42 ubuntu NetworkManager[1514]: <info>  [1585496382.2490] device (wlp3s0): state change: need-auth -> failed (reason 'no-secrets', sys-iface-state: 'managed')
Mar 29 15:39:42 ubuntu NetworkManager[1514]: <info>  [1585496382.2504] manager: NetworkManager state is now DISCONNECTED
Mar 29 15:39:42 ubuntu NetworkManager[1514]: <warn>  [1585496382.2557] device (wlp3s0): Activation: failed for connection 'BAHES_5g'
Mar 29 15:39:42 ubuntu NetworkManager[1514]: <info>  [1585496382.2561] device (wlp3s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Mar 29 15:39:42 ubuntu gnome-shell[2141]: An active wireless connection, in infrastructure mode, involves no access point?
Mar 29 15:39:42 ubuntu gnome-shell[2141]: An active wireless connection, in infrastructure mode, involves no access point?
Mar 29 15:39:43 ubuntu NetworkManager[1514]: <info>  [1585496383.2282] device (wlp3s0): supplicant interface state: scanning -> disconnected
Mar 29 15:39:43 ubuntu NetworkManager[1514]: <info>  [1585496383.2283] device (p2p-dev-wlp3s0): supplicant management interface state: scanning -> disconnected
Mar 29 15:39:45 ubuntu kernel: pcieport 0000:00:1c.5: AER: Corrected error received: 0000:00:1c.5
Mar 29 15:39:45 ubuntu kernel: pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Mar 29 15:39:45 ubuntu kernel: pcieport 0000:00:1c.5: AER:   device [8086:9d15] error status/mask=00000001/00000000
Mar 29 15:39:45 ubuntu kernel: pcieport 0000:00:1c.5: AER:    [ 0] RxErr



```

---

### Post by wildmanne39 on 2020-04-01
*Thread moved to **Networking & Wireless for a more appropriate fit**.* after being contacted on facebook.

Hi, please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created.

---

### Post by Boris_Bahes on 2020-04-02
> **wildmanne39 said:**
> *Thread moved to **Networking & Wireless for a more appropriate fit**.* after being contacted on facebook.

Hi, please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created.

Hi!

Here is output from script: [https://paste.ubuntu.com/p/gMKF4zWkZP/](https://paste.ubuntu.com/p/gMKF4zWkZP/)

---

### Post by chili555 on 2020-04-02
The access point you want to connect to is this:

```
BAHES_5g                        <MAC 'BAHES_5g' [AC9]>  Infra  [COLOR="#FF0000"]157[/COLOR]   5785 MHz  270 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
```As you see, it is broadcasting on channel 157.

Your wireless device reports this:

```
<snip>
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
```Channel 157 is not listed.

The available channels are regulated by each country, so you may be helped by setting your correct country code or regulatory domain. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

After setting yours, check again:

```
sudo iwlist chan
```

Is 157 now available? If not, I suggest that you change the channel in the router to 140.

---

### Post by Boris_Bahes on 2020-04-05
> **chili555 said:**
> The access point you want to connect to is this:

```
BAHES_5g                        <MAC 'BAHES_5g' [AC9]>  Infra  [COLOR=#FF0000]157[/COLOR]   5785 MHz  270 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
```As you see, it is broadcasting on channel 157.

Your wireless device reports this:

```
<snip>
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
```Channel 157 is not listed.

The available channels are regulated by each country, so you may be helped by setting your correct country code or regulatory domain. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

After setting yours, check again:

```
sudo iwlist chan
```

Is 157 now available? If not, I suggest that you change the channel in the router to 140.

Thanks for your assistance!

As you suggested I had to change channel in order to connect to 5G WiFi. I changed channel to 44 (5220) and client eventually connected.
Changing region via /etc/default/crda or sudo iw reg set HR didn't help. Do I have to restart OS to this take effect?

Which brings me to one more question. Is this exptected behavior of OS? Not to connect on channel out of regional regulations? For example I had no problem to connect to channel 157 on Windows 10 client.

Thanks again!

---

### Post by chili555 on 2020-04-05
This provides some useful information: [https://wireless.wiki.kernel.org/en/developers/Regulatory/CRDA](https://wireless.wiki.kernel.org/en/developers/Regulatory/CRDA) and this: [https://en.wikipedia.org/wiki/List_of_WLAN_channels](https://en.wikipedia.org/wiki/List_of_WLAN_channels)

> Nations apply their own RF emission regulations to the allowable channels, allowed users and maximum power levels within these frequency ranges.I am confident that nations regulate RF emissions, including and especially wifi, because they don't want microwaves and light dimmers and airport radar and police radio and wifi to all simultaneously compete.

I have no explanation as to why Windows evidently doesn't respect it. It is the case that a great many things work well in Linux and not Windows and vice-versa.

> 
Changing region via /etc/default/crda or sudo iw reg set HR didn't help. 
Do you mean that it didn't help connectivity or that it doesn't persist when you again run:

```
sudo iw reg get
```

---

### Post by Boris_Bahes on 2020-04-06
>  have no explanation as to why Windows evidently doesn't respect it. It is the case that a great many things work well in Linux and not Windows and vice-versa.

I was interested to know how does Linux behave in these situations. Windows example was just for comparison.


> Do you mean that it didn't help connectivity or that it doesn't persist when you again run:

It didn't help connectivity.

---

### Post by praseodym on 2020-04-06
What device/driver is in use? It may not work with the mac80211 subsytem, but with cfg80211. Please show
```

lspci -nnk
lsusb
lsmod
```

---

### Post by Boris_Bahes on 2020-04-07
> **praseodym said:**
> What device/driver is in use? It may not work with the mac80211 subsytem, but with cfg80211. Please show
```

lspci -nnk
lsusb
lsmod
```

Here is output: [http://paste.ubuntu.com/p/ZtksM3zXQS](http://paste.ubuntu.com/p/ZtksM3zXQS)

---

