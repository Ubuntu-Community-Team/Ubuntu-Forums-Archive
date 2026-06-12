---
title: "wpa_supplicant: No internet when using inet manual and wpa-roam"
date: 2016-02-20
forum: Networking &amp; Wireless
---

### Post by anthony95 on 2016-02-20
Hi, first post and also first time Linux user. Like many others I've seen online I am having trouble manually setting up wifi on my machine. I did a minimal install of Ubuntu Server 14.04 and then installed wpasupplicant and wireless-tools. I'm now trying to set up wifi by editing /etc/network/interfaces and /etc/wpa_supplicant/wpa_supplicant.conf but am experiencing a weird problem in which I can't connect to the internet (no IP, can't ping any addresses, including my router) when I use *inet manual* and *wpa-roam* in the following configuration:

```

# /etc/network/interfaces

allow-hotplug wlan0
iface wlan0 **inet manual**
**wpa-roam** /etc/wpa_supplicant/wpa_supplicant.conf

iface default inet dhcp

```

```

# /etc/wpa_supplicant/wpa_supplicant.conf

ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="MySSID"
    proto=WPA2
    key_mgmt=WPA-PSK
    psk="MyPassword"
}

```

However the internet *does* work (can ping addresses, etc.) when I set /etc/network/interfaces like so:

```

allow-hotplug wlan0
iface wlan0 inet **dhcp**
wpa-**conf **/etc/wpa_supplicant/wpa_supplicant.conf

```

As you can see, in both configurations I am specifying dhcp, but on the first one I'm using *inet manual*, *wpa-roam*, and specifying dhcp for any networks without a str_id in wpa_supplicant.conf (i.e., default networks). I can't think of a reason why the second dhcp configuration would work but not the first. Unless maybe wpa_supplicant.conf isn't correctly telling /etc/network/interfaces to use the default network settings? Or maybe I am missing a required package?

I'd appreciate any help... FWIW, I don't want to use the second configuration because I want to set up static IP's for home and work networks, and use dhcp by default. As far as I can tell, I need to use *inet manual* for that.

---

