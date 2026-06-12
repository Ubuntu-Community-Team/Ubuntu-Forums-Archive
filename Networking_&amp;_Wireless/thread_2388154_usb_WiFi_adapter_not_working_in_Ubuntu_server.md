---
title: "usb WiFi adapter not working in Ubuntu server"
date: 2018-03-29
forum: Networking &amp; Wireless
---

### Post by rubenstobbart on 2018-03-29
I have the following problem in Ubuntu Server 16.04:


[LIST]
[*]When I am installing Ubuntu from the CD, TP-Link adapter works fine and updates and aditional packages are download.
[*]After install, the adapter doesn't work and there's no Internet connection.
[/LIST]

If I enter in network interfaces there's no network interface at all.

How can I fix that?

---

### Post by chili555 on 2018-03-29
Please run and post:```
iwconfig
lsusb
cat /etc/network/interfaces
```Thanks!

---

### Post by rubenstobbart on 2018-03-29
iwconfig:

```

wifi0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:2 Mb/s   
          Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
enp2s5    IEEE 802.11b  ESSID:""  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:2 Mb/s   
          Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlx90f652e255a4  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
enp2s10   no wireless extensions.

```

lsusb:

```

Bus 001 Device 003: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 / TL-WN822N v2 802.11n [Atheros AR7010+AR9287]
Bus 001 Device 002: ID 13fe:4200 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

cat /etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

```

Thank you!!

---

### Post by chili555 on 2018-03-29
I suggest you set up /etc/network/interfaces something like:

```
auto lo
iface lo inet loopback

auto wlx90f652e255a4 
iface wlx90f652e255a4 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_router>
wpa-psk <your_wpa_key>
dns-nameservers 8.8.8.8 192.168.1.1
```
Be sure to select a static address outside the range used by the DHCP server in the router, switch or other access point. Of course, substitute your details here. I suggested a static IP address here so that you can easily ssh and ftp into the server. 

Get the system to read and use the changes:

```
sudo ifdown wlx90f652e255a4  && sudo ifup -v wlx90f652e255a4 
```
Did you connect?

```
ping -c3 192.168.1.1
ping -c3 www.google.com
```

---

### Post by rubenstobbart on 2018-03-30
I connect. Thank you very much!!!! \\:D/\\:D/\\:D/\\:D/

---

