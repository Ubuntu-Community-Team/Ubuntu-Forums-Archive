---
title: "Need some help with WPA too :-)"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by tiger's on 2007-06-27
Hello!

I've got a Zcom WiFi card (based on TI ACX111) and Dlink or Zyxel drivers (works fine in WinXP). I've got a Kubuntu/Xubuntu 7.04 and self-compiled ndiswrapper.

Also I've got a following logs:

```
[   25.292000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   25.400000] ndiswrapper: driver gplus (D-Link,04/09/2004,6.0.0.18) loaded
[   25.984000] ndiswrapper: using IRQ 11
[   26.520000] wlan0: ethernet device 00:60:b3:d8:12:2b using NDIS driver: gplus, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
[   26.520000] wlan0: encryption modes supported: WEP; TKIP with WPA
[   26.520000] usbcore: registered new interface driver ndiswrapper 
```

```
ndiswrapper -l
gplus : driver installed
        device (104C:9066) present (alternate driver: acx) 
```

```
iwconfig
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr=4096 B   Fragment thr=4096 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

```
iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 02:19:5B:C2:09:9C
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK 
```

```
/etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid My_AP
wpa-ap-scan 2
wpa-proto RSN WPA
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 83b2897b20a2ccfeaff34ecc596b1d67d9fb568188ad3e2ae5fe1ab703ab359b 
```

But nothing works yet... May be someone have ideas?

Thanks a lot!

---

### Post by kevdog on 2007-06-27
Im not making any assumptions, but with the info you provided above it looks like the driver only supports WPA version1 and not version 2.  Im assuming on the router you have chosen WPA-PSK wtih TKIP algorithm, (no WPA2), and then entered your key. 

Why dont you try this:
/etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid My_AP
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 83b2897b20a2ccfeaff34ecc596b1d67d9fb568188ad3e2ae5fe1ab703ab359b

Let me know what happens!

---

### Post by tiger's on 2007-06-27
> **kevdog said:**
> Im not making any assumptions, but with the info you provided above it looks like the driver only supports WPA version1 and not version 2.  Im assuming on the router you have chosen WPA-PSK wtih TKIP algorithm, (no WPA2), and then entered your key. 

Why dont you try this:
/etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid My_AP
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 83b2897b20a2ccfeaff34ecc596b1d67d9fb568188ad3e2ae5fe1ab703ab359b

Let me know what happens!

Hey, man! Thank's a lot! 

I thought that after NIC have failed to use WPA2 it would try WPA1 (next on list). So, your config works, only need to add "wpa-ap-scan 2" string because SSID is hidden.

So, problem solved.

---

