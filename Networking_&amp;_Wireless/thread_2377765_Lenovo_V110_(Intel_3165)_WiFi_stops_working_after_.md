---
title: "Lenovo V110 (Intel 3165) WiFi stops working after several minutes, Lubuntu 17.10"
date: 2017-11-16
forum: Networking &amp; Wireless
---

### Post by pullingmyhairout on 2017-11-16
Hello.
My Wifi connection works only for a couple of minutes, then stops (no packets go through, no new messages in kernel log).
Sometimes it recovers on its own, most of the time I need to issue manual reconnect to the wifi adapter.
No other devices (laptops and smartphones) have had problems with this access point.

System info:
Lenovo V110 laptop, Lubuntu 17.10 (upgraded from 17.04, which did not work in exactly the same way).
Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth
the rest (network script output) is here: [http://paste.ubuntu.com/25974928/](http://paste.ubuntu.com/25974928/)

What I tried (nothing worked):
options iwlwifi 11n_disable=1  (my AP doesnt support "n" anyways)
options iwlwifi bt_coex_active=N
options iwlwifi swcrypto=1
options iwlmvm power_scheme=1
options iwlwifi power_save=N (and it's already disabled by default)
all these options together
using other firmware versions my module could load: iwlwifi-7265D-29.ucode (default), iwlwifi-7265D-27.ucode, iwlwifi-7265D-22.ucode
(all of the above with reloading wifi kernel modules and reconnecting to the AP)
disabling ipv6
explicitly setting regulatory domain for my country

Please help me make this piece of fine Intel equipment work if it's possible at all.

---

### Post by jeremy31 on 2017-11-17
Have you tried ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot, some of these wireless devices don't like it when Network Manager tries to enable power management

---

### Post by pullingmyhairout on 2017-11-21
Yes, there was a "2" already, looks like I did it at some point and then forgot to add to the list of stuff I tried.

---

### Post by Hadaka on 2017-11-21
Hi, from the wireless diagnostic report..
*LSMOD shows 3 different wmi modules loaded..
```
wmi  3 wmi_bmof,peaq_wmi,ideapad_laptop
```
*To correct please do..
```
sudo rm -rf bmof_wmi
sudo rm -rf peaq_wmi
echo "blacklist bmof_wmi\nblacklist peaq_wmi"| sudo tee -a /etc/modprobe.d/blacklist-wmi.conf
```

**DMESG**
```
[  220.380791] wlp2s0: authenticate with <MAC 'Honeypot' [AC1]>
[  220.383446] wlp2s0: send auth to <MAC 'Honeypot' [AC1]> (try 1/3)
[  220.398860] wlp2s0: authenticated
[  220.399756] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  220.399760] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
```
*Is a result of the country code not being defined in " /etc/default/crda "
*Region: Europe/Moscow (based on set time zone) is shown in the diagnostic report.
***country 00: DFS-UNSET*** To correct please do..
```
sudo iw reg set RU
sudo sed -i 's/=.*/=RU/' /etc/default/crda
```
boot and test wireless
** You state ..
"What I tried (nothing worked)
options iwlwifi 11n_disable=1  ([COLOR=#ff0000]My AP doesnt support "n" anyways[/COLOR])"
If the AP doesnt support 802.11 n HT..(high throughput), then it is not likely
going to support 802.11 AC VHT..(very high throughput). Sounds like your
Intel card is cranking out data faster than your AP can process.

---

