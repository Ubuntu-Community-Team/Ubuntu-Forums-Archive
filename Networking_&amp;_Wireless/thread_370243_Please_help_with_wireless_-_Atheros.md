---
title: "Please help with wireless - Atheros"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by toddhd on 2007-02-25
Hi All:
I installed Ubuntu 6.10, and am trying to connect to my wireless. My PC has an Atheros based network card. My router is an ActionTec MI424WR courtesty of Verizon FIOS. I have it setup to use WPA-PSK with an ASCII based key.

I went into network settings and enabled my card. It asked me to supply my SSID, key type (ascii) and key, which I did. I left all things related to DHCP set to auto. But nothing ever happens, I don't get a network connection. 

I saw this post on the forums, but it doesn't seem to help:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=202834&highlight=madwifi)

I tried searching the forums too, I'm just lost. Nothing seems relevent and/or works.

Here are the contents of my networking file. I've been playing with various settings based on different posts, so I have no idea now what to do. Maybe this will help. I removed my security key values of course.
==================================

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid SeaburyDesign
wireless-key s:<my key in ascii>

auto wlan0
iface wlan0 inet dhcp
wpa-driver madwifi
wpa-conf managed
wpa-ssid SeaburyDesign
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my ascii key encoded>
===========================

Any help would be greatly appreciated.

---

### Post by spd106 on 2007-02-25
To aid wireless configuration the interfaces file comes pre-filled with many interface stanza, even though it is very unlikely that you will need all of them.

You can see which interfaces you actually have in the network-admin capplet aka System -> Admin -> Networking.

If you compare the two you will probably find that no wlan0. So if you copy all of the lines you added under wlan0 to the stanza for ath0 it should work. I also recommend that you use the wext driver rather than madwifi. Don't forget to generate a hex key.

The lines with the wireless- pre-fix are for WEP, so you won't need them.

It should look like this
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid SeaburyDesign
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my hex key>

auto wlan0
iface wlan0 inet dhcp
```

You might also want to consider installing Network Manager, unless you need WPA-Enterprise (see [https://wiki.ubuntu.com/WifiDocs/NetworkManager](https://wiki.ubuntu.com/WifiDocs/NetworkManager))

---

### Post by toddhd on 2007-02-25
Thanks for the response. I changed my interfaces file to match exactly what you have above, but still no network. I also tried swtiching the wpa-driver from wext to madwifi, and wpa-pairwise and wpa-group to TKIP, just in hopes of hitting the right recipe for success - no go.

Based on other discussions, I ran the following:

todd@basement:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

todd@basement:~$ iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:15:05:EE:44:EE
                    ESSID:"SeaburyDesign"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

sit0      Interface doesn't support scanning.

Does that help any?

Oh, and I tried installing network manager, and it gives an error. 'Network manager cannot be installed on your computer type (i386)'. I'm not sure why I'm getting that. I am running a clean, new install of Ubuntu 6.10 32bit on a pretty standard PC. I previously had Mandriva installed on this PC and ran fine, including the network, so I'm certain that my hardware is Linux compatible. 

Again, any help is appreciated.

---

