---
title: "Intel Ultimate-N 6300"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by daniel.j.crise on 2014-01-06
I have installed Ubuntu 12.04 and it was connecting just fine at my parents place over the break. I have recently moved back to my place and the wireless internet will not connect. I have absolutely no clue why this is happening. It recognizes several different wireless connection in the area but when I attempt to connect to mine it just keeps trying and keeps asking for my password. I am running a dual boot system with Ubuntu and Windows 7. I can connect just fine using Windows 7 but not Ubuntu. My computer is a HP Envy with a Intel(R) Centrino(R) Ultimate-N 6300 AGN. I consider myself a little computer illiterate and am stuck. Need to fix this asap as I have some programming I need to complete. Thank you!

---

### Post by chili555 on 2014-01-06
Please open a terminal and confirm your wireless device:```
lspci -nn
```If it is indeed an Ultimate-N 6300 AGN, please do:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us have your report.

---

### Post by daniel.j.crise on 2014-01-06
I have done everything you asked. It was a Ultimate-N 6300 so I continued with what you said and absolutley nothing happened after rebooting. Thank you for responding so fast.

---

### Post by chili555 on 2014-01-06
Are there any clues in the message log?```
dmesg | grep iwl
```

---

### Post by daniel.j.crise on 2014-01-06
This is what gets printed out:
[   18.211377] iwlwifi 0000:09:00.0: irq 62 for MSI/MSI-X
[   21.993860] iwlwifi 0000:09:00.0: loaded firmware version 9.221.4.1 build 25532
[   23.715194] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   23.715199] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   23.715201] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   23.715202] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   23.715204] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_P2P disabled
[   23.715207] iwlwifi 0000:09:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   23.715264] iwlwifi 0000:09:00.0: L1 Enabled; Disabling L0S
[   24.322064] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.408829] iwlwifi 0000:09:00.0: L1 Enabled; Disabling L0S
[   28.415468] iwlwifi 0000:09:00.0: Radio type=0x0-0x3-0x1
[   28.776097] iwlwifi 0000:09:00.0: L1 Enabled; Disabling L0S
[   28.782737] iwlwifi 0000:09:00.0: Radio type=0x0-0x3-0x1

---

### Post by chili555 on 2014-01-06
Nothing wrong there. Anything here?```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```

---

### Post by daniel.j.crise on 2014-01-06
Again, thank you for your time and helping me with this issue. The next part printed this:
Jan  6 16:59:19 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan  6 16:59:26 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  6 16:59:26 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  6 16:59:29 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan  6 16:59:29 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Jan  6 16:59:29 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  6 16:59:29 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: associating -> associated
Jan  6 16:59:29 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan  6 16:59:33 ubuntu NetworkManager[1107]: <warn> Activation (wlan0/wireless): association took too long.
Jan  6 16:59:33 ubuntu NetworkManager[1107]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  6 16:59:33 ubuntu NetworkManager[1107]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan  6 16:59:33 ubuntu NetworkManager[1107]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  6 16:59:33 ubuntu NetworkManager[1107]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan  6 16:59:58 ubuntu NetworkManager[1107]: <warn> No agents were available for this request.
Jan  6 16:59:58 ubuntu NetworkManager[1107]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan  6 16:59:58 ubuntu NetworkManager[1107]: <warn> Activation (wlan0) failed for access point (E17787)
Jan  6 16:59:58 ubuntu NetworkManager[1107]: <info> Marking connection 'E17787' invalid.
Jan  6 16:59:58 ubuntu NetworkManager[1107]: <warn> Activation (wlan0) failed.
Jan  6 16:59:58 ubuntu NetworkManager[1107]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan  6 16:59:58 ubuntu NetworkManager[1107]: <info> (wlan0): deactivating device (reason 'none') [0]

---

### Post by chili555 on 2014-01-06
>  Marking connection '[COLOR="#FF0000"]E17787[/COLOR]' invalid.I assume this is your home network and not that of your parents. I suggest you right-click the Network Manager icon and select Edit Connections, select Wireless and be certain that only your home network appears. If others appear, delete them. Also check to see which password is stored; home or parents. [http://i.stack.imgur.com/boOI0.jpg](http://i.stack.imgur.com/boOI0.jpg)

Again, I see nothing remarkable in your logs; it just tries to connect and fails.

---

### Post by daniel.j.crise on 2014-01-06
Ok. Thank you for your time.

---

