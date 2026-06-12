---
title: "Wireless setup problem"
date: 2005-06-26
forum: Networking &amp; Wireless
---

### Post by spiridion on 2005-06-26
after installing the drivers for my Broadcom BCM4309 using ndiswrapper,
I unable to connect to my wireless router.

The weird thing is that I am less than a meter away from my Linksys WRT54GS
and i works great with windows XP. 

In order to permform tests, i have removed all the security parameters and broadcast my ssid.

still, It doesn't work using iwconfig commands or the System>Administration>Networking panel.

any hints?

# ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present, hardware present

# iwconfig wlan0
wlan0     IEEE 802.11a  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:46 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# iwlist wlan0 scan
wlan0     No scan results

and here is the wireles section of my /etc/network/ interfaces

iface wlan0 inet static
wireless-essid mynetwork
address 192.168.1.50
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.1.1
wireless-mode Managed
dns-nameservers 212.27.32.176 212.27.32.177

---

