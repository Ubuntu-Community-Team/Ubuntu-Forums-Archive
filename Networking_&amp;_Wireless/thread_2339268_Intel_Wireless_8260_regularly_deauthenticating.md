---
title: "Intel Wireless 8260 regularly deauthenticating"
date: 2016-10-06
forum: Networking &amp; Wireless
---

### Post by killian-widdis on 2016-10-06
This problem is occurring only at my workplace, which has two networks, one  2.4GHz and one 5GHz (problem occurs on both). Every 10 to 30 minutes I lose connectivity for a few minutes (or until I reconnect to the network). I've noticed that when this happens all other networks disappear from the list of available connections.

The corresponding log in dmesg (which doesn't always show up when connection cuts out) indicates that my machine is deauthenticating for some reason.

```

[Oct 6 11:31] wlp4s0: deauthenticating from c0:56:27:41:ef:5f by local choice (Reason: 3=DEAUTH_LEAVING)
[  +0.925403] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[  +0.001350] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[  +0.138078] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[  +0.000575] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[  +0.081349] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[  +0.061993] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[  +3.089347] wlp4s0: authenticate with c0:56:27:41:ef:5f
[  +0.009205] wlp4s0: send auth to c0:56:27:41:ef:5f (try 1/3)
[  +0.004826] wlp4s0: authenticated
[  +0.002966] wlp4s0: associate with c0:56:27:41:ef:5f (try 1/3)
[  +0.001484] wlp4s0: RX AssocResp from c0:56:27:41:ef:5f (capab=0x411 status=0 aid=1)
[  +0.001633] wlp4s0: associated
[  +0.000045] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
[  +0.092040] wlp4s0: Limiting TX power to 27 (30 - 3) dBm as advertised by c0:56:27:41:ef:5f

```

So far, I've tried disabling power saving and ipv6, but neither of these had any effect and the latter just silenced all errors in dmesg. I'm attaching the output of the wireless-info script, if anyone has any idea what might be going wrong or how I can go about debugging this I would greatly appreciate the help!

---

### Post by chili555 on 2016-10-06
First, I suggest that you upgrade the firmware; from the terminal:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux*.deb
```
Then set your regulatory domain explicitly. Check yours:

```
sudo iw reg get
```
If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

```
sudo iw reg set IS
```
Of course, substitute your country code if not Iceland. Set it permanently:

```
gksudo gedit /etc/default/crda
```
Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

```
REGDOMAIN=IS
```
Proofread carefully, save and close the text editor.

If these changes do not help, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

Reboot and let us know if connectivity is improved.

---

### Post by killian-widdis on 2016-10-06
Neither the regulatory domain nor the 11n_disable setting seem to have done much, I'm still getting disconnected. I did however figure out that the dmesg snippet I pasted is actually just the result of me manually deauthenticating by turning WiFi on and off... kind of a facepalm moment but live and learn. Thanks for the help though, and let me know if you have any more ideas. I'm going  to keep trying to figure this out but am not sure where to look for the problem.

---

### Post by chili555 on 2016-10-06
Just in the interest of completeness, or maybe I'm a nervous nellie, did you try a reboot?

You might also try:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the last line from:```
options iwlwifi 11n_disable=8
```To:```
options iwlwifi swcrypto=1
```Proofread carefully, save and close the text editor. Reboot.

To try to capture the reason for the disconnects, wait until it does and then run:```
dmesg
```Or else:```
cat /var/log/syslog
```Look at the last ten lines or so; copy and paste them into a text document and post them here.

---

### Post by killian-widdis on 2016-10-07
I've rebooted with the country code set, as well as both 11n_disable and  swcrypto -- no luck. Unfortunately there's nothing pertinent in dmesg,  and nothing that jumps out at me from syslog but I'll paste output from the 20-ish minutes before I lost connection:
```
Oct  7 14:05:01 augur CRON[5835]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct  7 14:08:26 augur wpa_supplicant[1991]: wlp4s0: WPA: Group rekeying completed with c0:56:27:41:ef:5e [GTK=CCMP]
Oct  7 14:13:16 augur org.gnome.ScreenSaver[2530]: (gnome-screensaver:2694): GLib-CRITICAL **: Source ID 295 was not found when attempting to remove it
Oct  7 14:15:01 augur CRON[7098]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct  7 14:17:01 augur CRON[7348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  7 14:22:02 augur systemd-timesyncd[1642]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Oct  7 14:22:12 augur systemd-timesyncd[1642]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Oct  7 14:25:01 augur CRON[8446]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct  7 14:35:01 augur CRON[9772]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
```

---

### Post by chili555 on 2016-10-08
I'm sorry that I haven't further suggestions. We see no clues that lead us to a possible solution.

---

