---
title: "Joining WPA wireless network kicks everyone off"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by jlujan on 2008-05-28
When trying to connect to a WPA protected network, my laptop will cause all other wireless devices to lose their connections. Sometimes my laptop will connect, sometimes it will not. I recompiled NetworkManager from the dpkg source to extend the wpa supplicant timeout from 60sec to 120sec which improved connection success. Sometimes it will connect and then knock everyone off the wireless network including itself. This has happened when connecting to an Apple Airport Express access point as well as a Linksys WAP45G access point. I amusing the latest windows XP driver from Realtek through ndiswrapper compiled from the latest source release.


OS: Ubuntu 8.04 on a Toshiba A205-S5809 ( not using built in wireless)
Kernel: 2.6.24-16-generic
x86

lsusb:
...
Bus 007 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
...

ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

ndiswrapper -l
net8187b : driver installed
        device (0BDA:8189) present

Configuring using NetworkManager

May 28 16:52:00 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
May 28 16:52:00 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
May 28 16:52:00 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
May 28 16:52:00 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
May 28 16:52:00 jeremy-laptop NetworkManager: <info>  Activation (wlan1/wireless): access point 'Level10' is encrypted, but NO valid key exists.  New key needed. 
May 28 16:52:00 jeremy-laptop NetworkManager: <info>  Activation (wlan1) New wireless user key requested for network 'Level10'. 
May 28 16:52:00 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
May 28 16:52:07 jeremy-laptop NetworkManager: <info>  Activation (wlan1) New wireless user key for network 'Level10' received. 
May 28 16:52:07 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 16:52:07 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
May 28 16:52:07 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
May 28 16:52:07 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
May 28 16:52:07 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
May 28 16:52:07 jeremy-laptop NetworkManager: <info>  Activation (wlan1/wireless): access point 'Level10' is encrypted, and a key exists.  No new key needed. 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was '0' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4c6576656c3130' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 28 16:52:09 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
May 28 16:52:15 jeremy-laptop NetworkManager: <info>  Supplicant state changed: 1 
May 28 16:52:15 jeremy-laptop NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Level10'. 
May 28 16:52:15 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled. 
May 28 16:52:15 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started... 
May 28 16:52:16 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Beginning DHCP transaction. 
May 28 16:52:16 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete. 
May 28 16:52:16 jeremy-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan1 
May 28 16:52:16 jeremy-laptop dhclient: There is already a pid file /var/run/dhclient.wlan1.pid with pid 134519072
May 28 16:52:17 jeremy-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan1 
May 28 16:52:19 jeremy-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
May 28 16:52:19 jeremy-laptop dhclient: DHCPOFFER of 192.168.0.184 from 192.168.0.150
May 28 16:52:19 jeremy-laptop dhclient: DHCPREQUEST of 192.168.0.184 on wlan1 to 255.255.255.255 port 67
May 28 16:52:19 jeremy-laptop dhclient: DHCPACK of 192.168.0.184 from 192.168.0.150
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.184.
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: New relevant interface wlan1.IPv4 for mDNS.
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: Registering new address record for 192.168.0.184 on wlan1.IPv4.
May 28 16:52:19 jeremy-laptop dhclient: bound to 192.168.0.184 -- renewal in 343359 seconds.
May 28 16:52:19 jeremy-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan1 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) scheduled... 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) started... 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>    address 192.168.0.184 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>    netmask 255.255.255.0 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>    broadcast 192.168.0.255 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>    gateway 192.168.0.1 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>    nameserver 192.168.0.150 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>    nameserver 192.168.0.151 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>    domain name 'springfield.' 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) complete. 
May 28 16:52:19 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started... 
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: Withdrawing address record for 192.168.0.184 on wlan1.
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.184.
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: Interface wlan1.IPv4 no longer relevant for mDNS.
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.184.
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: New relevant interface wlan1.IPv4 for mDNS.
May 28 16:52:19 jeremy-laptop avahi-daemon[5073]: Registering new address record for 192.168.0.184 on wlan1.IPv4.
May 28 16:52:20 jeremy-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
May 28 16:52:20 jeremy-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May 28 16:52:20 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Finish handler scheduled. 
May 28 16:52:20 jeremy-laptop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete. 
May 28 16:52:20 jeremy-laptop NetworkManager: <info>  Supplicant state changed: 0 
May 28 16:52:20 jeremy-laptop NetworkManager: <info>  Activation (wlan1) successful, device activated. 
May 28 16:52:20 jeremy-laptop NetworkManager: <debug> [1212011540.560378] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Level10' 
May 28 16:52:20 jeremy-laptop NetworkManager: <debug> [1212011540.560651] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Level10' 
May 28 16:52:20 jeremy-laptop NetworkManager: <debug> [1212011540.560774] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Level10' 
May 28 16:52:20 jeremy-laptop NetworkManager: <debug> [1212011540.560884] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Level10' 
May 28 16:52:20 jeremy-laptop NetworkManager: <debug> [1212011540.560993] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Level10' 
May 28 16:52:20 jeremy-laptop NetworkManager: <debug> [1212011540.561101] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Level10' 
May 28 16:52:20 jeremy-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
May 28 16:52:40 jeremy-laptop NetworkManager: <info>  wlan1: link timed out. 
May 28 16:53:00 jeremy-laptop ntpdate[6592]: can't find host ntp.ubuntu.com 
May 28 16:53:00 jeremy-laptop ntpdate[6592]: no servers can be used, exiting
May 28 16:53:00 jeremy-laptop NetworkManager: <info>  Supplicant state changed: 0 
May 28 16:53:05 jeremy-laptop NetworkManager: <info>  Supplicant state changed: 1 
May 28 16:53:13 jeremy-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 28 16:53:37 jeremy-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
May 28 16:53:43 jeremy-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
May 28 16:53:43 jeremy-laptop dhclient: DHCPOFFER of 192.168.0.184 from 192.168.0.150
May 28 16:53:43 jeremy-laptop dhclient: DHCPREQUEST of 192.168.0.184 on wlan1 to 255.255.255.255 port 67
May 28 16:53:47 jeremy-laptop dhclient: DHCPREQUEST of 192.168.0.184 on wlan1 to 255.255.255.255 port 67
May 28 16:53:47 jeremy-laptop dhclient: DHCPACK of 192.168.0.184 from 192.168.0.150
May 28 16:53:47 jeremy-laptop dhclient: bound to 192.168.0.184 -- renewal in 325560 seconds.
May 28 16:53:47 jeremy-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 28 16:54:11 jeremy-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
May 28 16:54:21 jeremy-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 28 16:54:55 jeremy-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 28 16:57:09 jeremy-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one.

---

