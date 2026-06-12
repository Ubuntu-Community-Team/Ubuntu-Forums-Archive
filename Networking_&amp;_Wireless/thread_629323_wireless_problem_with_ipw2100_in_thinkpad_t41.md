---
title: "wireless problem with ipw2100 in thinkpad t41"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by netmax2k on 2007-12-02
I have a IBM thinkpad t41 with ipw2100 wireless card and having problems with making it work with WPA-PSK. I serached the forum and followed a couple of examples including weiman01's sticky with no luck. I have posted my config here for your advise and help.

my config information:

/etc/network/interfaces:
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <ssid>
wpa-key-mgmt WPA-PSK
wpa-ap-scan 1
wpa-proto RSN
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

iwconfig output:

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


user@astro:~$ lsmod | grep ipw
ipw2100                72240  0 
ieee80211              35656  1 ipw2100

---

### Post by netmax2k on 2007-12-03
Can someone help me with this  ?

---

