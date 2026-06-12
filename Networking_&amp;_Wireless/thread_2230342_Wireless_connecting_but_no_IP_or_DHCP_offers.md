---
title: "Wireless connecting but no IP or DHCP offers"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by Al_Lougher on 2014-06-18
Hey all

First time here, hoping someone can help. I have very *limited* knowledge of Ubuntu and only use it for my XBMC server which I've been running for 3+ years without any issue. I've lately had to move from a hard LAN connection to my router to a wireless connection utilizing a WUSB600N adapter. I had this adapter working fine a long time ago on another router but this weekend bought a new router and now having issues getting it to connect, and stay connected.

Essentially, what is happening is it seems to connect to the router OK. iwconfig shows the connection and in my router admin panel I see the MAC address of the adapter show up, but it shows up as 0.0.0.0 IP address then it disconnects. 

Here's what I have in my interfaces config (note if you see typos it's because I'm manually typing this in):

```

auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.0.108
netmask 255.255.255.0
gateway 192.168.0.1

wpa-driver wext
wpa-ssid "My_HomeNetwork_5G"
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-PSK
wpa-psk ***** (password generated using wpa_passphrase tool)

```

iwconfig:

```

lo    no wireless extensions
eth0   no wireless extensions
ra0    Ralink STA   ESSID:"My_HomeNetwork_5G"  Nickname:"RT2870STA"
         Mode: Managed   Frequency:5.18 GHz  Access Point: C8:D3:A3:57:31:C9
         Bit Rate=300 Mb/s
         RTS thr:off   Fragment thr: off
         Link Quality=70/100   Signal Level:-52 dBm  Noise level:-83 dBm
         etc..

```

Like I said this was working on my old router and I checked the settings on this new router and everything checks out. Using WPA + WPA2 mixed mode with AES and TKIP. Double checked the PSK and everything looks good.

Does anyone have any ideas what could be causing the issue? The fact that I see the adapter show up in the router logs and connection list tells me it's trying to connect but I can't figure out why it's not showing the correct static IP instead of 0.0.0.0 and not connecting.

Also if I change it to use DHCP instead of a static IP I get DCHPNOOFFERS back when bringing up the network.

Cheers.

Update: 0.0.0.0 IP address in the router log is normal for static IP devices apparently.

---

### Post by TheFu on 2014-06-19
I found that the **wicd-curses** tool is the easiest way to manage wifi connections with a CLI GUI. I stopped messing with the interfaces file for wifi stuff.

It just contains:
```
auto wlan0
iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```
But I've fairly certain the wpa_supplicant isn't used from here anymore.

---

### Post by Al_Lougher on 2014-06-19
Thing is my interfaces file has been working fine, on my old router, just not with this one. So I have no doubt that the wireless adapter and drivers are working fine.

In syslog I see this:

wpa_supplicant[3455]: WPS-AP-AVAILABLE
wpa_supplicant[3455]: Trying to associate with c8:d3:a3:57:31:c9 (SSID='My_HomeNetwork_5G' freq=5180 MHz)
wpa_supplicant[3455]: Association request to the driver failed
wpa_supplicant[3455]: Authentication with c8:d3:a3:37:31:c9 timed out.

Then this repeats every few seconds.

From iwlist scan:

```

Cell 03 - Address: C8:D3:A3:57:31:C9
            Protocol: 802.11a/n
            ESSID:"My_HomeNetwork_5G"
            Mode: Managed
            Frequency:5.18 GHz (Channel 36)
            Quality:94/100 Signal level:-53 dBm   Noise level:-92 dBm
            Encryption key:on
            Bit Rates:300 Mb/s
            IE: WPA Version 1
                 Group Cipher : TKIP
                 Pairwise Ciphers (2) : TKIP CCMP
                 Authentication Suites (1) : PSK
            IE: IEEE 802.11i/WPA2 Version 1
                 Group Cipher : TKIP
                 Pairwise Ciphers (2) : TKIP CCMP
                 Authentication Suites (1) : PSK

```

---

### Post by steeldriver on 2014-06-19
I don't get why you need to specify all that WPA and driver stuff explicitly - have you tried just a minimal

```

iface ra0 inet dhcp
  wpa-ssid My_HomeNetwork_5G
  wpa-passphrase *your_wpa_passphrase*

```

---

