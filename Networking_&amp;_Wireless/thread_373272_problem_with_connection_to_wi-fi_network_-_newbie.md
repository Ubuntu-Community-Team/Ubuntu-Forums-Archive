---
title: "problem with connection to wi-fi network - newbie"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by szymon_g on 2007-03-01
hi
i've got a problem with making connection with wifi network :-/
i've installed a command-line system (EE), i've installed restricted-modules, so ubuntu can see my wi-fi card (intel ipw3945abg).
i've changed a /etc/network/interfaces file, it is it:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid SpeedTouchBCE72F
wireless-key s:lin7!

i've got a valid dns adress

search lan
nameserver 192.168.1.254 
(it's my resolv.conf)

sudo iwlist eth1 scan shows that:

eth1      Scan completed :
          Cell 01 - Address: 00:11:F5:AE:51:96
                    ESSID:"SpeedTouchBCE72F"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-62 dBm  Noise level=-62 dBm
                    Extra: Last beacon: 244ms ago

any suggestion how to make a connection?
bye
szymon

---

### Post by nachotronics on 2007-03-01
You might want to install network-manager-gnome following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**. This utility helps you set up WEP or WPA secured networks.

Hope this helps.

---

### Post by szymon_g on 2007-03-03
thanx, but i've installed a command-line system only... so i dont have a Gnome :-/

---

