---
title: "WPA not working after upgrade to Hardy from Feisty"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by aolias on 2008-05-17
Hi lads,

I upgraded my Ubuntu installation from Feisty to Hardy and my wireless card just stopped to work.  

I have a WPN111 Netgear USB.  The ndiswrapper is working fine, because if I turn off the security in my router I can connect to the internet with no problem. But Enabling the WPA I cannot connect to the router.

I have installed wicd and I couldn't get it to work. Also I have running the gnome network manager. I installed the wpa_supplicant and I generated the key structure. So here it is my actual configuration

/etc/wpa_supplicant.conf
> 
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=2
fast_reauth=1

network={
	ssid="xxxxxxxxxxx"	
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=xxxxxxxxxxxxxxxxxxxxxxxxxx
} 

/etc/network/interfaces

> 
#iface wlan0 inet static
#address 192.168.0.9
#netmask 255.255.255.0
#gateway 192.168.0.1
#pre-up wpa_supplicant -Bw -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid xxxxxxxxxxxxxxxxxx
#wpa-ap-scan 1 # only needed if your access point uses a hidden ssid
wpa-proto WPA RSN
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxx



If I run the command   sudo ifup -v wlan0

> 
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "NETGEAR" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP TKIP -- OK
wpa_supplicant: wpa-group CCMP TKIP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto WPA RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:4d:2b:ee:a0
Sending on   LPF/wlan0/00:18:4d:2b:ee:a0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant



But never connects
I have also tried removing CCMP and RSN from the file, but the result is the same.



iwlist wlan0 scanning

> 
wlan0     Scan completed :
          
          Cell 02 - Address: 00:18:4D:01:BC:5E
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


iwconfig

> 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:4D:01:BC:5E   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Any idea? please help

---

### Post by kevdog on 2008-05-17
See post to manually do this yourself --
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

