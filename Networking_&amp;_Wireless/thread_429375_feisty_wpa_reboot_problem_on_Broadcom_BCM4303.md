---
title: "feisty wpa reboot problem on Broadcom BCM4303"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by remi71 on 2007-05-01
Hi

After upgrade from edgy to feisty my wpa configuration do not work after a reboot, but just work fine if i do:

```

ifdown wlan0 && ifup wlan0

```

My wi-fi nic chipset is Broadcom BCM4303, i use ndiswrapper module.
I've the following /etc/network/interfaces configuration:

```

auto wlan0

iface wlan0 inet static
        address         192.168.2.13
        netmask         255.255.255.0
        broadcast       192.168.2.255
        network         192.168.2.0
        gateway         192.168.2.1

        ### WPA WIRELESS SECTION ##################################################################

        # WPA DRIVER 'wext' is a generic driver that is applicable when using "ndiswrapper"
        wpa-driver wext

        # Network SSID
        wpa-ssid startrek.space

        # AP Scan Type: "1" Broadcast of ESSID, "2" Hidden Broadcast of ESSID
        wpa-ap-scan 2

        # WPA Protocol version: "WPA" version 1, "RSN" version 2
        wpa-proto WPA

        # WPA Pairwise: "TKIP" wpa version 1, "AES" wpa version 2
        wpa-pairwise TKIP

        # WPA Group: "TKIP" wpa version 1, "AES" wpa version 2
        wpa-group TKIP

        # WPA Key Management: "WPA-PSK" authentication via pre-shared key, "WPA-EAP" authentication via enterprise authentication server
        wpa-key-mgmt WPA-PSK

        # WPA Pre-Shared Key: Key for authentication (use wpa_passphrase <ssid> [passphrase] to generate it)
        wpa-psk 7aaa4150f7f38911c51080ce218b799edf283ac8cfd25cae3016aca6a08dc824

        ### END WPA WIRELESS SECTION ##################################################################

```

Any suggestion?

Thanks

---

