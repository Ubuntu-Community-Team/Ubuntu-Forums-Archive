---
title: "Wireless is connecting, but not working"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Vinn on 2007-11-08
Hi, wireless has been crappy in Ubuntu for me. It works for a little while then stops for no reason. Happened in 6.10 so I upgraded to Gutsy, and the same thing happened. It says it is connected to my network (which isnt secured), but I cant use the internet.

It's a built in Atheros based card on a Toshiba Satellite A45 laptop. What's wrong everyone? This is really frustrating.

---

### Post by Vinn on 2007-11-08
[size="7"]help?![/size]

---

### Post by gilf on 2007-11-09
Not sure -- I use Atheros card with no problem.

Try testing again from the Live CD, to eliminate any problems you may have caused with settings inadvertently, then use the method I outlined in my previous posts. 

Gilf

---

### Post by nu2lnx on 2007-11-09
Two things-

1) Patience... 

2) You wouldn't be working with T-Mobile would you?  I had great luck at the hotel I was in Monday night when I connected to their house wireless, but at the place I have been for the last 3 nights, I have been experiencing similar issues.  Connections that drop for no apparent reason.  Eventually someone who knows more than us will wander in here and ask for a log, or the results of a command.  It'll start there.  Out of curiosity what does your syslog say?  Here is a snippet from mine for the last few minutes.  I'd be interested to see if yours is similar... I wrapped it in code tags for management of space...

