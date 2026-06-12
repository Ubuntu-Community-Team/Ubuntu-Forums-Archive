---
title: "can't connect with 3945ABG"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by ssmith73 on 2007-12-30
Hi everyone
  I have tried multiple distros in an attempt to rid myself of my wired internet connection, it annoys my wife.  I have a Dell Inspiron 9400, using the Intel 3945ABG.  I have set the network up with no security, and the correct ssid is recognised.  I am getting desparate at this state, and i wonder is something wrong with the network card.  When i try to connect it takes forever and fails.  Maybe the syslog will help someone advise me?  Oh and i am using kubuntu 7.10

Cheers

S

ail -f /var/log/syslog
Dec 30 21:02:19 ssmith-laptop dhclient: Listening on LPF/eth1/00:1b:77:20:38:7e
Dec 30 21:02:19 ssmith-laptop dhclient: Sending on   LPF/eth1/00:1b:77:20:38:7e
Dec 30 21:02:19 ssmith-laptop dhclient: Listening on LPF/eth0/00:18:8b:c6:eb:c0
Dec 30 21:02:19 ssmith-laptop dhclient: Sending on   LPF/eth0/00:18:8b:c6:eb:c0
Dec 30 21:02:19 ssmith-laptop dhclient: Sending on   Socket/fallback
Dec 30 21:02:22 ssmith-laptop kernel: [  784.084000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:02:54 ssmith-laptop kernel: [  816.288000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:05:04 ssmith-laptop kernel: [  946.296000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:07:14 ssmith-laptop kernel: [ 1076.296000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:09:24 ssmith-laptop kernel: [ 1206.308000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:10:29 ssmith-laptop NetworkManager: <info>  Updating allowed wireless network lists.
Dec 30 21:10:29 ssmith-laptop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks.
Dec 30 21:10:47 ssmith-laptop NetworkManager: <debug> [1199049047.195062] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'sean'
Dec 30 21:10:47 ssmith-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / sean
Dec 30 21:10:47 ssmith-laptop NetworkManager: <info>  Deactivating device eth1.
Dec 30 21:10:47 ssmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec 30 21:10:47 ssmith-laptop NetworkManager: <info>  Device eth1 activation scheduled...
Dec 30 21:10:47 ssmith-laptop NetworkManager: <info>  Deactivating device eth0.
Dec 30 21:10:47 ssmith-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7984
Dec 30 21:10:47 ssmith-laptop dhclient: killed old client process, removed PID file
Dec 30 21:10:47 ssmith-laptop dhclient: DHCPRELEASE on eth0 to 192.168.1.254 port 67
Dec 30 21:10:47 ssmith-laptop avahi-daemon[5868]: Withdrawing address record for 192.168.1.1 on eth0.
Dec 30 21:10:47 ssmith-laptop avahi-daemon[5868]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.1.
Dec 30 21:10:47 ssmith-laptop avahi-daemon[5868]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 30 21:10:48 ssmith-laptop avahi-daemon[5868]: Withdrawing address record for fe80::218:8bff:fec6:ebc0 on eth0.
Dec 30 21:10:48 ssmith-laptop NetworkManager: <info>  Activation (eth1) started...
Dec 30 21:10:48 ssmith-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Dec 30 21:10:48 ssmith-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Dec 30 21:10:48 ssmith-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Dec 30 21:10:48 ssmith-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Dec 30 21:10:48 ssmith-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Dec 30 21:10:48 ssmith-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'sean' is unencrypted, no key needed.
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10).
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10).
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant6^I'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: response was 'OK'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10).
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: response was 'OK'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: response was '0'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7365616e'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: response was 'OK'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: response was 'OK'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  SUP: response was 'OK'
Dec 30 21:10:49 ssmith-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Dec 30 21:10:56 ssmith-laptop kernel: [ 1298.268000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:11:04 ssmith-laptop kernel: [ 1306.276000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:11:12 ssmith-laptop kernel: [ 1314.284000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:11:20 ssmith-laptop kernel: [ 1322.296000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:11:28 ssmith-laptop kernel: [ 1330.296000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:11:36 ssmith-laptop kernel: [ 1338.308000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:11:44 ssmith-laptop kernel: [ 1346.316000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:11:52 ssmith-laptop kernel: [ 1354.320000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:00 ssmith-laptop kernel: [ 1362.324000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:08 ssmith-laptop kernel: [ 1370.336000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:16 ssmith-laptop kernel: [ 1378.340000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:24 ssmith-laptop kernel: [ 1386.348000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:32 ssmith-laptop kernel: [ 1394.356000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:40 ssmith-laptop kernel: [ 1402.360000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:49 ssmith-laptop kernel: [ 1410.364000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long (>120s), failing activation.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth1) failure scheduled...
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth1) failed for access point (sean)
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth1) failed.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Deactivating device eth1.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Will activate connection 'eth0'.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Device eth0 activation scheduled...
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) started...
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 30 21:12:49 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 30 21:12:50 ssmith-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
Dec 30 21:12:50 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 30 21:12:50 ssmith-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Dec 30 21:12:50 ssmith-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0
Dec 30 21:12:51 ssmith-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0
Dec 30 21:12:52 ssmith-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 30 21:12:52 ssmith-laptop dhclient: DHCPOFFER from 192.168.1.254
Dec 30 21:12:52 ssmith-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Dec 30 21:12:52 ssmith-laptop dhclient: DHCPACK from 192.168.1.254
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.1.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: New relevant interface eth0.IPv4 for mDNS.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Registering new address record for 192.168.1.1 on eth0.IPv4.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Withdrawing address record for 192.168.1.1 on eth0.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.1.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.1.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: New relevant interface eth0.IPv4 for mDNS.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Registering new address record for 192.168.1.1 on eth0.IPv4.
Dec 30 21:12:52 ssmith-laptop dhclient: bound to 192.168.1.1 -- renewal in 1524 seconds.
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started...
Dec 30 21:12:52 ssmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec 30 21:12:52 ssmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Dec 30 21:12:52 ssmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 30 21:12:52 ssmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon:
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>    address 192.168.1.1
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>    netmask 255.255.255.0
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>    broadcast 255.255.255.255
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>    gateway 192.168.1.254
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>    nameserver 192.168.1.254
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Dec 30 21:12:52 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Withdrawing address record for 192.168.1.1 on eth0.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.1.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.1.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: New relevant interface eth0.IPv4 for mDNS.
Dec 30 21:12:52 ssmith-laptop avahi-daemon[5868]: Registering new address record for 192.168.1.1 on eth0.IPv4.
Dec 30 21:12:53 ssmith-laptop NetworkManager: <info>  Clearing nscd hosts cache.
Dec 30 21:12:53 ssmith-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
Dec 30 21:12:53 ssmith-laptop NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
Dec 30 21:12:53 ssmith-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Dec 30 21:12:53 ssmith-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 30 21:12:53 ssmith-laptop ntpdate[8447]: adjust time server 91.189.94.4 offset -0.030064 sec
Dec 30 21:12:54 ssmith-laptop avahi-daemon[5868]: Registering new address record for fe80::218:8bff:fec6:ebc0 on eth0.*.
Dec 30 21:12:57 ssmith-laptop kernel: [ 1418.408000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 30 21:12:57 ssmith-laptop kernel: [ 1418.952000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 30 21:13:03 ssmith-laptop kernel: [ 1425.080000] eth0: no IPv6 routers present
Dec 30 21:13:04 ssmith-laptop kernel: [ 1426.288000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

---

### Post by ssmith73 on 2007-12-30
Is there any program that could help me debug?

---

### Post by ssmith73 on 2007-12-31
any ideas?

---

### Post by kegobeer on 2007-12-31
I have the e1705 with the same card, running Ubuntu 7.10, but I never had any real problems.  I have a DIR-655 router, and I had to make my SSID visible in order to connect.  If I remember correctly (forgive me, I've been doing a lot of trial and error stuff today with my DWA-643), I made a manual configuration with the necessary info, rebooted, then went back to roaming mode.  It think it started working at that point.  I use WPA2/AES and have a solid connection.

What router do you have?

---

### Post by ssmith73 on 2008-01-01
I have a Netopia 2247-02 router - it works fine for my work laptop running XP - this also uses the same wireless card.

---

### Post by Edho on 2008-01-01
The 3945 works good, right after a good install.
With restricted driver , you can check that it's enabled in....
Menu : System...Administration...Restricted Drivers Manager.( Gutsy-7.10)

I did a download to test...700 Mb...fast and no errors.

There are meny threads here Howto check and configure your wireles network.

Please read and learn.

---

