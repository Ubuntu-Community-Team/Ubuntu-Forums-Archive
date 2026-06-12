---
title: "Encore ENUWI-G USB Adapter"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by boralyl on 2007-04-07
I used ndiswrapper to install drivers for my Encore ENUWI-G USB Adapter and got the wireless card working and internet access working.

The problem is my internet access suddenly stopped working one day.  The usb adapter is active and looking at ndiswrapper everything seems ok, but maybe someone here will see something I don't.

Some Info:
```
ndiswrapper -l
sis163u : driver installed
device (0457:0163) present
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:"04Z409115484"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:CD:14:A1
          Bit Rate:48 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3
          RTS thr:2312 B   Fragment thr:2312 B
          Power Management:off
          Link Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:38  Invalid misc:469   Missed beacon:0

sit0      no wireless extensions.

```

```
iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:CD:14:A1
                    ESSID:"04Z409115484"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 22 Mb/s
                              18 Mb/s; 12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s
                              5.5 Mb/s; 2 Mb/s; 1 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 02 - Address: 00:0D:0B:FD:7B:65
                    ESSID:"000D0BFD7B64"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s; 5.5 Mb/s
                              2 Mb/s; 1 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

My /etc/networks/interfaces file:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

Going into the network connections gui manager, I can set it to enabled, but no IP address ever appears next to the wireless connection, and I can't surf the net.  Any ideas?

---

### Post by Floppyjoe on 2007-04-07
You may need to add some information to your /etc/network/interfaces file.
```
sudo gedit /etc/network/interfaces
```
Something like the following:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid 04Z409115484
wireless-channel 6
wireless-mode managed

```

---

### Post by boralyl on 2007-04-08
Thanks, that worked.

---

