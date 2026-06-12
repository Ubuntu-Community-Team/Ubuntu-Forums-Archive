---
title: "Annoying laptop bug"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by ukch on 2008-01-21
I have a laptop with a Belkin PCMCIA wireless network card using the RT2500 chipset. Originally, I had great trouble in getting this card to work at all, but upon upgrading my system about a year ago the problem was fixed.

However, since upgrading to Gutsy in September, a minor but annoying problem has appeared. Basically, no matter what my network settings, my computer refuses to connect to my Wireless network on boot, and will not connect until I restart the networking using 'sudo /etc/init.d/networking restart'. I have to do this every time I reboot my computer or return from suspend. I suspect the problem may have something to do with the correct drivers being loaded after the network tries to set itself up, but have no idea how to test this theory. Here is my /etc/network/interfaces (with the SSID and network key blanked out, of course). It was created using the System>Administration>Network tool:

```
iface ra0 inet dhcp
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid xxxxxxxxxxxx
```

Please let me know what else I need to provide to figure out what the problem is.

---

### Post by ukch on 2008-01-25
When booting my laptop today, I noticed the following message:

```
modprobe: WARNING: Error inserting iwlwifi_rc80211_simple (/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_rc80211_simple.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Well, first of all, I checked, and the file is definitely there. Then I tried dmesg, which gave me the following information, among other things:

```
...
[   28.924000] ieee80211_init: failed to initialize WME (err=-17)
[   28.940000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_con
trol_unregister
[   28.940000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   28.940000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   28.940000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_con
trol_register
...
```

Anyone know what this means? Is it a bug, or what? Should I report it?

---

### Post by mc87 on 2008-02-06
I've got the same message at startup and the same output in dmesg. When I installed the wireless card it worked  right away and connected to the internet, but it will disconnect during large file downloads. I was thinking about trying to install the drivers from the website, but am worried this will only make things worse. Any ideas?

---