```
Nov  8 23:41:00 NOMAD NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Nov  8 23:41:00 NOMAD NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'TERMINATE'.  Response: 'TIMEOUT[CLI]' 
Nov  8 23:41:00 NOMAD NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't terminate wpasupplicant cleanly. 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Activation (eth1) started... 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 23:41:00 NOMAD NetworkManager: <info>  Activation (eth1/wireless): access point 'tmobile' is unencrypted, no key needed. 
Nov  8 23:41:00 NOMAD kernel: [ 2680.416000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov  8 23:41:01 NOMAD NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: response was '0' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 746d6f62696c65' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 23:41:02 NOMAD kernel: [ 2682.020000] SoftMAC: Open Authentication completed with 00:12:d9:ed:4d:90
Nov  8 23:41:02 NOMAD NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'tmobile'. 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 23:41:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 23:41:02 NOMAD kernel: [ 2682.032000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Nov  8 23:41:04 NOMAD avahi-daemon[4951]: Registering new address record for fe80::20b:7dff:fe09:8525 on eth1.*.
Nov  8 23:41:04 NOMAD NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  8 23:41:04 NOMAD NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 23:41:04 NOMAD NetworkManager: <debug> [1194583264.568144] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:C6:91:F0 to 00:12:D9:ED:4D:90 on wireless network 'tmobile' 
Nov  8 23:41:04 NOMAD NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  8 23:41:04 NOMAD NetworkManager: <debug> [1194583264.574248] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:41:04 NOMAD NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  8 23:41:05 NOMAD NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  8 23:41:07 NOMAD NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  8 23:41:08 NOMAD dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  8 23:41:10 NOMAD dhclient: DHCPOFFER from 10.217.105.65
Nov  8 23:41:10 NOMAD dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov  8 23:41:10 NOMAD dhclient: DHCPACK from 10.217.105.65
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Registering new address record for 10.217.105.121 on eth1.IPv4.
Nov  8 23:41:10 NOMAD NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Nov  8 23:41:10 NOMAD NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  8 23:41:10 NOMAD NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Nov  8 23:41:10 NOMAD dhclient: bound to 10.217.105.121 -- renewal in 373 seconds.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Withdrawing address record for 10.217.105.121 on eth1.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Registering new address record for 10.217.105.121 on eth1.IPv4.
Nov  8 23:41:10 NOMAD dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Nov  8 23:41:10 NOMAD dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Nov  8 23:41:10 NOMAD dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Nov  8 23:41:10 NOMAD NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov  8 23:41:10 NOMAD NetworkManager: <info>    address 10.217.105.121 
Nov  8 23:41:10 NOMAD NetworkManager: <info>    netmask 255.255.255.192 
Nov  8 23:41:10 NOMAD NetworkManager: <info>    broadcast 10.217.105.127 
Nov  8 23:41:10 NOMAD NetworkManager: <info>    gateway 10.217.105.65 
Nov  8 23:41:10 NOMAD NetworkManager: <info>    nameserver 66.94.9.120 
Nov  8 23:41:10 NOMAD NetworkManager: <info>    nameserver 66.94.25.120 
Nov  8 23:41:10 NOMAD NetworkManager: <info>    domain name 'cust.hotspot.t-mobile.com' 
Nov  8 23:41:10 NOMAD NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  8 23:41:10 NOMAD NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov  8 23:41:10 NOMAD NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Withdrawing address record for 10.217.105.121 on eth1.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Withdrawing address record for fe80::20b:7dff:fe09:8525 on eth1.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 23:41:10 NOMAD avahi-daemon[4951]: Registering new address record for 10.217.105.121 on eth1.IPv4.
Nov  8 23:41:11 NOMAD NetworkManager: <info>  Clearing nscd hosts cache. 
Nov  8 23:41:11 NOMAD NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov  8 23:41:11 NOMAD NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  8 23:41:11 NOMAD NetworkManager: <debug> [1194583271.145743] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:41:11 NOMAD NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Nov  8 23:41:11 NOMAD NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  8 23:41:12 NOMAD avahi-daemon[4951]: Registering new address record for fe80::20b:7dff:fe09:8525 on eth1.*.
Nov  8 23:41:15 NOMAD ntpdate[5780]: no server suitable for synchronization found
Nov  8 23:41:21 NOMAD kernel: [ 2700.984000] eth1: no IPv6 routers present
Nov  8 23:41:59 NOMAD NetworkManager: <debug> [1194583319.171602] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:ED:4D:90 to 00:12:D9:C6:9C:40 on wireless network 'tmobile' 
Nov  8 23:41:59 NOMAD NetworkManager: <debug> [1194583319.174981] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:43:01 NOMAD NetworkManager: <debug> [1194583381.602086] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'tmobile' 
Nov  8 23:43:01 NOMAD NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / tmobile 
Nov  8 23:43:01 NOMAD NetworkManager: <info>  Deactivating device eth1. 
Nov  8 23:43:01 NOMAD dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5718
Nov  8 23:43:01 NOMAD dhclient: killed old client process, removed PID file
Nov  8 23:43:01 NOMAD dhclient: DHCPRELEASE on eth1 to 10.217.105.65 port 67
Nov  8 23:43:01 NOMAD avahi-daemon[4951]: Withdrawing address record for 10.217.105.121 on eth1.
Nov  8 23:43:01 NOMAD avahi-daemon[4951]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:43:01 NOMAD avahi-daemon[4951]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  8 23:43:02 NOMAD NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:02 NOMAD avahi-daemon[4951]: Withdrawing address record for fe80::20b:7dff:fe09:8525 on eth1.
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Activation (eth1) started... 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 23:43:02 NOMAD NetworkManager: <info>  Activation (eth1/wireless): access point 'tmobile' is unencrypted, no key needed. 
Nov  8 23:43:03 NOMAD NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  8 23:43:03 NOMAD NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant6^I' 
Nov  8 23:43:04 NOMAD kernel: [ 2803.532000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: response was '0' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 746d6f62696c65' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  SUP: response was 'OK' 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 23:43:04 NOMAD kernel: [ 2804.020000] SoftMAC: Open Authentication completed with 00:12:d9:c6:9c:40
Nov  8 23:43:04 NOMAD NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'tmobile'. 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 23:43:04 NOMAD NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 23:43:04 NOMAD kernel: [ 2804.032000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Nov  8 23:43:05 NOMAD NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  8 23:43:05 NOMAD dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Nov  8 23:43:05 NOMAD NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 23:43:05 NOMAD NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  8 23:43:05 NOMAD avahi-daemon[4951]: Registering new address record for fe80::20b:7dff:fe09:8525 on eth1.*.
Nov  8 23:43:06 NOMAD NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  8 23:43:07 NOMAD NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  8 23:43:09 NOMAD dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov  8 23:43:09 NOMAD dhclient: DHCPOFFER from 10.217.105.65
Nov  8 23:43:09 NOMAD dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov  8 23:43:09 NOMAD dhclient: DHCPACK from 10.217.105.65
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Registering new address record for 10.217.105.121 on eth1.IPv4.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Withdrawing address record for 10.217.105.121 on eth1.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Registering new address record for 10.217.105.121 on eth1.IPv4.
Nov  8 23:43:09 NOMAD NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Nov  8 23:43:09 NOMAD NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  8 23:43:09 NOMAD NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Nov  8 23:43:09 NOMAD dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Nov  8 23:43:09 NOMAD dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Nov  8 23:43:09 NOMAD dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Nov  8 23:43:09 NOMAD NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov  8 23:43:09 NOMAD NetworkManager: <info>    address 10.217.105.121 
Nov  8 23:43:09 NOMAD NetworkManager: <info>    netmask 255.255.255.192 
Nov  8 23:43:09 NOMAD NetworkManager: <info>    broadcast 10.217.105.127 
Nov  8 23:43:09 NOMAD NetworkManager: <info>    gateway 10.217.105.65 
Nov  8 23:43:09 NOMAD NetworkManager: <info>    nameserver 66.94.9.120 
Nov  8 23:43:09 NOMAD NetworkManager: <info>    nameserver 66.94.25.120 
Nov  8 23:43:09 NOMAD NetworkManager: <info>    domain name 'cust.hotspot.t-mobile.com' 
Nov  8 23:43:09 NOMAD NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  8 23:43:09 NOMAD NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov  8 23:43:09 NOMAD NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Withdrawing address record for 10.217.105.121 on eth1.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Withdrawing address record for fe80::20b:7dff:fe09:8525 on eth1.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.217.105.121.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 23:43:09 NOMAD avahi-daemon[4951]: Registering new address record for 10.217.105.121 on eth1.IPv4.
Nov  8 23:43:09 NOMAD dhclient: bound to 10.217.105.121 -- renewal in 397 seconds.
Nov  8 23:43:10 NOMAD NetworkManager: <info>  Clearing nscd hosts cache. 
Nov  8 23:43:10 NOMAD NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov  8 23:43:10 NOMAD NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  8 23:43:10 NOMAD NetworkManager: <debug> [1194583390.116822] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:43:10 NOMAD NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Nov  8 23:43:10 NOMAD NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  8 23:43:10 NOMAD ntpdate[5900]: adjust time server 91.189.94.4 offset 0.194671 sec
Nov  8 23:43:11 NOMAD avahi-daemon[4951]: Registering new address record for fe80::20b:7dff:fe09:8525 on eth1.*.
Nov  8 23:43:20 NOMAD kernel: [ 2819.980000] eth1: no IPv6 routers present
Nov  8 23:44:28 NOMAD NetworkManager: <debug> [1194583468.187563] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:C6:9C:40 to 00:12:D9:ED:4D:90 on wireless network 'tmobile' 
Nov  8 23:44:28 NOMAD NetworkManager: <debug> [1194583468.190944] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:44:41 NOMAD kernel: [ 2900.876000] SoftMAC: Open Authentication completed with 00:12:d9:c6:9c:40
Nov  8 23:44:42 NOMAD NetworkManager: <debug> [1194583482.187613] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:ED:4D:90 to 00:12:D9:C6:9C:40 on wireless network 'tmobile' 
Nov  8 23:44:42 NOMAD NetworkManager: <debug> [1194583482.190944] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:44:42 NOMAD kernel: [ 2902.120000] SoftMAC: Open Authentication completed with 00:12:d9:ed:4d:90
Nov  8 23:49:46 NOMAD dhclient: DHCPREQUEST on eth1 to 10.217.105.65 port 67
Nov  8 23:49:46 NOMAD dhclient: DHCPACK from 10.217.105.65
Nov  8 23:49:46 NOMAD NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Nov  8 23:49:46 NOMAD dhclient: bound to 10.217.105.121 -- renewal in 393 seconds.
Nov  8 23:51:16 NOMAD NetworkManager: <debug> [1194583876.211596] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:ED:4D:90 to 00:12:D9:C6:9C:40 on wireless network 'tmobile' 
Nov  8 23:51:16 NOMAD NetworkManager: <debug> [1194583876.214863] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:55:07 NOMAD kernel: [ 3526.624000] SoftMAC: Open Authentication completed with 00:12:d9:c6:98:80
Nov  8 23:55:08 NOMAD NetworkManager: <debug> [1194584108.219619] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:C6:9C:40 to 00:12:D9:C6:98:80 on wireless network 'tmobile' 
Nov  8 23:55:08 NOMAD NetworkManager: <debug> [1194584108.222798] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:55:08 NOMAD kernel: [ 3527.868000] SoftMAC: Open Authentication completed with 00:12:d9:c6:9c:40
Nov  8 23:55:12 NOMAD NetworkManager: <debug> [1194584112.219592] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:ED:4D:90 to 00:12:D9:C6:98:80 on wireless network 'tmobile' 
Nov  8 23:55:12 NOMAD NetworkManager: <debug> [1194584112.223631] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:56:19 NOMAD dhclient: DHCPREQUEST on eth1 to 10.217.105.65 port 67
Nov  8 23:56:19 NOMAD dhclient: DHCPACK from 10.217.105.65
Nov  8 23:56:19 NOMAD NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Nov  8 23:56:19 NOMAD dhclient: bound to 10.217.105.121 -- renewal in 344 seconds.
Nov  8 23:57:22 NOMAD NetworkManager: <debug> [1194584242.231646] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:ED:4D:90 to 00:12:D9:C6:98:80 on wireless network 'tmobile' 
Nov  8 23:57:22 NOMAD NetworkManager: <debug> [1194584242.234851] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  8 23:59:32 NOMAD NetworkManager: <debug> [1194584372.235633] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:ED:4D:90 to 00:12:D9:C6:98:80 on wireless network 'tmobile' 
Nov  8 23:59:32 NOMAD NetworkManager: <debug> [1194584372.239191] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  9 00:01:42 NOMAD NetworkManager: <debug> [1194584502.243620] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:12:D9:ED:4D:90 to 00:12:D9:C6:98:80 on wireless network 'tmobile' 
Nov  9 00:01:42 NOMAD NetworkManager: <debug> [1194584502.246699] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'tmobile' 
Nov  9 00:02:03 NOMAD dhclient: DHCPREQUEST on eth1 to 10.217.105.65 port 67
Nov  9 00:02:03 NOMAD dhclient: DHCPACK from 10.217.105.65
Nov  9 00:02:03 NOMAD NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Nov  9 00:02:03 NOMAD dhclient: bound to 10.217.105.121 -- renewal in 339 seconds.
```

---

