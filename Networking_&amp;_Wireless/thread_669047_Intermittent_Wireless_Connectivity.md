---
title: "Intermittent Wireless Connectivity"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by jbrown96 on 2008-01-16
My father just got a new Lenovo 3000 N200, and I have convinced him to put Ubuntu 7.10 AMD64 on it. I have been trying to set it up for him, but the wireless has been a huge problem. 
It uses the BCM4310 chipset, which is bad news. It's been a while since I've dealt with this type of card, so the restricted drivers manager was awesome. 
Wireless does work, but only with some networks. It needs to be able to connect any access point because he travels a lot. This is where the trouble begins. Network-Manager will connect to some networks some of the time. It connects without fail to our 2wire AP that uses WPA-PSK, but has problems if I change the ESSID. I can play with it and get it to work by selecting it from the usual dropdown menu, "connecting to other wireless network," or taking it out of roaming mode and configuring it. 
There is another "linksys" (no security, imagine that) AP within range, so I have tried connecting to that too, but it will not work. 
Changing encryption (none, WEP, WPA-PSK) seems to have random success. I'll attach some system logs, but the problem seems to be that once connected, DHCP does not work. The strange part is that it happens on my computer (Thinkpad T61p intel 3945abg), too. I have mixed success connecting to various APs, same log files, too. 

Is there anyway to make it more reliable. My father is no computer expert, and while he will follow instructions, troubleshooting is a little above him. 

log files from /var/log/daemon.log

