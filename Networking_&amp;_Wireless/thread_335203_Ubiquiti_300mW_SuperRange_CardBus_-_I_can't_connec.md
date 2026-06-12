---
title: "Ubiquiti 300mW SuperRange CardBus - I can't connect to my AP with it"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by tee2 on 2007-01-10
I'm stumped, so maybe someone sees something I've missed.

Here is my iwconfig output (the ubiquiti card is ath0, the eth1 card is my laptop's built in card)
```
tee@tee-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksysR7a40a2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:7A:40:A2   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/100  Signal level=-78 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:8

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys_SES_38666"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:38255  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

here is my interfaces file
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant.conf
wpa-ssid linksys_SES_38666
post-down killall -q wpa_supplicant

auto wlan0
iface wlan0 inet dhcp


```

and here is my wpa_supplicant.conf file
```
ctrl_interface=/var/run/wpa_supplicant

ap_scan=2

network={
       ssid="linksys_SES_38666"
       key_mgmt=WPA-PSK
       proto=WPA
       pairwise=TKIP
       group=TKIP
       psk="xxxxxxxxxxxxxxxxx"
}

```

---

