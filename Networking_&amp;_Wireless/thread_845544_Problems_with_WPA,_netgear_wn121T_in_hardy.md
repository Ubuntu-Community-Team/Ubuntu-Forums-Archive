---
title: "Problems with WPA, netgear wn121T in hardy"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by happyoldguy on 2008-06-30
doh! I left the mac address filtering enabled on the router - works now I've fixed that up:D...


---------------------------------




Apologies if I missed the fix, I have searched here for quite a while before posting....

Ok here goes.

My setup - 
linksys router wrt160n
WPA-Mixed enabled

DSL working, wireless working (can access internet from Eeepc and Mac mini) and wired connection works fine

I want to be able to use WPA - not too keen on WEP, and certainly don't want to use an open network.

My network name is prickly - the other network in the area is from a neighbours setup

ok, so here are my configs and the output of various commands


[I]/etc/networking/interfaces
[/I]


auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
wpa-driver wext
wpa-ssid prickly
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <mylonghexstring> - generated using this guide -  [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) - ie. wpa_passphrase <my_essid> <my_preshared_key>    

	

*/etc/wpa_supplicant.conf*

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
   ssid="prickly"
   scanssid=1
   proto=WPA
   key_mgmt=WPA-PSK
   psk="<my pre shared key>"
   pairwise=TKIP
   group=TKIP

}

Here's the output from various commands I have seen others run to try to diagnose issues

[I]
$route[/I]

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.116.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.84.0    *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     0      0        0 wlan1
default         *               0.0.0.0         U     1000   0        0 wlan1

*$iwconfig*

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

*$sudo iwlist scan*

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:11:F5:CD:E8:93
                    ESSID:"BTVOYAGER2091-93"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1D:7E:B2:FB:2F
                    ESSID:"prickly"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

*$ sudo lshw -C network*

  *-network UNCLAIMED     
       description: Ethernet controller
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=52 mingnt=11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:14:6c:ca:ce:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.52+Netgear,11/19/2007,1.0.7.3 link=no multicast=yes wireless=IEEE 802.11g


[I]$sudo ifdown -v wlan1
[/I]
Configuring interface wlan1=wlan1 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan1.pid -lf /var/lib/dhcp3/dhclient.wlan1.leases wlan1
There is already a pid file /var/run/dhclient.wlan1.pid with pid 20590
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:14:6c:ca:ce:8e
Sending on   LPF/wlan1/00:14:6c:ca:ce:8e
Sending on   Socket/fallback
DHCPRELEASE on wlan1 to 192.168.1.1 port 67
ifconfig wlan1 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/linux-wlan-ng-post-down
wlanctl-ng: Operation not supported
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan1.pid
Stopped /sbin/wpa_supplicant (pid 20547).

*$sudo ifup -v wlan1*

Configuring interface wlan1=wlan1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
[B]run-parts: executing /etc/network/if-pre-up.d/linux-wlan-ng-pre-up
wlanctl-ng: Operation not supported
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1[/B]
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan1.pid -i wlan1 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan1
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "prickly" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise TKIP -- OK
wpa_supplicant: wpa-group TKIP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto WPA -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan1.pid -lf /var/lib/dhcp3/dhclient.wlan1.leases wlan1
There is already a pid file /var/run/dhclient.wlan1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:14:6c:ca:ce:8e
Sending on   LPF/wlan1/00:14:6c:ca:ce:8e
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.1.2
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
 * Stopping NTP server ntpd
   ...done.
run-parts: executing /etc/network/if-up.d/wpasupplicant


Ajny thoughts anyone?

is the problem in this bit

[B]un-parts: executing /etc/network/if-pre-up.d/linux-wlan-ng-pre-up
wlanctl-ng: Operation not supported
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1[/B]

or is something else going wrong?

suggestions on how to troubleshoot further appreciated 

thanks

---

