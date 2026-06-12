---
title: "TP-Link TL-WN722N USB wireless adapter-SOLUTION"
date: 2015-07-28
forum: Networking &amp; Wireless
---

### Post by atux on 2015-07-28
Dear all. i am writing this post just to share my experience and solution of the TP-Link TL-WN722N USB and how to make it work.
i am using ubuntu server 12.04 and it works in newer versions as well, out if the box.
The steps that i have followed are:
-apt-get update, apt-get upgrade
-plug the usb adapter
-apt-get install wireless-tools usbutils 
-edit the file /etc/network/interfaces and add a section for the wifi. if you have only one wifi it gets recognised as wlan0. verify with dmesq
auto wlan0
iface wlan0 inet dhcp[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        wpa-ssid "SSID_name"[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        wpa-psk "passwd_wifi"[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]
-issue iwconfig in the command line and if you see the
...
wlan0     IEEE 802.11bgn  ESSID:off/any
            Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Encryption key:off
            Power Management:off
...
you are good to go.

-scan for network name only with the command  iwlist wlan0 scan | grep ESSID
-if unsuccessful then reboot and try again.

---

