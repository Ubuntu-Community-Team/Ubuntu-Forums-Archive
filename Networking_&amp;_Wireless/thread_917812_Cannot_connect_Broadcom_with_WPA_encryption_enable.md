---
title: "Cannot connect Broadcom with WPA encryption enabled"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by natrone on 2008-09-12
:confused:I am using a Broadcom BCM94306 Wireless LAN Controller (rev 02).  Trust me I know the issues with Broadcom cards and their non-seamless operation in Linux (no fault of Linux).  It has been such an issue that I am about to junk my HP laptop and buy one that does not incorporate Broadcom into the system.  I was finally able to get the card functioning with no encryption enabled using ndiswrapper.  As soon as I enable WPA on the router and then in network-manager on the laptop I cannot achieve connection.  WPA Supplicant is installed and I tried to configure it following the WPAHowTo in the wiki and numerous posts (I emphasize NUMEROUS) to no avail.  Any help would be greatly appreciated.  Below is one post I followed and my /etc/network/interfaces and /etc/wpa_supplicant.conf entries:

[http://ubuntuforums.org/showthread.php?t=227331]("http://ubuntuforums.org/showthread.php?t=227331")

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto wlan 0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid "MySSID"
wpa-ap-scan 1
wpa-proto TKIP
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk "MyPSK"

/etc/wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="MySSID"
        scan_ssid=1
        proto=TKIP
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="MyPSK"

---

