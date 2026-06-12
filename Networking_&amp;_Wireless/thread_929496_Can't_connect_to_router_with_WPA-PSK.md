---
title: "Can't connect to router with WPA-PSK"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Ursidae on 2008-09-25
I'm having problems connecting to my wireless router that is using WPA-PSK security. I can connect to unprotected wireless networks though.

Here's what /etc.network/interfaces looks like
iface ath0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
wpa-psk ****
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid RKRQEAGGW

auto atho

It was working fine for months, but now the only way I seem to be able to see my router now is by enabling roaming on the wireless connection. It says I'm connected, but when I look on my router, I'm not connected.
Other pcs running xp connect fine.
Can anyone offer some ideas as to where I can start looking to try and figure this out? 
Thanks.

---

### Post by willca on 2008-09-25
Check if you got wpa_supplicant installed.

sudo dpkg -l | grep wpa

ii  wpasupplicant                          0.6.0+0.5.8-0ubuntu2           Client support for WPA and WPA2 (IEEE 802.11

If not,
sudo apt-get install wpa_supplicant

Create a file called /etc/wpa_supplicant.conf, and paste in the following. Modify the ssid and psk values. 

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="YourWiFiSSID"
   psk="YourWiFiPassword"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }

Then test if it works.
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

If all good...

Edit /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

Then restart networking 
sudo /etc/init.d/networking restart

Verify.
sudo iwlist wlan0 scan

---

