---
title: "Wireless connection problems"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by plehman on 2005-11-16
Hi all,

I have a Dell Inspiron 5150 laptop with an Intel Pro/Wireless 2200 card installed.  I was able to get wpa_supplicant installed and all, but for some reason, I am having a problem getting it to automatically connect...

If I boot the machine and log-in (after a large timeout for setting up network connections during boot), in order to get my wireless card to connect to my access point, I have to execute the following in a terminal:

```
sudo dhclient eth1
```

Likewise, if I am on a wired network, then disconnect, the network-manager applet asks me for the passcode, but in the end it fails.  It seems that my problem may be related to DHCPOFFER because if I try the following at the command line:

```
sudo ifup eth1
```

it constantly is looking at varying intervals 

```
DHCPDISCOVER on eth1 to 255.255.255.255 port 67
```

messages, but never an IP address being assigned.  This is why I ultimately have to run dhclient to grab an IP address.  The contents of my /etc/wpa_supplicant.conf file are listed below:

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid=<<REMOVED>>
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=<<LARGE HEX STRING, REMOVED FOR READABILITY>>
}

```

Any ideas on how to fix this?

---

