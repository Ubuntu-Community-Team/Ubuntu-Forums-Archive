---
title: "how do you enable wpa in network manager"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by Tethylis on 2007-08-13
Hey, I am trying to enable wpa using wpa supplicant in network manager but having no luck. I have a ralink rt2500.

     -Here is what I have in my /etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel

network={
      ssid="CrashBox"
      scan_ssid=1
      key_mgmt=WPA-PSK
      psk="blahblahblah"
}

     -This is what I have in my /etc/network/interfaces

auto lo
iface lo inet dhcp

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface ra0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid CrashBox
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto ra0

What else do I have to do to enable wpa in network manager? Im pretty new to linux overall so any help would be greatly appreciated ^^

---

