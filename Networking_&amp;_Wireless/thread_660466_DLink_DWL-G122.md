---
title: "DLink DWL-G122"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by ram zu on 2008-01-06
Hi.

I'me using 7.10 with a d-link dwl-g122, near the AP and with a good signal strength.
When I plug in the usb device, the system recognise the pen and after a few seconds it start to discover AP's.
After that I select the correct AP and enter the correct information (wep key 64) but it dosnt get IP and after some time it ask for the same info again and again... (when I know that is correct).

What is wrong withis on?
My next step is using NDISWrapper.

P.S. If the pen find some AP's and I don't connect to any of them, after a while the AP list show no results (???)

---

### Post by ram zu on 2008-01-12
In the upper post I was using dwl-g122 B1 but I get a C1 version and now I get connected to my wifi.
But after a some time it get disconected again.
Here is some lines from my:

_syslog_

```
Jan 10 22:12:22 tobias NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 10 22:12:22 tobias NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan1'. 
Jan 10 22:12:22 tobias dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.reason
Jan 10 22:12:22 tobias NetworkManager: <info>  Will activate connection 'wlan1/2WIRE-PT-185'. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Device wlan1 activation scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) started... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1/wireless): access point '2WIRE-PT-185' is encrypted, but NO valid key exists.  New key needed. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) New wireless user key requested for network '2WIRE-PT-185'. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) New wireless user key for network '2WIRE-PT-185' received. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1/wireless): access point '2WIRE-PT-185' is encrypted, and a key exists.  No new key needed. 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was '0' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 32574952452d50542d313835' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Jan 10 22:12:25 tobias kernel: [ 3289.112838] wlan1: Initial auth_alg=0
Jan 10 22:12:25 tobias kernel: [ 3289.112844] wlan1: authenticate with AP 00:1b:5b:af:95:c1
Jan 10 22:12:25 tobias kernel: [ 3289.114348] wlan1: RX authentication from 00:1b:5b:af:95:c1 (alg=0 transaction=2 status=0)
Jan 10 22:12:25 tobias kernel: [ 3289.114351] wlan1: authenticated
Jan 10 22:12:25 tobias kernel: [ 3289.114353] wlan1: associate with AP 00:1b:5b:af:95:c1
Jan 10 22:12:25 tobias NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point '2WIRE-PT-185'. 
Jan 10 22:12:25 tobias NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 10 22:12:25 tobias NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started... 
Jan 10 22:12:25 tobias kernel: [ 3289.116216] wlan1: RX AssocResp from 00:1b:5b:af:95:c1 (capab=0x431 status=0 aid=1)
Jan 10 22:12:25 tobias kernel: [ 3289.116219] wlan1: associated
Jan 10 22:12:26 tobias NetworkManager: <info>  Activation (wlan1) Beginning DHCP transaction. 
Jan 10 22:12:26 tobias dhclient: wmaster0: unknown hardware address type 801
Jan 10 22:12:26 tobias NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete. 
Jan 10 22:12:26 tobias NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan1 
Jan 10 22:12:27 tobias NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan1 
Jan 10 22:12:27 tobias dhclient: wmaster0: unknown hardware address type 801
Jan 10 22:12:27 tobias dhclient: DHCPREQUEST on wlan1 to 255.255.255.255 port 67
Jan 10 22:12:27 tobias dhclient: DHCPACK from 192.168.1.254
Jan 10 22:12:28 tobias avahi-daemon[4769]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.71.
Jan 10 22:12:28 tobias avahi-daemon[4769]: New relevant interface wlan1.IPv4 for mDNS.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Registering new address record for 192.168.1.71 on wlan1.IPv4.
Jan 10 22:12:28 tobias NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan1 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) started... 
Jan 10 22:12:28 tobias dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.host_name
Jan 10 22:12:28 tobias dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.nis_domain
Jan 10 22:12:28 tobias dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.nis_servers
Jan 10 22:12:28 tobias NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan 10 22:12:28 tobias NetworkManager: <info>    address 192.168.1.71 
Jan 10 22:12:28 tobias NetworkManager: <info>    netmask 255.255.255.0 
Jan 10 22:12:28 tobias NetworkManager: <info>    broadcast 192.168.1.255 
Jan 10 22:12:28 tobias NetworkManager: <info>    gateway 192.168.1.254 
Jan 10 22:12:28 tobias NetworkManager: <info>    nameserver 192.168.1.254 
Jan 10 22:12:28 tobias NetworkManager: <info>    domain name 'gateway.2wire.net' 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) complete. 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started... 
Jan 10 22:12:28 tobias avahi-daemon[4769]: Withdrawing address record for 192.168.1.71 on wlan1.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.71.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.71.
Jan 10 22:12:28 tobias avahi-daemon[4769]: New relevant interface wlan1.IPv4 for mDNS.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Registering new address record for 192.168.1.71 on wlan1.IPv4.
Jan 10 22:12:28 tobias dhclient: bound to 192.168.1.71 -- renewal in 33909 seconds.
Jan 10 22:12:29 tobias NetworkManager: <info>  Clearing nscd hosts cache. 
Jan 10 22:12:29 tobias NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan 10 22:12:29 tobias NetworkManager: <info>  Activation (wlan1) successful, device activated. 
Jan 10 22:12:29 tobias NetworkManager: <info>  Activation (wlan1) Finish handler scheduled. 
Jan 10 22:12:29 tobias NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit)
```

