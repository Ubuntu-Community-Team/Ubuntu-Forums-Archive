---
title: "wpa_supplicant won't start with preup"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2007-01-09
hi,

i've got my wpa_supplicant.conf configured how i think it should. It looks like this:

```
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="ssid"
scan_ssid=1
proto=WPA
# key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk=psk
}
```My /etc/network/interfaces spells```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
preup wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -wB
post-down killall -q wpa_supplicant

auto wlan0
iface wlan0 inet dhcp

auto eth0
```but when ubuntu dpaer drake LTS starts, it doesn't connect. First I have to manually do ```
sudo wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -wB
```and then select the network with thre WifiRadar. But often these two lasts staps don't suffice, and i have to start the terminal session with a ```
sudo rm /var/run/wpa_supplicant/ath0 
```this all doesn't make me very happy, because it took me a day to find out, and its my friends laptop, who propbably won't like ubuntu as much without a ready to go wlan. So what am I missing?
I also have Wireless Assistant installed, but it doesn't help out much with encrypted networks. And sometimes I seem to need to run the wpa_gui inbetween the wpa startup and the Wireless radar.

Is there a way to have this all automated. And I also still want the  laptop to adcces other (secured) networks. Is Edgy better at it?

---

### Post by Mujaheiden on 2007-01-17
Okay, starting at the beginning of the forum solved my problem. admin pleaze delete. I still have difficulties navigating ubuntu forums :)

---

