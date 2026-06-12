---
title: "ipw3945 and wpa gutsy"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by mb0108 on 2007-10-16
Hi all, 

I know that there are many threads about the ipw3945. But I tried them all and I have the big problem, that when I use the ipw3945 with wpa encryption, I get network packet losses and the network is very slow. 
When I open the network and connect and connect without encryption, evrything works fine, but thats not really a solution for me :-) 
I have a Dell XPS m1330 and installed Feisty and updated to Gutsys latest packages using the Updatemanager. 

I tried with the Networkmanager and ended up in manual configuration but the problem stays the same. 

Here are some outputs that may help:

dmesg | grep ipw3945

[   28.029284] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   28.029289] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   28.031446] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   30.037391] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

modinfo ipw3945:

filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2mp.ubuntu1
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     04FD04D6570525365D93930
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.22-14-generic SMP mod_unload 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)

cat /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The wired ethernet port
auto eth0

# This is the wireless interface through which wpa supplicant will provide logical interfaces
iface eth1 inet dhcp 
   wpa-driver wext
   wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto eth1

cat /etc/wpa_supplicant/wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
# 0: Der Treiber des Interfaces kümmert sich um das Scannen von Netzen und die AP Auswahl.
#    Dieser Mode sollte benutzt werden, wenn man eine Verschlüsselung auf ein Kabelnetzwerk legt.
# 1: wpa_supplicant kümmert sich um das Scannen von Netzen und die AP Auswahl.
# 2: Fast wie 0, es wird aber mit Hilfe von Sicherheitsrichtlinien und der SSID zu APs verbunden (BSSID wird nicht unterstützt)
#
# Normalerweise funktioniert entweder Mode 1 oder Mode 2.
ap_scan=1
network={
        ssid="secret"
        scan_ssid=1
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=
        group=TKIP CCMP
        psk=mypsk
}

ping [www.google.de](www.google.de)

PING [www.l.google.com](www.l.google.com) (209.85.135.147) 56(84) bytes of data.
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=1 ttl=244 time=51.8 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=2 ttl=244 time=54.1 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=4 ttl=244 time=51.1 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=8 ttl=244 time=51.4 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=9 ttl=244 time=51.2 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=10 ttl=244 time=52.7 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=12 ttl=244 time=51.4 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=14 ttl=244 time=52.1 ms
64 bytes from 209.85.135.147: icmp_seq=15 ttl=244 time=51.3 ms
64 bytes from mu-in-f147.google.com (209.85.135.147): icmp_seq=17 ttl=244 time=51.5 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
17 packets transmitted, 10 received, 41% packet loss, time 50367ms
rtt min/avg/max/mdev = 51.115/51.908/54.101/0.861 ms

Thanks for any help,
Michael

---

### Post by mb0108 on 2007-10-16
Hi, 

for your information: if someone has similar problems. I replaced the ipw3945 driver with the iwl3945  module, which is built in to the Gutsy kernel. Now I have a perfect WLAN connection with WPA2. The only issue is now, that the Wifi LED on the dell is not shining but that's of minor importance. 

Michael

---

### Post by ahhyamom on 2007-10-18
Hi,

Can you please post some steps in order to get this driver working.

I'm assuming something on the order of:

modprobe -r ipw3945
modprobe iwl3945

??

Thank you.

---