_daemon.log_

```
Jan 10 22:12:22 tobias NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 10 22:12:22 tobias NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan1'. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Will activate connection 'wlan1/2WIRE-PT-185'. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Device wlan1 activation scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) started... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1/wireless): access point '2WIRE-PT-185' is encrypted, but NO valid key exists.  New key needed. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) New wireless user key requested for network '2WIRE-PT-185'. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) New wireless user key for network '2WIRE-PT-185' received. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Jan 10 22:12:22 tobias NetworkManager: <info>  Activation (wlan1/wireless): access point '2WIRE-PT-185' is encrypted, and a key exists.  No new key needed. 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Jan 10 22:12:23 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was '0' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 32574952452d50542d313835' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 10 22:12:24 tobias NetworkManager: <info>  SUP: response was 'OK' 
Jan 10 22:12:24 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Jan 10 22:12:25 tobias NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point '2WIRE-PT-185'. 
Jan 10 22:12:25 tobias NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 10 22:12:25 tobias NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started... 
Jan 10 22:12:26 tobias NetworkManager: <info>  Activation (wlan1) Beginning DHCP transaction. 
Jan 10 22:12:26 tobias dhclient: wmaster0: unknown hardware address type 801
Jan 10 22:12:26 tobias NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete. 
Jan 10 22:12:26 tobias NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan1 
Jan 10 22:12:27 tobias NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan1 
Jan 10 22:12:27 tobias dhclient: wmaster0: unknown hardware address type 801
Jan 10 22:12:27 tobias dhclient: DHCPREQUEST on wlan1 to 255.255.255.255 port 67
Jan 10 22:12:27 tobias dhclient: DHCPACK from 192.168.1.254
Jan 10 22:12:28 tobias avahi-daemon[4769]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.71.
Jan 10 22:12:28 tobias avahi-daemon[4769]: New relevant interface wlan1.IPv4 for mDNS.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Registering new address record for 192.168.1.71 on wlan1.IPv4.
Jan 10 22:12:28 tobias NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan1 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) started... 
Jan 10 22:12:28 tobias NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan 10 22:12:28 tobias NetworkManager: <info>    address 192.168.1.71 
Jan 10 22:12:28 tobias NetworkManager: <info>    netmask 255.255.255.0 
Jan 10 22:12:28 tobias NetworkManager: <info>    broadcast 192.168.1.255 
Jan 10 22:12:28 tobias NetworkManager: <info>    gateway 192.168.1.254 
Jan 10 22:12:28 tobias NetworkManager: <info>    nameserver 192.168.1.254 
Jan 10 22:12:28 tobias NetworkManager: <info>    domain name 'gateway.2wire.net' 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) complete. 
Jan 10 22:12:28 tobias NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started... 
Jan 10 22:12:28 tobias avahi-daemon[4769]: Withdrawing address record for 192.168.1.71 on wlan1.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.71.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.71.
Jan 10 22:12:28 tobias avahi-daemon[4769]: New relevant interface wlan1.IPv4 for mDNS.
Jan 10 22:12:28 tobias avahi-daemon[4769]: Registering new address record for 192.168.1.71 on wlan1.IPv4.
Jan 10 22:12:28 tobias dhclient: bound to 192.168.1.71 -- renewal in 33909 seconds.
Jan 10 22:12:29 tobias NetworkManager: <info>  Clearing nscd hosts cache. 
Jan 10 22:12:29 tobias NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan 10 22:12:29 tobias NetworkManager: <info>  Activation (wlan1) successful, device activated. 
Jan 10 22:12:29 tobias NetworkManager: <info>  Activation (wlan1) Finish handler scheduled. 
Jan 10 22:12:29 tobias NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete. 
```

This was found after some time acessing with VNC
```
Jan 12 11:38:53 tobias NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
Jan 12 11:40:19 tobias NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
Jan 12 11:41:51 tobias NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one.
```

