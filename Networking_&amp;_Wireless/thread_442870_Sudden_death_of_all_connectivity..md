---
title: "Sudden death of all connectivity."
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by decall07 on 2007-05-13
I am using an old DELL laptop with a built-in network card. My version of ubuntu is 7.04. And I am using all default settings.

My internet connection was working fine until I came home from work one day and found a solid dark orange light on my network card on the left and a flashing orange light on the right. The connection still receives packages according to my network applet but it is not sending anything out.. I check the wires, reset the modem, tried a different wire, tried the docking station ethernet port, attempted to use the usb option on the modem, and purchased a pci network card.  None of these actions helped at all. I am still without an internet connection... and still very frustrated. . Any suggestions would be appreciate. Here is a sample of what seemed important from my daemon.log files (it is a lot, I know):

May 12 06:55:14 SOC NetworkManager: <information>^Istarting... 
May 12 06:55:14 SOC NetworkManager: <information>^Ieth2: Device is fully-supported using driver '8139too'. 
May 12 06:55:14 SOC NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 12 06:55:14 SOC NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 12 06:55:14 SOC NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth2'. 
May 12 06:55:14 SOC NetworkManager: <information>^IDeactivating device eth2. 
May 12 06:55:14 SOC avahi-daemon[4556]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May 12 06:55:14 SOC avahi-daemon[4556]: Successfully dropped root privileges.
May 12 06:55:14 SOC avahi-daemon[4556]: avahi-daemon 0.6.17 starting up.
May 12 06:55:14 SOC avahi-daemon[4556]: Successfully called chroot().
May 12 06:55:14 SOC avahi-daemon[4556]: Successfully dropped remaining capabilities.
May 12 06:55:14 SOC avahi-daemon[4557]: chroot.c: open() failed: No such file or directory
May 12 06:55:14 SOC avahi-daemon[4556]: Failed to open /etc/resolv.conf: Invalid argument
May 12 06:55:14 SOC NetworkManager: <information>^Ieth1: Device is fully-supported using driver '3c59x'. 
May 12 06:55:14 SOC NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 12 06:55:14 SOC avahi-daemon[4556]: No service found in /etc/avahi/services.
May 12 06:55:14 SOC avahi-daemon[4556]: Network interface enumeration completed.
May 12 06:55:14 SOC avahi-daemon[4556]: Registering HINFO record with values 'I686'/'LINUX'.
May 12 06:55:14 SOC avahi-daemon[4556]: Server startup complete. Host name is SOC.local. Local service cookie is 1360535740.
May 12 06:55:14 SOC NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 12 06:55:14 SOC NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth1'. 
May 12 06:55:14 SOC NetworkManager: <information>^IDeactivating device eth1. 
May 12 06:55:14 SOC NetworkManager: <information>^Ieth0: Device is fully-supported using driver '3c59x'. 
May 12 06:55:14 SOC NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 12 06:55:14 SOC NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 12 06:55:14 SOC NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
May 12 06:55:14 SOC NetworkManager: <information>^IDeactivating device eth0. 
May 12 06:55:14 SOC NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
May 12 06:55:14 SOC NetworkManager: <information>^IWill activate wired connection 'eth2' because it now has a link. 
May 12 06:55:14 SOC NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth2'. 
May 12 06:55:14 SOC NetworkManager: <information>^IWill activate connection 'eth2'. 
May 12 06:55:14 SOC NetworkManager: <information>^IDevice eth2 activation scheduled... 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) started... 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) successful. 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 12 06:55:14 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) started... 
May 12 06:55:15 SOC NetworkManager: <information>^IActivation (eth2) Beginning DHCP transaction. 
May 12 06:55:15 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
May 12 06:55:15 SOC NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth2 
May 12 06:55:16 SOC NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth2 
May 12 06:55:17 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
May 12 06:55:19 SOC hcid[4876]: Bluetooth HCI daemon
May 12 06:55:19 SOC NetworkManager: <debug info>^I[1178967319.213838] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 12 06:55:19 SOC hcid[4876]: Starting SDP server
May 12 06:55:21 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
May 12 06:55:31 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
May 12 06:55:35 SOC avahi-daemon[4556]: Registering new address record for fe80::219:5bff:fe0a:30f9 on eth2.*.
May 12 06:55:37 SOC hald: mounted /dev/sdc1 on behalf of uid 1000
May 12 06:55:37 SOC hald: mounted /dev/sdb1 on behalf of uid 1000
May 12 06:55:42 SOC NetworkManager: <information>^IUpdating allowed wireless network lists. 
May 12 06:55:42 SOC NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 12 06:55:43 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
May 12 06:55:47 SOC dhclient: No DHCPOFFERS received.
May 12 06:55:47 SOC avahi-autoipd(eth2)[5264]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May 12 06:55:47 SOC avahi-autoipd(eth2)[5264]: Successfully called chroot().
May 12 06:55:47 SOC avahi-autoipd(eth2)[5264]: Successfully dropped root privileges.
May 12 06:55:47 SOC avahi-autoipd(eth2)[5264]: fopen() failed: Permission denied
May 12 06:55:47 SOC avahi-autoipd(eth2)[5264]: Starting with address 169.254.6.139
May 12 06:55:53 SOC avahi-autoipd(eth2)[5264]: Callout BIND, address 169.254.6.139 on interface eth2
May 12 06:55:53 SOC avahi-daemon[4556]: Joining mDNS multicast group on interface eth2.IPv4 with address 169.254.6.139.
May 12 06:55:53 SOC avahi-daemon[4556]: New relevant interface eth2.IPv4 for mDNS.
May 12 06:55:53 SOC avahi-daemon[4556]: Registering new address record for 169.254.6.139 on eth2.IPv4.
May 12 06:55:57 SOC avahi-autoipd(eth2)[5264]: Successfully claimed IP address 169.254.6.139
May 12 06:55:57 SOC avahi-autoipd(eth2)[5264]: fopen() failed: Permission denied
May 12 06:55:57 SOC NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth2 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) started... 
May 12 06:55:57 SOC NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf. 
May 12 06:55:57 SOC NetworkManager: <information>^Iavahi-autoipd running on eth2, assuming IPv4LL address 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) complete. 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) started... 
May 12 06:55:57 SOC NetworkManager: <information>^Inot touching eth2 configuration, was configured externally 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) Finish handler scheduled. 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) complete. 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 12 06:55:57 SOC NetworkManager: <information>^IActivation (eth2) successful, device activated. 
May 12 06:55:57 SOC NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth2 
May 12 06:56:10 SOC ntpdate[5325]: can't find host ntp.ubuntu.com 
May 12 06:56:10 SOC ntpdate[5325]: no servers can be used, exiting
May 12 07:09:43 SOC hcid[4876]: Stopping SDP server
May 12 07:09:43 SOC hcid[4876]: Unregister path: /org/bluez
May 12 07:09:43 SOC hcid[4876]: Exit
May 12 07:21:37 SOC NetworkManager: <debug info>^I[1178968897.719404] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Ubuntu_7_04_i386'). 
May 12 07:37:17 SOC init: tty1 main process ended, respawning
May 12 07:37:36 SOC init: tty3 main process ended, respawning
May 12 07:38:05 SOC hald: unmounted /dev/sdc1 from '/media/DEC'S EXT' on behalf of uid 1000
May 12 07:38:05 SOC hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
May 12 07:38:45 SOC hald: mounted /dev/sdb1 on behalf of uid 1000
May 12 07:38:46 SOC hald: mounted /dev/sdc1 on behalf of uid 1000
May 12 07:38:47 SOC NetworkManager: <information>^IUpdating allowed wireless network lists. 
May 12 07:38:47 SOC NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 12 07:45:44 SOC NetworkManager: <debug info>^I[1178970344.693402] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_Ubuntu_7_04_i386'). 
May 12 08:19:46 SOC NetworkManager: <information>^ISWITCH: terminating current connection 'eth2' because it's no longer valid. 
May 12 08:19:46 SOC NetworkManager: <information>^IDeactivating device eth2. 
May 12 08:19:46 SOC NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
May 12 08:19:46 SOC NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
May 12 08:19:46 SOC avahi-daemon[4556]: Withdrawing address record for 169.254.6.139 on eth2.
May 12 08:19:46 SOC avahi-daemon[4556]: Leaving mDNS multicast group on interface eth2.IPv4 with address 169.254.6.139.
May 12 08:19:46 SOC avahi-daemon[4556]: Interface eth2.IPv4 no longer relevant for mDNS.
May 12 08:19:46 SOC avahi-daemon[4556]: Withdrawing address record for fe80::219:5bff:fe0a:30f9 on eth2.
May 12 08:19:54 SOC NetworkManager: <information>^IWill activate wired connection 'eth2' because it now has a link. 
May 12 08:19:54 SOC NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth2'. 
May 12 08:19:54 SOC NetworkManager: <information>^IWill activate connection 'eth2'. 
May 12 08:19:54 SOC NetworkManager: <information>^IDevice eth2 activation scheduled... 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) started... 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) successful. 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 12 08:19:54 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) started... 
May 12 08:19:55 SOC avahi-daemon[4556]: Registering new address record for fe80::219:5bff:fe0a:30f9 on eth2.*.
May 12 08:19:56 SOC NetworkManager: <information>^IActivation (eth2) Beginning DHCP transaction. 
May 12 08:19:56 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
May 12 08:19:56 SOC NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth2 
May 12 08:19:56 SOC avahi-autoipd(eth2)[5264]: Got SIGTERM, quitting.
May 12 08:19:56 SOC avahi-autoipd(eth2)[5264]: Callout STOP, address 169.254.6.139 on interface eth2
May 12 08:19:56 SOC avahi-autoipd(eth2)[5265]: client: RTNETLINK answers: No such device
May 12 08:19:56 SOC avahi-autoipd(eth2)[5265]: Script execution failed with return value 2
May 12 08:19:57 SOC NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth2 
May 12 08:19:59 SOC NetworkManager: <information>^IOld device 'eth2' activating, won't change. 
May 12 08:20:01 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
May 12 08:20:06 SOC NetworkManager: <information>^IOld device 'eth2' activating, won't change. 
May 12 08:20:07 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
May 12 08:20:19 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 13
May 12 08:20:32 SOC dhclient: No DHCPOFFERS received.
May 12 08:20:32 SOC avahi-autoipd(eth2)[9321]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May 12 08:20:32 SOC avahi-autoipd(eth2)[9321]: Successfully called chroot().
May 12 08:20:32 SOC avahi-autoipd(eth2)[9321]: Successfully dropped root privileges.
May 12 08:20:32 SOC avahi-autoipd(eth2)[9321]: fopen() failed: Permission denied
May 12 08:20:32 SOC avahi-autoipd(eth2)[9321]: Starting with address 169.254.6.139
May 12 08:20:37 SOC avahi-autoipd(eth2)[9321]: Callout BIND, address 169.254.6.139 on interface eth2
May 12 08:20:37 SOC avahi-daemon[4556]: Joining mDNS multicast group on interface eth2.IPv4 with address 169.254.6.139.
May 12 08:20:37 SOC avahi-daemon[4556]: New relevant interface eth2.IPv4 for mDNS.
May 12 08:20:37 SOC avahi-daemon[4556]: Registering new address record for 169.254.6.139 on eth2.IPv4.
May 12 08:20:41 SOC avahi-autoipd(eth2)[9321]: Successfully claimed IP address 169.254.6.139
May 12 08:20:41 SOC avahi-autoipd(eth2)[9321]: fopen() failed: Permission denied
May 12 08:20:41 SOC NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth2 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) started... 
May 12 08:20:41 SOC NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf. 
May 12 08:20:41 SOC NetworkManager: <information>^Iavahi-autoipd running on eth2, assuming IPv4LL address 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) complete. 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) started... 
May 12 08:20:41 SOC NetworkManager: <information>^Inot touching eth2 configuration, was configured externally 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) Finish handler scheduled. 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) complete. 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 12 08:20:41 SOC NetworkManager: <information>^IActivation (eth2) successful, device activated. 
May 12 08:20:41 SOC NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth2 
May 12 08:20:54 SOC ntpdate[9347]: can't find host ntp.ubuntu.com 
May 12 08:20:54 SOC ntpdate[9347]: no servers can be used, exiting
May 12 08:22:04 SOC avahi-daemon[4556]: Got SIGTERM, quitting.
May 12 08:22:04 SOC avahi-daemon[4556]: Leaving mDNS multicast group on interface eth2.IPv4 with address 169.254.6.139.
May 12 08:23:02 SOC NetworkManager: <information>^ISWITCH: terminating current connection 'eth2' because it's no longer valid. 
May 12 08:23:02 SOC NetworkManager: <information>^IDeactivating device eth2. 
May 12 08:23:02 SOC NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
May 12 08:23:02 SOC NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
May 12 08:24:47 SOC NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
May 12 08:24:47 SOC NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
May 12 08:24:47 SOC NetworkManager: <information>^IWill activate connection 'eth0'. 
May 12 08:24:47 SOC NetworkManager: <information>^IDevice eth0 activation scheduled... 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) started... 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 12 08:24:47 SOC NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 12 08:24:48 SOC NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
May 12 08:24:48 SOC NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 12 08:24:48 SOC NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
May 12 08:24:50 SOC NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
May 12 08:24:54 SOC dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 12 08:25:02 SOC dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 12 08:25:12 SOC dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 12 08:25:22 SOC dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 12 08:25:25 SOC dhclient: No DHCPOFFERS received.
May 12 08:25:25 SOC avahi-autoipd(eth0)[9479]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May 12 08:25:25 SOC avahi-autoipd(eth0)[9479]: Successfully called chroot().
May 12 08:25:25 SOC avahi-autoipd(eth0)[9479]: Successfully dropped root privileges.
May 12 08:25:25 SOC avahi-autoipd(eth0)[9479]: fopen() failed: Permission denied
May 12 08:25:25 SOC avahi-autoipd(eth0)[9479]: Starting with address 169.254.4.24
May 12 08:25:30 SOC avahi-autoipd(eth0)[9479]: Callout BIND, address 169.254.4.24 on interface eth0
May 12 08:25:34 SOC avahi-autoipd(eth0)[9479]: Successfully claimed IP address 169.254.4.24
May 12 08:25:34 SOC avahi-autoipd(eth0)[9479]: fopen() failed: Permission denied
May 12 08:25:34 SOC NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth0 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
May 12 08:25:34 SOC NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf. 
May 12 08:25:34 SOC NetworkManager: <information>^Iavahi-autoipd running on eth0, assuming IPv4LL address 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May 12 08:25:34 SOC NetworkManager: <information>^Inot touching eth0 configuration, was configured externally 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May 12 08:25:34 SOC NetworkManager: <information>^IActivation (eth0) successful, device activated. 
May 12 08:25:34 SOC NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
May 12 08:25:34 SOC ntpdate[9500]: can't find host ntp.ubuntu.com 
May 12 08:25:34 SOC ntpdate[9500]: no servers can be used, exiting
May 12 08:25:47 SOC NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
May 12 08:25:47 SOC NetworkManager: <information>^IDeactivating device eth0. 
May 12 08:25:48 SOC NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
May 12 08:25:48 SOC NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
May 12 08:26:07 SOC NetworkManager: <information>^IWill activate wired connection 'eth2' because it now has a link. 
May 12 08:26:07 SOC NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth2'. 
May 12 08:26:07 SOC NetworkManager: <information>^IWill activate connection 'eth2'. 
May 12 08:26:07 SOC NetworkManager: <information>^IDevice eth2 activation scheduled... 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) started... 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) successful. 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 12 08:26:07 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) started... 
May 12 08:26:09 SOC NetworkManager: <information>^IActivation (eth2) Beginning DHCP transaction. 
May 12 08:26:09 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
May 12 08:26:09 SOC NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth2 
May 12 08:26:09 SOC avahi-autoipd(eth2)[9321]: Got SIGTERM, quitting.
May 12 08:26:09 SOC avahi-autoipd(eth2)[9321]: Callout STOP, address 169.254.6.139 on interface eth2
May 12 08:26:09 SOC avahi-autoipd(eth2)[9322]: client: RTNETLINK answers: No such device
May 12 08:26:09 SOC avahi-autoipd(eth2)[9322]: Script execution failed with return value 2
May 12 08:26:10 SOC NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth2 
May 12 08:26:11 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
May 12 08:26:15 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
May 12 08:26:22 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
May 12 08:26:37 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
May 12 08:26:41 SOC NetworkManager: <information>^IOld device 'eth2' activating, won't change. 
May 12 08:26:42 SOC dhclient: No DHCPOFFERS received.
May 12 08:26:42 SOC avahi-autoipd(eth2)[9548]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May 12 08:26:42 SOC avahi-autoipd(eth2)[9548]: Successfully called chroot().
May 12 08:26:42 SOC avahi-autoipd(eth2)[9548]: Successfully dropped root privileges.
May 12 08:26:42 SOC avahi-autoipd(eth2)[9548]: fopen() failed: Permission denied
May 12 08:26:42 SOC avahi-autoipd(eth2)[9548]: Starting with address 169.254.6.139
May 12 08:26:47 SOC avahi-autoipd(eth2)[9548]: Callout BIND, address 169.254.6.139 on interface eth2
May 12 08:26:51 SOC avahi-autoipd(eth2)[9548]: Successfully claimed IP address 169.254.6.139
May 12 08:26:51 SOC avahi-autoipd(eth2)[9548]: fopen() failed: Permission denied
May 12 08:26:51 SOC NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth2 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) started... 
May 12 08:26:51 SOC NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf. 
May 12 08:26:51 SOC NetworkManager: <information>^Iavahi-autoipd running on eth2, assuming IPv4LL address 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) complete. 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) started... 
May 12 08:26:51 SOC NetworkManager: <information>^Inot touching eth2 configuration, was configured externally 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) Finish handler scheduled. 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) complete. 
May 12 08:26:51 SOC NetworkManager: <information>^IActivation (eth2) successful, device activated. 
May 12 08:26:51 SOC NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth2 
May 12 08:26:51 SOC ntpdate[9569]: can't find host ntp.ubuntu.com 
May 12 08:26:51 SOC ntpdate[9569]: no servers can be used, exiting
May 12 08:43:43 SOC hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
May 12 08:43:43 SOC hald: unmounted /dev/sdc1 from '/media/DEC'S EXT' on behalf of uid 1000
May 12 08:43:45 SOC NetworkManager: <debug info>^I[1178973825.772776] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_355B_3CF8'). 
May 12 08:43:48 SOC gdm[4657]: Master halting...
May 12 08:43:52 SOC init: tty4 main process (4009) killed by TERM signal
May 12 08:43:52 SOC init: tty5 main process (4010) killed by TERM signal
May 12 08:43:52 SOC init: tty2 main process (4013) killed by TERM signal
May 12 08:43:52 SOC init: tty6 main process (4016) killed by TERM signal
May 12 08:43:52 SOC init: tty3 main process (8973) killed by TERM signal
May 12 08:43:52 SOC init: tty1 main process (8927) killed by TERM signal
May 12 19:09:55 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
May 12 19:09:59 SOC NetworkManager: <information>^Istarting... 
May 12 19:09:59 SOC NetworkManager: <information>^Ieth2: Device is fully-supported using driver '8139too'. 
May 12 19:09:59 SOC NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 12 19:09:59 SOC NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 12 19:09:59 SOC NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth2'. 
May 12 19:09:59 SOC NetworkManager: <information>^IDeactivating device eth2. 
May 12 19:09:59 SOC NetworkManager: <information>^Ieth1: Device is fully-supported using driver '3c59x'. 
May 12 19:09:59 SOC NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 12 19:10:00 SOC NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 12 19:10:00 SOC NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth1'. 
May 12 19:10:00 SOC NetworkManager: <information>^IDeactivating device eth1. 
May 12 19:10:00 SOC NetworkManager: <information>^Ieth0: Device is fully-supported using driver '3c59x'. 
May 12 19:10:00 SOC NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 12 19:10:00 SOC NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 12 19:10:00 SOC NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
May 12 19:10:00 SOC NetworkManager: <information>^IDeactivating device eth0. 
May 12 19:10:00 SOC NetworkManager: <information>^IWill activate wired connection 'eth2' because it now has a link. 
May 12 19:10:00 SOC NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth2'. 
May 12 19:10:00 SOC NetworkManager: <information>^IWill activate connection 'eth2'. 
May 12 19:10:00 SOC NetworkManager: <information>^IDevice eth2 activation scheduled... 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) started... 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) successful. 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 12 19:10:00 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) started... 
May 12 19:10:01 SOC NetworkManager: <information>^IActivation (eth2) Beginning DHCP transaction. 
May 12 19:10:01 SOC dhclient: There is already a pid file /var/run/dhclient.eth2.pid with pid 134993440
May 12 19:10:01 SOC NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
May 12 19:10:01 SOC NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth2 
May 12 19:10:02 SOC NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth2 
May 12 19:10:03 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
May 12 19:10:06 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
May 12 19:10:12 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
May 12 19:10:12 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
May 12 19:10:21 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
May 12 19:10:26 SOC dhclient: No DHCPOFFERS received.
May 12 19:10:26 SOC dhclient: No working leases in persistent database - sleeping.
May 12 19:10:26 SOC avahi-autoipd(eth2)[4894]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May 12 19:10:26 SOC avahi-autoipd(eth2)[4894]: Successfully called chroot().
May 12 19:10:26 SOC avahi-autoipd(eth2)[4894]: Successfully dropped root privileges.
May 12 19:10:26 SOC avahi-autoipd(eth2)[4894]: fopen() failed: Permission denied
May 12 19:10:26 SOC avahi-autoipd(eth2)[4894]: Starting with address 169.254.6.139
May 12 19:10:27 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
May 12 19:10:31 SOC avahi-autoipd(eth2)[4894]: Callout BIND, address 169.254.6.139 on interface eth2
May 12 19:10:35 SOC avahi-autoipd(eth2)[4894]: Successfully claimed IP address 169.254.6.139
May 12 19:10:35 SOC avahi-autoipd(eth2)[4894]: fopen() failed: Permission denied
May 12 19:10:35 SOC ntpdate[4911]: can't find host ntp.ubuntu.com 
May 12 19:10:35 SOC ntpdate[4911]: no servers can be used, exiting
May 12 19:10:37 SOC dhclient: No DHCPOFFERS received.
May 12 19:10:37 SOC NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth2 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) started... 
May 12 19:10:37 SOC NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf. 
May 12 19:10:37 SOC NetworkManager: <information>^Iavahi-autoipd running on eth2, assuming IPv4LL address 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) complete. 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) started... 
May 12 19:10:37 SOC NetworkManager: <information>^Inot touching eth2 configuration, was configured externally 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) Finish handler scheduled. 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) Stage 5 of 5 (IP Configure Commit) complete. 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 12 19:10:37 SOC NetworkManager: <information>^IActivation (eth2) successful, device activated. 
May 12 19:10:37 SOC NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth2 
May 12 19:10:37 SOC ntpdate[4941]: can't find host ntp.ubuntu.com 
May 12 19:10:37 SOC ntpdate[4941]: no servers can be used, exiting
May 12 19:12:40 SOC hald: mounted /dev/sdb1 on behalf of uid 1000
May 12 19:12:45 SOC NetworkManager: <information>^IUpdating allowed wireless network lists. 
May 12 19:12:45 SOC NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 12 19:17:21 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
May 12 19:17:26 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
May 12 19:17:32 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
May 12 19:17:46 SOC dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
May 12 19:17:52 SOC dhclient: No DHCPOFFERS received.
May 12 19:17:52 SOC dhclient: No working leases in persistent database - sleeping.

---

### Post by netsoul on 2007-05-14
The same thing happened with my Toshiba laptop right after I installed latest HAL updates.  Now I have "Failed to initialize HAL" error and no connections (both wi-fi and Ethernet)

---

### Post by decall07 on 2007-05-16
Mine was just random. I came home from work and noticed it.. Does anyone have any solutions?

---

