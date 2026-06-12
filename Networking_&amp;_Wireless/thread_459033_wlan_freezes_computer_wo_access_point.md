---
title: "wlan freezes computer w/o access point"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by gyeti on 2007-05-30
I have a weird problem with my wlan on a Thinkpad x40 running ubuntu dapper. I recently managed to get wpa_supplicant working but now my machine freezes when the access point is not found. It dies without leaving any info in the log messages. I always have to run "sudo ifdown ath0" before leaving home, which is kind of inconvenient. Does anybody have experience with a problem similar to that?

Here is the wpa_supplicant.conf I'm using:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
#
network={
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="dummy passphrase"
}

network={
        ssid="real essid"
        scan_ssid=1
        proto=WPA
        pairwise=TKIP
        group=TKIP
        eap=TLS
        key_mgmt=WPA-PSK
        psk="very secret real passphrase"
}

The first network block I included in the hope to solve the problem but it didn't help either.

Does anybody have an idea?

cheers,
gyeti

---