This one was after using the VNC to this computer too
```
Jan 13 02:18:06 tobias NetworkManager: <info>  wlan1: link timed out. 
Jan 13 02:18:06 tobias NetworkManager: <info>  SWITCH: found better connection 'wlan1/2WIRE-PT-185' than current connection 'wlan1/2WIRE-PT-185'.  same_ssid=1, have_link=0 
Jan 13 02:18:06 tobias NetworkManager: <info>  Will activate connection 'wlan1/2WIRE-PT-185'. 
Jan 13 02:18:06 tobias NetworkManager: <info>  Device wlan1 activation scheduled... 
Jan 13 02:18:06 tobias NetworkManager: <info>  Deactivating device wlan1. 
Jan 13 02:18:06 tobias dhclient: There is already a pid file /var/run/dhclient.wlan1.pid with pid 5543
Jan 13 02:18:06 tobias dhclient: killed old client process, removed PID file
Jan 13 02:18:06 tobias dhclient: wmaster0: unknown hardware address type 801
Jan 13 02:18:06 tobias dhclient: wmaster0: unknown hardware address type 801
Jan 13 02:18:06 tobias dhclient: DHCPRELEASE on wlan1 to 192.168.1.254 port 67
Jan 13 02:18:06 tobias avahi-daemon[4776]: Withdrawing address record for 192.168.1.71 on wlan1.
Jan 13 02:18:06 tobias avahi-daemon[4776]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.71.
Jan 13 02:18:06 tobias avahi-daemon[4776]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jan 13 02:18:07 tobias NetworkManager: <info>  Activation (wlan1) started... 
Jan 13 02:18:07 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 13 02:18:07 tobias NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan1 
Jan 13 02:18:07 tobias NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface wlan1 
Jan 13 02:18:07 tobias NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan1 
Jan 13 02:18:07 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Jan 13 02:18:07 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 13 02:18:07 tobias NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Jan 13 02:18:07 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Jan 13 02:18:07 tobias NetworkManager: <info>  Activation (wlan1/wireless): access point '2WIRE-PT-185' is encrypted, and a key exists.  No new key needed. 
Jan 13 02:18:08 tobias NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 13 02:18:08 tobias NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant5^I' 
Jan 13 02:18:20 tobias NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Jan 13 02:18:20 tobias NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_interface_init: supplicant error for 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant5^I'.  Response: 'TIMEOUT[CLI]' 
Jan 13 02:18:20 tobias NetworkManager: <WARN>  real_act_stage2_config(): Activation (wlan1/wireless): couldn't connect to the supplicant. 
Jan 13 02:18:20 tobias NetworkManager: <info>  Activation (wlan1) failure scheduled... 
Jan 13 02:18:20 tobias NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Jan 13 02:18:21 tobias NetworkManager: <info>  Activation (wlan1) failed for access point (2WIRE-PT-185) 
Jan 13 02:18:21 tobias NetworkManager: <info>  Activation (wlan1) failed. 
Jan 13 02:18:21 tobias NetworkManager: <info>  Deactivating device wlan1. 
Jan 13 02:18:45 tobias NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device wlan1: Network is down 
Jan 13 02:19:33 tobias last message repeated 2 times
Jan 13 02:20:21 tobias last message repeated 2 times
Jan 13 02:22:26 tobias NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device wlan1: Network is down 
Jan 13 02:24:30 tobias NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless
```

It still detects the wifi network but it can't connect (always asking for the pass key).
After this the only thing I have to do is restarting the computer and everithing goes back to normal, but sometimes I need to unplug the usb pen and plug it in again.

What should I do?

---

### Post by Fc1032 on 2008-01-13
hi, i have the same problems as you... The laptop detects the usb and after some information, it SAYS it has a signal strength but i cant connect to the internet. I have xubuntu, guess it should be the same! I cant even detect the laptop on my main computer. Someone please tell us what to do

---

### Post by Lowell Boggs on 2008-01-13
I am having the same problem as describe above but I'm not using a laptop nor am I using a Dlink G122 -- instead I'm using a Dlink DI-624

I am using an hp-pavillion desk-top which defaults to having lan0 turned off with wireless turned on.  

I am noticing that it takes almost 24 hours after I boot before the wireless lan simple stops talking.

Does anyone know of a way in s/w to simply restart the network?  Rebooting is a real problem as I have  jobs running that take more than 24 hours to complete.

Is there some command that I can use to manually kill and restart the ethernet?

I tried ifconfig wlan0 down, then up but I just get errors.

Thanks,
  Lowell

---

### Post by ram zu on 2008-01-13
I'm using a desktop too.

In the last few days my wireless stays connect until I make some remote connection (???)
I can't have this kind of up and down because I running some servers in this machine and if it goes off some one will get kicked... :)

The problem is that I cant put this machine near the router because the router is in the living room and there is now way I can get a 24h server in to there (my wife will cut me in peaces).

I'm starting to see some PLC devices just in case.

---

### Post by ram zu on 2008-01-14
Lost connection again.

The only thing I think that is weird is;

"Jan 15 02:43:20 tobias NetworkManager: <info>  SWITCH: found better connection 'wlan1/2WIRE-PT-185' than current connection 'wlan1/2WIRE-PT-185'.  same_ssid=1, have_link=0"

The NM found that the AP were I'm connected is better that the on that I'm connected??????
Can someone explain me this one?

Is this a NM bug?

---