Successful Connection
> Jan 15 23:21:48 ubuntu NetworkManager: <debug> [1200460908.126732] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '2WIRE476' 
Jan 15 23:21:48 ubuntu NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth0 / 2WIRE476 
Jan 15 23:21:48 ubuntu NetworkManager: <info>  Deactivating device eth0. 
Jan 15 23:21:48 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6665
Jan 15 23:21:48 ubuntu dhclient: killed old client process, removed PID file
Jan 15 23:21:48 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.1.254 port 67
Jan 15 23:21:48 ubuntu avahi-daemon[5125]: Withdrawing address record for 192.168.1.68 on eth0.
Jan 15 23:21:48 ubuntu avahi-daemon[5125]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Jan 15 23:21:48 ubuntu avahi-daemon[5125]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan 15 23:21:49 ubuntu NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:49 ubuntu avahi-daemon[5125]: Withdrawing address record for fe80::21e:4cff:feb1:5e13 on eth0.
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) started... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0/wireless): access point '2WIRE476' is encrypted, but NO valid key exists.  New key needed. 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) New wireless user key requested for network '2WIRE476'. 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) New wireless user key for network '2WIRE476' received. 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 15 23:21:49 ubuntu NetworkManager: <info>  Activation (eth0/wireless): access point '2WIRE476' is encrypted, and a key exists.  No new key needed. 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth0^I^Iwext^I/var/run/wpa_supplicant7^I' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was '0' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 3257495245343736' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 15 23:21:50 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 15 23:21:51 ubuntu NetworkManager: <info>  Activation (eth0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point '2WIRE476'. 
Jan 15 23:21:51 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 15 23:21:51 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 15 23:21:51 ubuntu avahi-daemon[5125]: Registering new address record for fe80::21e:4cff:feb1:5e13 on eth0.*.
Jan 15 23:21:52 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jan 15 23:21:52 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 1
Jan 15 23:21:52 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 15 23:21:52 ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jan 15 23:21:53 ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jan 15 23:21:55 ubuntu NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Jan 15 23:21:57 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan 15 23:21:57 ubuntu dhclient: DHCPOFFER from 192.168.1.254
Jan 15 23:21:57 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan 15 23:21:57 ubuntu dhclient: DHCPACK from 192.168.1.254
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: New relevant interface eth0.IPv4 for mDNS.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Registering new address record for 192.168.1.68 on eth0.IPv4.
Jan 15 23:21:57 ubuntu NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Jan 15 23:21:57 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 15 23:21:57 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jan 15 23:21:57 ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan 15 23:21:57 ubuntu NetworkManager: <info>    address 192.168.1.68 
Jan 15 23:21:57 ubuntu NetworkManager: <info>    netmask 255.255.255.0 
Jan 15 23:21:57 ubuntu NetworkManager: <info>    broadcast 192.168.1.255 
Jan 15 23:21:57 ubuntu NetworkManager: <info>    gateway 192.168.1.254 
Jan 15 23:21:57 ubuntu NetworkManager: <info>    nameserver 192.168.1.254 
Jan 15 23:21:57 ubuntu NetworkManager: <info>    domain name 'gateway.2wire.net' 
Jan 15 23:21:57 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 15 23:21:57 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jan 15 23:21:57 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Withdrawing address record for 192.168.1.68 on eth0.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Withdrawing address record for fe80::21e:4cff:feb1:5e13 on eth0.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: New relevant interface eth0.IPv4 for mDNS.
Jan 15 23:21:57 ubuntu avahi-daemon[5125]: Registering new address record for 192.168.1.68 on eth0.IPv4.
Jan 15 23:21:57 ubuntu dhclient: bound to 192.168.1.68 -- renewal in 39350 seconds.
Jan 15 23:21:58 ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
Jan 15 23:21:58 ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan 15 23:21:58 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jan 15 23:21:58 ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jan 15 23:21:58 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 15 23:21:58 ubuntu NetworkManager: <debug> [1200460918.428888] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network '2WIRE476' 

Failed Connection
> Jan 16 00:44:42 ubuntu NetworkManager: <debug> [1200465882.216207] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'linksys' 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth0 / linksys 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Deactivating device eth0. 
Jan 16 00:44:42 ubuntu avahi-daemon[5113]: Withdrawing address record for fe80::21e:4cff:feb1:5e13 on eth0.
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Activation (eth0) started... 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 00:44:42 ubuntu NetworkManager: <info>  Activation (eth0/wireless): access point 'linksys' is unencrypted, no key needed. 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth0^I^Iwext^I/var/run/wpa_supplicant2^I' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: response was '0' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b737973' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  Activation (eth0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'linksys'. 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 16 00:44:43 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 16 00:44:45 ubuntu avahi-daemon[5113]: Registering new address record for fe80::21e:4cff:feb1:5e13 on eth0.*.
Jan 16 00:44:45 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jan 16 00:44:45 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 16 00:44:45 ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jan 16 00:44:46 ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jan 16 00:44:48 ubuntu NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Jan 16 00:44:49 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan 16 00:44:55 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jan 16 00:45:06 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan 16 00:45:09 ubuntu NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Jan 16 00:45:18 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Jan 16 00:45:20 ubuntu dhclient: No DHCPOFFERS received.
Jan 16 00:45:20 ubuntu avahi-autoipd(eth0)[7299]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jan 16 00:45:20 ubuntu avahi-autoipd(eth0)[7299]: Successfully called chroot().
Jan 16 00:45:20 ubuntu avahi-autoipd(eth0)[7299]: Successfully dropped root privileges.
Jan 16 00:45:20 ubuntu avahi-autoipd(eth0)[7299]: Starting with address 169.254.4.161
Jan 16 00:45:24 ubuntu avahi-autoipd(eth0)[7299]: Callout BIND, address 169.254.4.161 on interface eth0
Jan 16 00:45:24 ubuntu avahi-daemon[5113]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.4.161.
Jan 16 00:45:24 ubuntu avahi-daemon[5113]: New relevant interface eth0.IPv4 for mDNS.
Jan 16 00:45:24 ubuntu avahi-daemon[5113]: Registering new address record for 169.254.4.161 on eth0.IPv4.
Jan 16 00:45:28 ubuntu avahi-autoipd(eth0)[7299]: Successfully claimed IP address 169.254.4.161
Jan 16 00:45:28 ubuntu NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth0 
Jan 16 00:45:28 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jan 16 00:45:28 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Jan 16 00:45:28 ubuntu NetworkManager: <info>  Activation (eth0) failure scheduled... 
Jan 16 00:45:28 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Jan 16 00:45:28 ubuntu NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  Activation (eth0) failed for access point (linksys) 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  Activation (eth0) failed. 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  Deactivating device eth0. 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Jan 16 00:45:29 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 00:45:29 ubuntu avahi-daemon[5113]: Withdrawing address record for 169.254.4.161 on eth0.
Jan 16 00:45:29 ubuntu avahi-daemon[5113]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.4.161.
Jan 16 00:45:29 ubuntu avahi-daemon[5113]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan 16 00:45:29 ubuntu avahi-daemon[5113]: Withdrawing address record for fe80::21e:4cff:feb1:5e13 on eth0.
Jan 16 00:45:30 ubuntu avahi-autoipd(eth0)[7299]: SIOCSIFFLAGS failed: Permission denied
Jan 16 00:45:30 ubuntu avahi-autoipd(eth0)[7299]: Callout STOP, address 169.254.4.161 on interface eth0
Jan 16 00:45:30 ubuntu dhclient: receive_packet failed on eth0: Network is down
Jan 16 00:45:30 ubuntu avahi-autoipd(eth0)[7300]: client: RTNETLINK answers: Cannot assign requested address
Jan 16 00:45:30 ubuntu avahi-autoipd(eth0)[7300]: Script execution failed with return value 2
Jan 16 00:45:34 ubuntu NetworkManager: <debug> [1200465934.492905] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'thisisonlyatest' 
Jan 16 00:45:34 ubuntu NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth0 / thisisonlyatest 


Thanks for all the help

---

