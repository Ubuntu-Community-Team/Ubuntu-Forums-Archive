---
title: "[SOLVED] Networking daemon"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Mr.Pickels on 2008-09-03
I am brand new to Ubuntu and I find it has some troubles.  Durring a reboot or shutdown I can see a few warnings and errors, and I'll end up rebooting the box manually as it seams to get stuck.

I've looked around the system logs and found the following, but I can't decipher it...

Sep  3 00:35:34 GregUbuntu NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list. 
Sep  3 00:35:34 GregUbuntu NetworkManager: <WARN>  ifparser_init(): Error: Can't parse inet line 'inet'  
Sep  3 00:35:34 GregUbuntu NetworkManager: <info>  Removing wired Ethernet (802.3) device 'eth0'. 
Sep  3 00:35:34 GregUbuntu NetworkManager: <info>  Deactivating device eth0. 
Sep  3 00:35:34 GregUbuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5581
Sep  3 00:35:34 GregUbuntu dhclient: killed old client process, removed PID file
Sep  3 00:35:34 GregUbuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Sep  3 00:35:34 GregUbuntu dhclient: Internet Systems Consortium DHCP Client V3.0.6
Sep  3 00:35:34 GregUbuntu dhclient: Copyright 2004-2007 Internet Systems Consortium.
Sep  3 00:35:34 GregUbuntu dhclient: All rights reserved.
Sep  3 00:35:34 GregUbuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Sep  3 00:35:34 GregUbuntu dhclient: 
Sep  3 00:35:34 GregUbuntu avahi-daemon[5262]: Withdrawing address record for 192.168.81.103 on eth0.
Sep  3 00:35:34 GregUbuntu avahi-daemon[5262]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.81.103.
Sep  3 00:35:34 GregUbuntu avahi-daemon[5262]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep  3 00:35:34 GregUbuntu dhclient: DHCPRELEASE on eth0 to 192.168.81.1 port 67
Sep  3 00:35:34 GregUbuntu dhclient: send_packet: Network is unreachable
Sep  3 00:35:34 GregUbuntu dhclient: send_packet: please consult README file regarding broadcast address.
Sep  3 00:35:35 GregUbuntu avahi-daemon[5262]: Withdrawing address record for fe80::21d:92ff:fe73:ecd0 on eth0.
Sep  3 00:35:35 GregUbuntu NetworkManager: <info>  Recreating the device list. 
Sep  3 00:35:35 GregUbuntu dhclient: Listening on LPF/eth0/00:1d:92:73:ec:d0
Sep  3 00:35:35 GregUbuntu dhclient: Sending on   LPF/eth0/00:1d:92:73:ec:d0
Sep  3 00:35:35 GregUbuntu dhclient: Sending on   Socket/fallback
Sep  3 00:35:35 GregUbuntu dhclient: DHCPREQUEST of 192.168.81.103 on eth0 to 255.255.255.255 port 67
Sep  3 00:35:35 GregUbuntu dhclient: send_packet: Network is down
Sep  3 00:35:35 GregUbuntu dhclient: receive_packet failed on eth0: Network is down
Sep  3 00:35:35 GregUbuntu NetworkManager: <info>  Device list recreated successfully. 
Sep  3 00:35:35 GregUbuntu NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list. 
Sep  3 00:35:35 GregUbuntu NetworkManager: <info>  Recreating the device list. 
Sep  3 00:35:35 GregUbuntu NetworkManager: <info>  Device list recreated successfully. 
Sep  3 00:35:37 GregUbuntu avahi-daemon[5262]: Registering new address record for fe80::21d:92ff:fe73:ecd0 on eth0.*.
Sep  3 00:35:43 GregUbuntu dhclient: DHCPREQUEST of 192.168.81.103 on eth0 to 255.255.255.255 port 67
Sep  3 00:35:43 GregUbuntu dhclient: DHCPACK of 192.168.81.103 from 192.168.81.1
Sep  3 00:35:43 GregUbuntu avahi-daemon[5262]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.81.103.
Sep  3 00:35:43 GregUbuntu avahi-daemon[5262]: New relevant interface eth0.IPv4 for mDNS.
Sep  3 00:35:43 GregUbuntu avahi-daemon[5262]: Registering new address record for 192.168.81.103 on eth0.IPv4.
Sep  3 00:35:43 GregUbuntu dhclient: bound to 192.168.81.103 -- renewal in 39579 seconds.
Sep  3 00:35:43 GregUbuntu ntpdate[6970]: step time server 91.189.94.4 offset -0.576403 sec
Sep  3 00:35:45 GregUbuntu NetworkManager: <info>  Going to sleep. 
Sep  3 00:35:45 GregUbuntu NetworkManager: <info>  Waking up from sleep. 
Sep  3 01:03:52 GregUbuntu NetworkManager: <info>  Updating allowed wireless network lists. 
Sep  3 01:03:52 GregUbuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep  3 01:51:15 GregUbuntu NetworkManager: <debug> [1220431875.540937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_797D_1AE3'). 
Sep  3 01:51:15 GregUbuntu hald: mounted /dev/sdd1 on behalf of uid 1000
Sep  3 01:51:56 GregUbuntu hald: unmounted /dev/sdd1 from '/media/CANON_DC' on behalf of uid 1000
Sep  3 01:52:05 GregUbuntu NetworkManager: <debug> [1220431925.050591] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_797D_1AE3'). 
Sep  3 01:54:52 GregUbuntu NetworkManager: <debug> [1220432092.879058] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_BITTER_FILMS_VOL_1'). 
Sep  3 02:24:01 GregUbuntu NetworkManager: <debug> [1220433841.880929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_X2_DISC1'). 
Sep  3 09:30:33 GregUbuntu init: tty4 main process (4813) killed by TERM signal
Sep  3 09:30:33 GregUbuntu init: tty5 main process (4814) killed by TERM signal
Sep  3 09:30:33 GregUbuntu init: tty2 main process (4818) killed by TERM signal
Sep  3 09:30:33 GregUbuntu init: tty3 main process (4819) killed by TERM signal
Sep  3 09:30:33 GregUbuntu init: tty6 main process (4820) killed by TERM signal
Sep  3 09:30:33 GregUbuntu init: tty1 main process (5718) killed by TERM signal
Sep  3 09:30:34 GregUbuntu avahi-daemon[5262]: Got SIGTERM, quitting.
Sep  3 09:30:34 GregUbuntu avahi-daemon[5262]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.81.103.
Sep  3 09:30:35 GregUbuntu gdm[18876]: CRITICAL: gdm_connection_close: assertion `conn != NULL' failed 
Sep  3 09:30:35 GregUbuntu last message repeated 2 times
Sep  3 09:30:35 GregUbuntu gdm[18876]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Sep  3 09:30:35 GregUbuntu gdm[18876]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Sep  3 09:30:35 GregUbuntu gdm[18876]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Sep  3 09:30:35 GregUbuntu gdm[18876]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Sep  3 09:30:36 GregUbuntu gdm[18876]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Sep  3 09:30:36 GregUbuntu gdm[18876]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Sep  3 09:30:36 GregUbuntu gdm[18876]: WARNING: gdm_slave_send: Can't open fifo! 
Sep  3 09:30:36 GregUbuntu gdm[18876]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Sep  3 09:30:36 GregUbuntu gdm[18876]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Sep  3 09:30:36 GregUbuntu gdm[18876]: WARNING: gdm_auth_secure_display: Cannot safely open  
Sep  3 09:30:36 GregUbuntu gdm[18876]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Sep  3 09:30:36 GregUbuntu gdm[18876]: WARNING: Request for invalid configuration key daemon/ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh 
Sep  3 09:30:36 GregUbuntu gdm[18876]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Sep  3 09:30:36 GregUbuntu gdm[18876]: WARNING: Request for invalid configuration key daemon/ConsoleNotify=true 
Sep  3 09:34:38 GregUbuntu ntpdate[4887]: step time server 91.189.94.4 offset -4.180699 sec
Sep  3 09:34:38 GregUbuntu NetworkManager: <info>  starting... 
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Successfully dropped root privileges.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: avahi-daemon 0.6.22 starting up.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Successfully called chroot().
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Successfully dropped remaining capabilities.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: No service file found in /etc/avahi/services.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.81.103.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: New relevant interface eth0.IPv4 for mDNS.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Network interface enumeration completed.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Registering new address record for fe80::21d:92ff:fe73:ecd0 on eth0.*.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Registering new address record for 192.168.81.103 on eth0.IPv4.
Sep  3 09:34:38 GregUbuntu avahi-daemon[5347]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep  3 09:34:39 GregUbuntu avahi-daemon[5347]: Server startup complete. Host name is GregUbuntu.local. Local service cookie is 4166250442.
Sep  3 09:34:39 GregUbuntu NetworkManager: <debug> [1220459679.560214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RAM_GSA_H55L'). 
Sep  3 09:45:35 GregUbuntu NetworkManager: <info>  Updating allowed wireless network lists. 
Sep  3 09:45:35 GregUbuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep  3 09:46:40 GregUbuntu ntfs-3g[6098]: Version 1.2216 external FUSE 27 
Sep  3 09:46:40 GregUbuntu ntfs-3g[6098]: Mounted /dev/sda2 (Read-Write, label "Disk0_Part2", NTFS 3.1) 
Sep  3 09:46:40 GregUbuntu ntfs-3g[6098]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_CA.UTF-8 
Sep  3 09:46:40 GregUbuntu ntfs-3g[6098]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/sda2,blkdev,blksize=4096 
Sep  3 09:46:40 GregUbuntu hald: mounted /dev/sda2 on behalf of uid 1000


I'm running an on-board 10/100 NIC, no wifi to worry about.
Connecting to a Linksys 4 port Router

---

