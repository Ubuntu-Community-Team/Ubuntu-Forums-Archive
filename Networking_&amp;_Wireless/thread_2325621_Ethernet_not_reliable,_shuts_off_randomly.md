---
title: "Ethernet not reliable, shuts off randomly"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by noah_overcash2 on 2016-05-23
Hey,
I'm using my Ethernet port (Broadcom NIC NetXtreme BCM57781) and it connects for about a minute, then disconnects randomly.  I've tried using wicd and network-manager.

I'm not sure what all commands to run, but I'll do what I know.
cat /var/log/wicd/wicd.log
```
[COLOR=#000000]2016/05/23 20:49:34 :: [/COLOR]2016/05/23 20:49:34 :: wicd initializing...
2016/05/23 20:49:34 :: ---------------------------
2016/05/23 20:49:34 :: wicd is version 1.7.2.4 768
2016/05/23 20:49:34 :: setting backend to external
2016/05/23 20:49:34 :: trying to load backend external
2016/05/23 20:49:34 :: successfully loaded backend external
2016/05/23 20:49:34 :: WARNING: No path found for dhcpcd
2016/05/23 20:49:34 :: WARNING: No path found for pump
2016/05/23 20:49:34 :: WARNING: No path found for udhcpc
2016/05/23 20:49:34 :: WARNING: No path found for kdesu
2016/05/23 20:49:34 :: WARNING: No path found for ktsuss
2016/05/23 20:49:34 :: trying to load backend external
2016/05/23 20:49:34 :: successfully loaded backend external
2016/05/23 20:49:34 :: WARNING: No path found for dhcpcd
2016/05/23 20:49:34 :: WARNING: No path found for pump
2016/05/23 20:49:34 :: WARNING: No path found for udhcpc
2016/05/23 20:49:34 :: WARNING: No path found for kdesu
2016/05/23 20:49:34 :: WARNING: No path found for ktsuss
2016/05/23 20:49:34 :: Couldn't detect a wireless interface.
2016/05/23 20:49:34 :: setting wireless interface None
2016/05/23 20:49:34 :: automatically detected wired interface eth0
2016/05/23 20:49:34 :: setting wired interface eth0
2016/05/23 20:49:34 :: setting wpa driver wext
2016/05/23 20:49:35 :: setting use global dns to False
2016/05/23 20:49:35 :: setting global dns
2016/05/23 20:49:35 :: global dns servers are None None None
2016/05/23 20:49:35 :: domain is None
2016/05/23 20:49:35 :: search domain is None
2016/05/23 20:49:35 :: setting automatically reconnect when connection drops True
2016/05/23 20:49:35 :: found wired_connect_mode in configuration 1
2016/05/23 20:49:35 :: found should_verify_ap in configuration 1
2016/05/23 20:49:35 :: Setting dhcp client to 0
2016/05/23 20:49:36 :: found show_never_connect in configuration True
2016/05/23 20:49:37 :: Wireless configuration file found...
2016/05/23 20:49:37 :: Wired configuration file found...
2016/05/23 20:49:37 :: chmoding configuration files 0600...
2016/05/23 20:49:37 :: chowning configuration files root:root...
2016/05/23 20:49:37 :: Using wireless interface...
2016/05/23 20:49:37 :: Using wired interface...eth0
2016/05/23 20:49:37 :: scanning start
2016/05/23 20:49:37 :: scanning done
2016/05/23 20:49:37 :: found 0 networks:
2016/05/23 20:49:42 :: ifconfig eth0
2016/05/23 20:49:47 :: ifconfig eth0
2016/05/23 20:49:52 :: ifconfig eth0
2016/05/23 20:49:57 :: ifconfig eth0
2016/05/23 20:50:02 :: ifconfig eth0
2016/05/23 20:50:07 :: ifconfig eth0
2016/05/23 20:50:12 :: ifconfig eth0
2016/05/23 20:50:17 :: ifconfig eth0
2016/05/23 20:50:22 :: ifconfig eth0
2016/05/23 20:50:27 :: ifconfig eth0
2016/05/23 20:50:32 :: ifconfig eth0
2016/05/23 20:50:37 :: ifconfig eth0
2016/05/23 20:50:42 :: ifconfig eth0
2016/05/23 20:50:47 :: ifconfig eth0
2016/05/23 20:50:52 :: ifconfig eth0
2016/05/23 20:50:57 :: ifconfig eth0
2016/05/23 20:51:02 :: ifconfig eth0
2016/05/23 20:51:07 :: ifconfig eth0
2016/05/23 20:51:12 :: ifconfig eth0
2016/05/23 20:51:17 :: ifconfig eth0
2016/05/23 20:51:22 :: ifconfig eth0
2016/05/23 20:51:27 :: ifconfig eth0
2016/05/23 20:51:32 :: ifconfig eth0
2016/05/23 20:51:37 :: ifconfig eth0
2016/05/23 20:51:42 :: ifconfig eth0
2016/05/23 20:51:47 :: ifconfig eth0
2016/05/23 20:51:52 :: ifconfig eth0
2016/05/23 20:51:57 :: ifconfig eth0
2016/05/23 20:52:02 :: ifconfig eth0
2016/05/23 20:52:07 :: ifconfig eth0
2016/05/23 20:52:12 :: ifconfig eth0
2016/05/23 20:52:17 :: ifconfig eth0
2016/05/23 20:52:22 :: ifconfig eth0
2016/05/23 20:52:27 :: ifconfig eth0
2016/05/23 20:52:32 :: ifconfig eth0
2016/05/23 20:52:37 :: ifconfig eth0
2016/05/23 20:52:42 :: ifconfig eth0
2016/05/23 20:52:47 :: ifconfig eth0
2016/05/23 20:52:52 :: ifconfig eth0
2016/05/23 20:52:57 :: ifconfig eth0
2016/05/23 20:53:02 :: ifconfig eth0
2016/05/23 20:53:07 :: ifconfig eth0
2016/05/23 20:53:12 :: ifconfig eth0
2016/05/23 20:53:17 :: ifconfig eth0
2016/05/23 20:53:22 :: ifconfig eth0
2016/05/23 20:53:27 :: ifconfig eth0
2016/05/23 20:53:32 :: ifconfig eth0
2016/05/23 20:53:37 :: ifconfig eth0
2016/05/23 20:53:42 :: ifconfig eth0
2016/05/23 20:53:47 :: ifconfig eth0
2016/05/23 20:53:52 :: ifconfig eth0
2016/05/23 20:53:57 :: ifconfig eth0
2016/05/23 20:54:02 :: ifconfig eth0
2016/05/23 20:54:07 :: ifconfig eth0
2016/05/23 20:54:12 :: ifconfig eth0
2016/05/23 20:54:17 :: ifconfig eth0
2016/05/23 20:54:22 :: ifconfig eth0
2016/05/23 20:54:27 :: ifconfig eth0
2016/05/23 20:54:32 :: ifconfig eth0
2016/05/23 20:54:37 :: ifconfig eth0
2016/05/23 20:54:42 :: ifconfig eth0
2016/05/23 20:54:47 :: ifconfig eth0
2016/05/23 20:54:52 :: ifconfig eth0
2016/05/23 20:54:57 :: ifconfig eth0
2016/05/23 20:55:02 :: ifconfig eth0
2016/05/23 20:55:07 :: ifconfig eth0
2016/05/23 20:55:12 :: ifconfig eth0
2016/05/23 20:55:17 :: ifconfig eth0
2016/05/23 20:55:22 :: ifconfig eth0
2016/05/23 20:55:27 :: ifconfig eth0
2016/05/23 20:55:32 :: ifconfig eth0
2016/05/23 20:55:37 :: ifconfig eth0
2016/05/23 20:55:42 :: ifconfig eth0
2016/05/23 20:55:47 :: ifconfig eth0
2016/05/23 20:55:52 :: ifconfig eth0
2016/05/23 20:55:57 :: ifconfig eth0
2016/05/23 20:56:02 :: ifconfig eth0
2016/05/23 20:56:07 :: ifconfig eth0
2016/05/23 20:56:12 :: ifconfig eth0
2016/05/23 20:56:17 :: ifconfig eth0
2016/05/23 20:56:22 :: ifconfig eth0
2016/05/23 20:56:27 :: ifconfig eth0
2016/05/23 20:56:32 :: ifconfig eth0
2016/05/23 20:56:32 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 20:56:32 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 20:56:32 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 20:56:32 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 20:56:32 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 20:56:32 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 20:56:32 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 20:56:32 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 20:56:32 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 20:56:32 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 20:56:32 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 20:56:32 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 20:56:32 :: attempting to set hostname with dhclient
2016/05/23 20:56:32 :: using dhcpcd or another supported client may work better
2016/05/23 20:56:32 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x61d786cd)
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 20:56:32 :: ifconfig eth0 0.0.0.0 
2016/05/23 20:56:32 :: /sbin/ip route flush dev eth0
2016/05/23 20:56:32 :: ifconfig eth0 down
2016/05/23 20:56:32 :: ifconfig eth0 up
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 20:56:33 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 20:56:33 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 20:56:33 :: Autoconnecting...
2016/05/23 20:56:33 :: Starting wireless autoconnect...
2016/05/23 20:56:33 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 20:56:33 :: scanning start
2016/05/23 20:56:33 :: scanning done
2016/05/23 20:56:33 :: found 0 networks:
2016/05/23 20:56:33 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 20:56:33 :: Forced disconnect on
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 20:56:33 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 20:56:33 :: attempting to set hostname with dhclient
2016/05/23 20:56:33 :: using dhcpcd or another supported client may work better
2016/05/23 20:56:33 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x3b2b3834)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 20:56:33 :: ifconfig eth0 0.0.0.0 
2016/05/23 20:56:33 :: /sbin/ip route flush dev eth0
2016/05/23 20:56:33 :: ifconfig eth0 down
2016/05/23 20:56:33 :: ifconfig eth0 up
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 20:56:33 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 20:56:33 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 20:56:33 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 20:56:33 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 20:56:33 :: Autoconnecting...
2016/05/23 20:56:33 :: Starting wireless autoconnect...
2016/05/23 20:56:33 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 20:56:33 :: scanning start
2016/05/23 20:56:33 :: scanning done
2016/05/23 20:56:33 :: found 0 networks:
2016/05/23 20:56:33 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 20:56:39 :: ifconfig eth0
2016/05/23 20:56:39 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 20:56:39 :: Autoconnecting...
2016/05/23 20:56:39 :: Starting wireless autoconnect...
2016/05/23 20:56:39 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 20:56:39 :: scanning start
2016/05/23 20:56:39 :: scanning done
2016/05/23 20:56:39 :: found 0 networks:
2016/05/23 20:56:39 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 20:56:44 :: ifconfig eth0
2016/05/23 20:56:44 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 20:56:44 :: Autoconnecting...
2016/05/23 20:56:44 :: Starting wireless autoconnect...
2016/05/23 20:56:44 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 20:56:44 :: scanning start
2016/05/23 20:56:44 :: scanning done
2016/05/23 20:56:44 :: found 0 networks:
2016/05/23 20:56:44 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 20:56:49 :: ifconfig eth0
2016/05/23 20:56:54 :: ifconfig eth0
2016/05/23 20:56:59 :: ifconfig eth0
2016/05/23 20:57:04 :: ifconfig eth0
2016/05/23 20:57:09 :: ifconfig eth0
2016/05/23 20:57:14 :: ifconfig eth0
2016/05/23 20:57:19 :: ifconfig eth0
2016/05/23 20:57:24 :: ifconfig eth0
2016/05/23 20:57:29 :: ifconfig eth0
2016/05/23 20:57:34 :: ifconfig eth0
2016/05/23 20:57:39 :: ifconfig eth0
2016/05/23 20:57:44 :: ifconfig eth0
2016/05/23 20:57:49 :: ifconfig eth0
2016/05/23 20:57:54 :: ifconfig eth0
2016/05/23 20:57:59 :: ifconfig eth0
2016/05/23 20:58:04 :: ifconfig eth0
2016/05/23 20:58:09 :: ifconfig eth0
2016/05/23 20:58:14 :: ifconfig eth0
2016/05/23 20:58:19 :: ifconfig eth0
2016/05/23 20:58:24 :: ifconfig eth0
2016/05/23 20:58:29 :: ifconfig eth0
2016/05/23 20:58:34 :: ifconfig eth0
2016/05/23 20:58:39 :: ifconfig eth0
2016/05/23 20:58:44 :: ifconfig eth0
2016/05/23 20:58:49 :: ifconfig eth0
2016/05/23 20:58:54 :: ifconfig eth0
2016/05/23 20:58:59 :: ifconfig eth0
2016/05/23 20:59:04 :: ifconfig eth0
2016/05/23 20:59:09 :: ifconfig eth0
2016/05/23 20:59:14 :: ifconfig eth0
2016/05/23 20:59:19 :: ifconfig eth0
2016/05/23 20:59:24 :: ifconfig eth0
2016/05/23 20:59:29 :: ifconfig eth0
2016/05/23 20:59:34 :: ifconfig eth0
2016/05/23 20:59:39 :: ifconfig eth0
2016/05/23 20:59:44 :: ifconfig eth0
2016/05/23 20:59:49 :: ifconfig eth0
2016/05/23 20:59:54 :: ifconfig eth0
2016/05/23 20:59:59 :: ifconfig eth0
2016/05/23 21:00:04 :: ifconfig eth0
2016/05/23 21:00:09 :: ifconfig eth0
2016/05/23 21:00:14 :: ifconfig eth0
2016/05/23 21:00:19 :: ifconfig eth0
2016/05/23 21:00:24 :: ifconfig eth0
2016/05/23 21:00:29 :: ifconfig eth0
2016/05/23 21:00:34 :: ifconfig eth0
2016/05/23 21:00:39 :: ifconfig eth0
2016/05/23 21:00:44 :: ifconfig eth0
2016/05/23 21:00:49 :: ifconfig eth0
2016/05/23 21:00:54 :: ifconfig eth0
2016/05/23 21:00:59 :: ifconfig eth0
2016/05/23 21:01:04 :: ifconfig eth0
2016/05/23 21:01:09 :: ifconfig eth0
2016/05/23 21:01:14 :: ifconfig eth0
2016/05/23 21:01:19 :: ifconfig eth0
2016/05/23 21:01:24 :: ifconfig eth0
2016/05/23 21:01:29 :: ifconfig eth0
2016/05/23 21:01:34 :: ifconfig eth0
2016/05/23 21:01:39 :: ifconfig eth0
2016/05/23 21:01:44 :: ifconfig eth0
2016/05/23 21:01:49 :: ifconfig eth0
2016/05/23 21:01:54 :: ifconfig eth0
2016/05/23 21:01:59 :: ifconfig eth0
2016/05/23 21:02:04 :: ifconfig eth0
2016/05/23 21:02:09 :: ifconfig eth0
2016/05/23 21:02:14 :: ifconfig eth0
2016/05/23 21:02:19 :: ifconfig eth0
2016/05/23 21:02:24 :: ifconfig eth0
2016/05/23 21:02:29 :: ifconfig eth0
2016/05/23 21:02:34 :: ifconfig eth0
2016/05/23 21:02:39 :: ifconfig eth0
2016/05/23 21:02:44 :: ifconfig eth0
2016/05/23 21:02:44 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:02:44 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:02:44 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:02:44 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:02:44 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:02:44 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:02:44 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:02:44 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:02:44 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:02:44 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:02:44 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:02:44 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:02:44 :: attempting to set hostname with dhclient
2016/05/23 21:02:44 :: using dhcpcd or another supported client may work better
2016/05/23 21:02:44 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x3a79e806)
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:02:44 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:02:44 :: /sbin/ip route flush dev eth0
2016/05/23 21:02:44 :: ifconfig eth0 down
2016/05/23 21:02:45 :: ifconfig eth0 up
2016/05/23 21:02:45 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:02:45 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:02:45 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:02:45 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:02:45 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:02:45 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:02:45 :: Autoconnecting...
2016/05/23 21:02:45 :: Starting wireless autoconnect...
2016/05/23 21:02:45 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:02:45 :: scanning start
2016/05/23 21:02:45 :: scanning done
2016/05/23 21:02:45 :: found 0 networks:
2016/05/23 21:02:45 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:02:45 :: Forced disconnect on
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:02:45 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:02:45 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:02:45 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:02:45 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:02:45 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:02:45 :: attempting to set hostname with dhclient
2016/05/23 21:02:45 :: using dhcpcd or another supported client may work better
2016/05/23 21:02:45 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x40fd242)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:02:45 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:02:45 :: /sbin/ip route flush dev eth0
2016/05/23 21:02:46 :: ifconfig eth0 down
2016/05/23 21:02:46 :: ifconfig eth0 up
2016/05/23 21:02:46 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:02:46 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:02:46 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:02:46 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:02:46 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:02:46 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:02:46 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:02:46 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:02:46 :: Autoconnecting...
2016/05/23 21:02:46 :: Starting wireless autoconnect...
2016/05/23 21:02:46 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:02:46 :: scanning start
2016/05/23 21:02:46 :: scanning done
2016/05/23 21:02:46 :: found 0 networks:
2016/05/23 21:02:46 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:02:51 :: ifconfig eth0
2016/05/23 21:02:51 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:02:51 :: Autoconnecting...
2016/05/23 21:02:51 :: Starting wireless autoconnect...
2016/05/23 21:02:51 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:02:51 :: scanning start
2016/05/23 21:02:51 :: scanning done
2016/05/23 21:02:51 :: found 0 networks:
2016/05/23 21:02:51 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:02:56 :: ifconfig eth0
2016/05/23 21:02:56 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:02:56 :: Autoconnecting...
2016/05/23 21:02:56 :: Starting wireless autoconnect...
2016/05/23 21:02:56 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:02:56 :: scanning start
2016/05/23 21:02:56 :: scanning done
2016/05/23 21:02:56 :: found 0 networks:
2016/05/23 21:02:56 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:03:01 :: ifconfig eth0
2016/05/23 21:03:06 :: ifconfig eth0
2016/05/23 21:03:11 :: ifconfig eth0
2016/05/23 21:03:16 :: ifconfig eth0
2016/05/23 21:03:21 :: ifconfig eth0
2016/05/23 21:03:26 :: ifconfig eth0
2016/05/23 21:03:31 :: ifconfig eth0
2016/05/23 21:03:36 :: ifconfig eth0
2016/05/23 21:03:41 :: ifconfig eth0
2016/05/23 21:03:46 :: ifconfig eth0
2016/05/23 21:03:51 :: ifconfig eth0
2016/05/23 21:03:56 :: ifconfig eth0
2016/05/23 21:04:01 :: ifconfig eth0
2016/05/23 21:04:06 :: ifconfig eth0
2016/05/23 21:04:11 :: ifconfig eth0
2016/05/23 21:04:16 :: ifconfig eth0
2016/05/23 21:04:21 :: ifconfig eth0
2016/05/23 21:04:26 :: ifconfig eth0
2016/05/23 21:04:31 :: ifconfig eth0
2016/05/23 21:04:36 :: ifconfig eth0
2016/05/23 21:04:41 :: ifconfig eth0
2016/05/23 21:04:46 :: ifconfig eth0
2016/05/23 21:04:46 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:04:46 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:04:46 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:04:46 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:04:46 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:04:46 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:04:46 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:04:46 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:04:46 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:04:46 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:04:46 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:04:46 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:04:46 :: attempting to set hostname with dhclient
2016/05/23 21:04:46 :: using dhcpcd or another supported client may work better
2016/05/23 21:04:46 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x4e3c5f60)
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:04:46 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:04:46 :: /sbin/ip route flush dev eth0
2016/05/23 21:04:46 :: ifconfig eth0 down
2016/05/23 21:04:46 :: ifconfig eth0 up
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:04:47 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:04:47 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:04:47 :: Autoconnecting...
2016/05/23 21:04:47 :: Starting wireless autoconnect...
2016/05/23 21:04:47 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:04:47 :: scanning start
2016/05/23 21:04:47 :: scanning done
2016/05/23 21:04:47 :: found 0 networks:
2016/05/23 21:04:47 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:04:47 :: Forced disconnect on
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:04:47 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:04:47 :: attempting to set hostname with dhclient
2016/05/23 21:04:47 :: using dhcpcd or another supported client may work better
2016/05/23 21:04:47 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x66edcad7)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:04:47 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:04:47 :: /sbin/ip route flush dev eth0
2016/05/23 21:04:47 :: ifconfig eth0 down
2016/05/23 21:04:47 :: ifconfig eth0 up
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:04:47 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:04:47 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:04:47 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:04:47 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:04:47 :: Autoconnecting...
2016/05/23 21:04:47 :: Starting wireless autoconnect...
2016/05/23 21:04:47 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:04:47 :: scanning start
2016/05/23 21:04:47 :: scanning done
2016/05/23 21:04:47 :: found 0 networks:
2016/05/23 21:04:47 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:04:53 :: ifconfig eth0
2016/05/23 21:04:53 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:04:53 :: Autoconnecting...
2016/05/23 21:04:53 :: Starting wireless autoconnect...
2016/05/23 21:04:53 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:04:53 :: scanning start
2016/05/23 21:04:53 :: scanning done
2016/05/23 21:04:53 :: found 0 networks:
2016/05/23 21:04:53 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:04:58 :: ifconfig eth0
2016/05/23 21:04:58 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:04:58 :: Autoconnecting...
2016/05/23 21:04:58 :: Starting wireless autoconnect...
2016/05/23 21:04:58 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:04:58 :: scanning start
2016/05/23 21:04:58 :: scanning done
2016/05/23 21:04:58 :: found 0 networks:
2016/05/23 21:04:58 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:05:03 :: ifconfig eth0
2016/05/23 21:05:08 :: ifconfig eth0
2016/05/23 21:05:13 :: ifconfig eth0
2016/05/23 21:05:18 :: ifconfig eth0
2016/05/23 21:05:23 :: ifconfig eth0
2016/05/23 21:05:28 :: ifconfig eth0
2016/05/23 21:05:33 :: ifconfig eth0
2016/05/23 21:05:38 :: ifconfig eth0
2016/05/23 21:05:43 :: ifconfig eth0
2016/05/23 21:05:48 :: ifconfig eth0
2016/05/23 21:05:53 :: ifconfig eth0
2016/05/23 21:05:58 :: ifconfig eth0
2016/05/23 21:06:03 :: ifconfig eth0
2016/05/23 21:06:08 :: ifconfig eth0
2016/05/23 21:06:13 :: ifconfig eth0
2016/05/23 21:06:18 :: ifconfig eth0
2016/05/23 21:06:23 :: ifconfig eth0
2016/05/23 21:06:28 :: ifconfig eth0
2016/05/23 21:06:33 :: ifconfig eth0
2016/05/23 21:06:38 :: ifconfig eth0
2016/05/23 21:06:43 :: ifconfig eth0
2016/05/23 21:06:48 :: ifconfig eth0
2016/05/23 21:06:53 :: ifconfig eth0
2016/05/23 21:06:58 :: ifconfig eth0
2016/05/23 21:07:03 :: ifconfig eth0
2016/05/23 21:07:08 :: ifconfig eth0
2016/05/23 21:07:13 :: ifconfig eth0
2016/05/23 21:07:18 :: ifconfig eth0
2016/05/23 21:07:23 :: ifconfig eth0
2016/05/23 21:07:28 :: ifconfig eth0
2016/05/23 21:07:33 :: ifconfig eth0
2016/05/23 21:07:38 :: ifconfig eth0
2016/05/23 21:07:43 :: ifconfig eth0
2016/05/23 21:07:48 :: ifconfig eth0
2016/05/23 21:07:53 :: ifconfig eth0
2016/05/23 21:07:58 :: ifconfig eth0
2016/05/23 21:08:03 :: ifconfig eth0
2016/05/23 21:08:08 :: ifconfig eth0
2016/05/23 21:08:13 :: ifconfig eth0
2016/05/23 21:08:18 :: ifconfig eth0
2016/05/23 21:08:23 :: ifconfig eth0
2016/05/23 21:08:28 :: ifconfig eth0
2016/05/23 21:08:33 :: ifconfig eth0
2016/05/23 21:08:38 :: ifconfig eth0
2016/05/23 21:08:43 :: ifconfig eth0
2016/05/23 21:08:48 :: ifconfig eth0
2016/05/23 21:08:53 :: ifconfig eth0
2016/05/23 21:08:58 :: ifconfig eth0
2016/05/23 21:09:03 :: ifconfig eth0
2016/05/23 21:09:08 :: ifconfig eth0
2016/05/23 21:09:13 :: ifconfig eth0
2016/05/23 21:09:18 :: ifconfig eth0
2016/05/23 21:09:23 :: ifconfig eth0
2016/05/23 21:09:28 :: ifconfig eth0
2016/05/23 21:09:33 :: ifconfig eth0
2016/05/23 21:09:38 :: ifconfig eth0
2016/05/23 21:09:43 :: ifconfig eth0
2016/05/23 21:09:48 :: ifconfig eth0
2016/05/23 21:09:53 :: ifconfig eth0
2016/05/23 21:09:58 :: ifconfig eth0
2016/05/23 21:10:03 :: ifconfig eth0
2016/05/23 21:10:08 :: ifconfig eth0
2016/05/23 21:10:13 :: ifconfig eth0
2016/05/23 21:10:18 :: ifconfig eth0
2016/05/23 21:10:23 :: ifconfig eth0
2016/05/23 21:10:28 :: ifconfig eth0
2016/05/23 21:10:33 :: ifconfig eth0
2016/05/23 21:10:38 :: ifconfig eth0
2016/05/23 21:10:43 :: ifconfig eth0
2016/05/23 21:10:48 :: ifconfig eth0
2016/05/23 21:10:53 :: ifconfig eth0
2016/05/23 21:10:58 :: ifconfig eth0
2016/05/23 21:11:03 :: ifconfig eth0
2016/05/23 21:11:08 :: ifconfig eth0
2016/05/23 21:11:13 :: ifconfig eth0
2016/05/23 21:11:18 :: ifconfig eth0
2016/05/23 21:11:23 :: ifconfig eth0
2016/05/23 21:11:28 :: ifconfig eth0
2016/05/23 21:11:33 :: ifconfig eth0
2016/05/23 21:11:38 :: ifconfig eth0
2016/05/23 21:11:43 :: ifconfig eth0
2016/05/23 21:11:48 :: ifconfig eth0
2016/05/23 21:11:53 :: ifconfig eth0
2016/05/23 21:11:58 :: ifconfig eth0
2016/05/23 21:12:03 :: ifconfig eth0
2016/05/23 21:12:08 :: ifconfig eth0
2016/05/23 21:12:13 :: ifconfig eth0
2016/05/23 21:12:18 :: ifconfig eth0
2016/05/23 21:12:23 :: ifconfig eth0
2016/05/23 21:12:28 :: ifconfig eth0
2016/05/23 21:12:33 :: ifconfig eth0
2016/05/23 21:12:38 :: ifconfig eth0
2016/05/23 21:12:43 :: ifconfig eth0
2016/05/23 21:12:48 :: ifconfig eth0
2016/05/23 21:12:53 :: ifconfig eth0
2016/05/23 21:12:58 :: ifconfig eth0
2016/05/23 21:13:03 :: ifconfig eth0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:03 :: attempting to set hostname with dhclient
2016/05/23 21:13:03 :: using dhcpcd or another supported client may work better
2016/05/23 21:13:03 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x2e1a8599)
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:13:03 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:13:03 :: /sbin/ip route flush dev eth0
2016/05/23 21:13:03 :: ifconfig eth0 down
2016/05/23 21:13:03 :: ifconfig eth0 up
2016/05/23 21:13:03 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:03 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:03 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:03 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:03 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:13:03 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:13:03 :: Autoconnecting...
2016/05/23 21:13:03 :: Starting wireless autoconnect...
2016/05/23 21:13:03 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:13:03 :: scanning start
2016/05/23 21:13:03 :: scanning done
2016/05/23 21:13:03 :: found 0 networks:
2016/05/23 21:13:03 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:13:03 :: Forced disconnect on
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:03 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:03 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:04 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:04 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:04 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:04 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:04 :: attempting to set hostname with dhclient
2016/05/23 21:13:04 :: using dhcpcd or another supported client may work better
2016/05/23 21:13:04 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x4767b71a)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:13:04 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:13:04 :: /sbin/ip route flush dev eth0
2016/05/23 21:13:04 :: ifconfig eth0 down
2016/05/23 21:13:04 :: ifconfig eth0 up
2016/05/23 21:13:04 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:04 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:04 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:04 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:04 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:04 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:13:04 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:13:04 :: Autoconnecting...
2016/05/23 21:13:04 :: Starting wireless autoconnect...
2016/05/23 21:13:04 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:13:04 :: scanning start
2016/05/23 21:13:04 :: scanning done
2016/05/23 21:13:04 :: found 0 networks:
2016/05/23 21:13:04 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:13:10 :: ifconfig eth0
2016/05/23 21:13:15 :: ifconfig eth0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:15 :: attempting to set hostname with dhclient
2016/05/23 21:13:15 :: using dhcpcd or another supported client may work better
2016/05/23 21:13:15 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x3f2f1f89)
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:13:15 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:13:15 :: /sbin/ip route flush dev eth0
2016/05/23 21:13:15 :: ifconfig eth0 down
2016/05/23 21:13:15 :: ifconfig eth0 up
2016/05/23 21:13:15 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:15 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:15 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:15 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:15 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:13:15 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:13:15 :: Autoconnecting...
2016/05/23 21:13:15 :: Starting wireless autoconnect...
2016/05/23 21:13:15 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:13:15 :: scanning start
2016/05/23 21:13:15 :: scanning done
2016/05/23 21:13:15 :: found 0 networks:
2016/05/23 21:13:15 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:13:15 :: Forced disconnect on
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:15 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:15 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:16 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:16 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:16 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:16 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:16 :: attempting to set hostname with dhclient
2016/05/23 21:13:16 :: using dhcpcd or another supported client may work better
2016/05/23 21:13:16 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x1812fa2b)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:13:16 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:13:16 :: /sbin/ip route flush dev eth0
2016/05/23 21:13:16 :: ifconfig eth0 down
2016/05/23 21:13:16 :: ifconfig eth0 up
2016/05/23 21:13:16 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:16 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:16 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:16 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:16 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:16 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:13:16 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:13:16 :: Autoconnecting...
2016/05/23 21:13:16 :: Starting wireless autoconnect...
2016/05/23 21:13:16 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:13:16 :: scanning start
2016/05/23 21:13:16 :: scanning done
2016/05/23 21:13:16 :: found 0 networks:
2016/05/23 21:13:16 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:13:22 :: ifconfig eth0
2016/05/23 21:13:22 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:13:22 :: Autoconnecting...
2016/05/23 21:13:22 :: Starting wired autoconnect...
2016/05/23 21:13:22 :: found default in configuration 1
2016/05/23 21:13:22 :: Reading wired profile wired-default
2016/05/23 21:13:22 :: found afterscript in configuration None
2016/05/23 21:13:22 :: found dhcphostname in configuration noahlub
2016/05/23 21:13:22 :: found postdisconnectscript in configuration None
2016/05/23 21:13:22 :: found dns_domain in configuration None
2016/05/23 21:13:22 :: found gateway in configuration None
2016/05/23 21:13:22 :: found use_global_dns in configuration False
2016/05/23 21:13:22 :: found lastused in configuration True
2016/05/23 21:13:22 :: found ip in configuration None
2016/05/23 21:13:22 :: found beforescript in configuration None
2016/05/23 21:13:22 :: found encryption_enabled in configuration False
2016/05/23 21:13:22 :: found broadcast in configuration None
2016/05/23 21:13:22 :: found netmask in configuration None
2016/05/23 21:13:22 :: found usedhcphostname in configuration 1
2016/05/23 21:13:22 :: found predisconnectscript in configuration None
2016/05/23 21:13:22 :: found enctype in configuration None
2016/05/23 21:13:22 :: found default in configuration 1
2016/05/23 21:13:22 :: found dns2 in configuration 8.8.4.4
2016/05/23 21:13:22 :: found search_domain in configuration None
2016/05/23 21:13:22 :: found use_static_dns in configuration True
2016/05/23 21:13:22 :: found dns3 in configuration None
2016/05/23 21:13:22 :: found profilename in configuration wired-default
2016/05/23 21:13:22 :: found dns1 in configuration 8.8.8.8
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:22 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:22 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:22 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:13:22 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:13:22 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:13:22 :: attempting to set hostname with dhclient
2016/05/23 21:13:22 :: using dhcpcd or another supported client may work better
2016/05/23 21:13:22 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x508f5eb8)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:13:22 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:13:22 :: /sbin/ip route flush dev eth0
2016/05/23 21:13:22 :: ifconfig eth0 down
2016/05/23 21:13:22 :: ifconfig eth0 up
2016/05/23 21:13:23 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:13:23 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:13:23 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:13:23 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:13:23 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:13:23 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:13:23 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:13:23 :: found lastused in configuration True
2016/05/23 21:13:23 :: Attempting to autoconnect with wired interface...
2016/05/23 21:13:23 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 21:13:23 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 21:13:23 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 21:13:23 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 21:13:23 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 21:13:23 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 21:13:23 :: Putting interface down
2016/05/23 21:13:23 :: ifconfig eth0 down
2016/05/23 21:13:23 :: Releasing DHCP leases...
2016/05/23 21:13:23 :: attempting to set hostname with dhclient
2016/05/23 21:13:23 :: using dhcpcd or another supported client may work better
2016/05/23 21:13:23 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x2615ef16)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:13:23 :: Setting false IP...
2016/05/23 21:13:23 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:13:23 :: Stopping wpa_supplicant
2016/05/23 21:13:23 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:13:23 :: Flushing the routing table...
2016/05/23 21:13:23 :: /sbin/ip route flush dev eth0
2016/05/23 21:13:23 :: Putting interface up...
2016/05/23 21:13:23 :: ifconfig eth0 up
2016/05/23 21:13:25 :: Running DHCP with hostname noahlub
2016/05/23 21:13:25 :: attempting to set hostname with dhclient
2016/05/23 21:13:25 :: using dhcpcd or another supported client may work better
2016/05/23 21:13:25 :: /sbin/dhclient -v eth0
2016/05/23 21:13:25 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 21:13:25 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 21:13:25 :: All rights reserved.
2016/05/23 21:13:25 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 21:13:25 :: 
2016/05/23 21:13:25 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:13:25 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:13:25 :: Sending on   Socket/fallback
2016/05/23 21:13:25 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xd025b66d)
2016/05/23 21:13:28 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0xd025b66d)
2016/05/23 21:13:28 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x6db625d0)
2016/05/23 21:13:28 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 21:13:28 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 21:13:28 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:13:28 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 21:13:28 :: bound to 162.228.104.207 -- renewal in 265 seconds.
2016/05/23 21:13:28 :: DHCP connection successful
2016/05/23 21:13:28 :: Setting DNS : 8.8.8.8
2016/05/23 21:13:28 :: Setting DNS : 8.8.4.4
2016/05/23 21:13:28 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 21:13:28 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 21:13:28 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 21:13:28 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 21:13:28 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 21:13:28 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 21:13:32 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 21:13:32 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 21:13:32 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 21:13:32 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 21:13:32 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 21:13:32 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 21:13:32 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 21:13:32 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 21:13:32 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 21:13:32 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:13:32 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:13:32 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 21:13:32 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 21:13:32 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 21:13:33 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 21:13:33 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 21:13:33 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 21:13:33 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 21:13:33 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 21:13:33 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 21:13:33 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 21:13:33 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 21:13:33 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 21:13:33 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 21:13:33 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 21:13:33 :: Connecting thread exiting.
2016/05/23 21:13:33 :: ifconfig eth0
2016/05/23 21:13:33 :: IP Address is: 162.228.104.207
2016/05/23 21:13:34 :: Sending connection attempt result success
2016/05/23 21:13:39 :: ifconfig eth0
2016/05/23 21:13:44 :: ifconfig eth0
2016/05/23 21:13:49 :: ifconfig eth0
2016/05/23 21:13:54 :: ifconfig eth0
2016/05/23 21:13:59 :: ifconfig eth0
2016/05/23 21:14:04 :: ifconfig eth0
2016/05/23 21:14:09 :: ifconfig eth0
2016/05/23 21:14:14 :: ifconfig eth0
2016/05/23 21:14:19 :: ifconfig eth0
2016/05/23 21:14:24 :: ifconfig eth0
2016/05/23 21:14:29 :: ifconfig eth0
2016/05/23 21:14:34 :: ifconfig eth0
2016/05/23 21:14:39 :: ifconfig eth0
2016/05/23 21:14:44 :: ifconfig eth0
2016/05/23 21:14:49 :: ifconfig eth0
2016/05/23 21:14:54 :: ifconfig eth0
2016/05/23 21:14:59 :: ifconfig eth0
2016/05/23 21:15:04 :: ifconfig eth0
2016/05/23 21:15:09 :: ifconfig eth0
2016/05/23 21:15:14 :: ifconfig eth0
2016/05/23 21:15:19 :: ifconfig eth0
2016/05/23 21:15:24 :: ifconfig eth0
2016/05/23 21:15:29 :: ifconfig eth0
2016/05/23 21:15:34 :: ifconfig eth0
2016/05/23 21:15:39 :: ifconfig eth0
2016/05/23 21:15:44 :: ifconfig eth0
2016/05/23 21:15:49 :: ifconfig eth0
2016/05/23 21:15:54 :: ifconfig eth0
2016/05/23 21:15:59 :: ifconfig eth0
2016/05/23 21:16:04 :: ifconfig eth0
2016/05/23 21:16:09 :: ifconfig eth0
2016/05/23 21:16:14 :: ifconfig eth0
2016/05/23 21:16:19 :: ifconfig eth0
2016/05/23 21:16:24 :: ifconfig eth0
2016/05/23 21:16:29 :: ifconfig eth0
2016/05/23 21:16:34 :: ifconfig eth0
2016/05/23 21:16:39 :: ifconfig eth0
2016/05/23 21:16:44 :: ifconfig eth0
2016/05/23 21:16:49 :: ifconfig eth0
2016/05/23 21:16:54 :: ifconfig eth0
2016/05/23 21:16:59 :: ifconfig eth0
2016/05/23 21:17:04 :: ifconfig eth0
2016/05/23 21:17:09 :: ifconfig eth0
2016/05/23 21:17:14 :: ifconfig eth0
2016/05/23 21:17:19 :: ifconfig eth0
2016/05/23 21:17:24 :: ifconfig eth0
2016/05/23 21:17:29 :: ifconfig eth0
2016/05/23 21:17:34 :: ifconfig eth0
2016/05/23 21:17:39 :: ifconfig eth0
2016/05/23 21:17:44 :: ifconfig eth0
2016/05/23 21:17:49 :: ifconfig eth0
2016/05/23 21:17:54 :: ifconfig eth0
2016/05/23 21:17:59 :: ifconfig eth0
2016/05/23 21:18:04 :: ifconfig eth0
2016/05/23 21:18:09 :: ifconfig eth0
2016/05/23 21:18:14 :: ifconfig eth0
2016/05/23 21:18:19 :: ifconfig eth0
2016/05/23 21:18:24 :: ifconfig eth0
2016/05/23 21:18:29 :: ifconfig eth0
2016/05/23 21:18:34 :: ifconfig eth0
2016/05/23 21:18:39 :: ifconfig eth0
2016/05/23 21:18:44 :: ifconfig eth0
2016/05/23 21:18:49 :: ifconfig eth0
2016/05/23 21:18:54 :: ifconfig eth0
2016/05/23 21:18:59 :: ifconfig eth0
2016/05/23 21:19:04 :: ifconfig eth0
2016/05/23 21:19:09 :: ifconfig eth0
2016/05/23 21:19:14 :: ifconfig eth0
2016/05/23 21:19:19 :: ifconfig eth0
2016/05/23 21:19:24 :: ifconfig eth0
2016/05/23 21:19:29 :: ifconfig eth0
2016/05/23 21:19:34 :: ifconfig eth0
2016/05/23 21:19:39 :: ifconfig eth0
2016/05/23 21:19:44 :: ifconfig eth0
2016/05/23 21:19:49 :: ifconfig eth0
2016/05/23 21:19:54 :: ifconfig eth0
2016/05/23 21:19:59 :: ifconfig eth0
2016/05/23 21:19:59 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:19:59 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:19:59 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:19:59 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:19:59 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:19:59 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:19:59 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:19:59 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:19:59 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:19:59 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:19:59 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:19:59 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:19:59 :: attempting to set hostname with dhclient
2016/05/23 21:19:59 :: using dhcpcd or another supported client may work better
2016/05/23 21:19:59 :: /sbin/dhclient -v -r eth0
Killed old client process
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x4e5af2ca)
/etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:20:00 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:20:00 :: /sbin/ip route flush dev eth0
2016/05/23 21:20:00 :: ifconfig eth0 down
2016/05/23 21:20:01 :: ifconfig eth0 up
2016/05/23 21:20:01 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:20:01 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:20:01 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:20:01 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:20:01 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:20:01 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:20:01 :: Autoconnecting...
2016/05/23 21:20:01 :: Starting wireless autoconnect...
2016/05/23 21:20:01 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:20:01 :: scanning start
2016/05/23 21:20:01 :: scanning done
2016/05/23 21:20:01 :: found 0 networks:
2016/05/23 21:20:01 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:20:01 :: Forced disconnect on
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:20:01 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:20:01 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:20:01 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:20:01 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:20:01 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:20:01 :: attempting to set hostname with dhclient
2016/05/23 21:20:01 :: using dhcpcd or another supported client may work better
2016/05/23 21:20:01 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x59dd29ee)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:20:01 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:20:01 :: /sbin/ip route flush dev eth0
2016/05/23 21:20:01 :: ifconfig eth0 down
2016/05/23 21:20:02 :: ifconfig eth0 up
2016/05/23 21:20:02 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:20:02 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:20:02 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:20:02 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:20:02 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:20:02 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:20:02 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:20:02 :: ifconfig eth0
2016/05/23 21:20:02 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:20:02 :: Autoconnecting...
2016/05/23 21:20:02 :: Starting wireless autoconnect...
2016/05/23 21:20:02 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:20:02 :: scanning start
2016/05/23 21:20:02 :: scanning done
2016/05/23 21:20:02 :: found 0 networks:
2016/05/23 21:20:02 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:20:07 :: ifconfig eth0
2016/05/23 21:20:07 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:20:07 :: Autoconnecting...
2016/05/23 21:20:07 :: Starting wireless autoconnect...
2016/05/23 21:20:07 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:20:07 :: scanning start
2016/05/23 21:20:07 :: scanning done
2016/05/23 21:20:07 :: found 0 networks:
2016/05/23 21:20:07 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:20:12 :: ifconfig eth0
2016/05/23 21:20:12 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:20:12 :: Autoconnecting...
2016/05/23 21:20:12 :: Starting wireless autoconnect...
2016/05/23 21:20:12 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:20:12 :: scanning start
2016/05/23 21:20:12 :: scanning done
2016/05/23 21:20:12 :: found 0 networks:
2016/05/23 21:20:12 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:20:17 :: ifconfig eth0
2016/05/23 21:20:22 :: ifconfig eth0
2016/05/23 21:20:27 :: ifconfig eth0
2016/05/23 21:20:32 :: ifconfig eth0
2016/05/23 21:20:37 :: ifconfig eth0
2016/05/23 21:20:42 :: ifconfig eth0
2016/05/23 21:20:47 :: ifconfig eth0
2016/05/23 21:20:52 :: ifconfig eth0
2016/05/23 21:20:57 :: ifconfig eth0
2016/05/23 21:21:02 :: ifconfig eth0
2016/05/23 21:21:07 :: ifconfig eth0
2016/05/23 21:21:12 :: ifconfig eth0
2016/05/23 21:21:17 :: ifconfig eth0
2016/05/23 21:21:22 :: ifconfig eth0
2016/05/23 21:21:27 :: ifconfig eth0
2016/05/23 21:21:32 :: ifconfig eth0
2016/05/23 21:21:37 :: ifconfig eth0
2016/05/23 21:21:42 :: ifconfig eth0
2016/05/23 21:21:47 :: ifconfig eth0
2016/05/23 21:21:52 :: ifconfig eth0
2016/05/23 21:21:57 :: ifconfig eth0
2016/05/23 21:22:02 :: ifconfig eth0
2016/05/23 21:22:07 :: ifconfig eth0
2016/05/23 21:22:12 :: ifconfig eth0
2016/05/23 21:22:17 :: ifconfig eth0
2016/05/23 21:22:22 :: ifconfig eth0
2016/05/23 21:22:27 :: ifconfig eth0
2016/05/23 21:22:32 :: ifconfig eth0
2016/05/23 21:22:37 :: ifconfig eth0
2016/05/23 21:22:42 :: ifconfig eth0
2016/05/23 21:22:47 :: ifconfig eth0
2016/05/23 21:22:52 :: ifconfig eth0
2016/05/23 21:22:57 :: ifconfig eth0
2016/05/23 21:23:02 :: ifconfig eth0
2016/05/23 21:23:07 :: ifconfig eth0
2016/05/23 21:23:12 :: ifconfig eth0
2016/05/23 21:23:17 :: ifconfig eth0
2016/05/23 21:23:22 :: ifconfig eth0
2016/05/23 21:23:27 :: ifconfig eth0
2016/05/23 21:23:32 :: ifconfig eth0
2016/05/23 21:23:37 :: ifconfig eth0
2016/05/23 21:23:42 :: ifconfig eth0
2016/05/23 21:23:47 :: ifconfig eth0
2016/05/23 21:23:52 :: ifconfig eth0
2016/05/23 21:23:57 :: ifconfig eth0
2016/05/23 21:24:02 :: ifconfig eth0
2016/05/23 21:24:02 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:24:02 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:24:02 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:24:02 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:24:02 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:24:02 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:24:02 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:24:02 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:24:02 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:24:02 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:24:02 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:24:02 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:24:02 :: attempting to set hostname with dhclient
2016/05/23 21:24:02 :: using dhcpcd or another supported client may work better
2016/05/23 21:24:02 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x2902076b)
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:24:02 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:24:02 :: /sbin/ip route flush dev eth0
2016/05/23 21:24:02 :: ifconfig eth0 down
2016/05/23 21:24:02 :: ifconfig eth0 up
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:24:03 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:24:03 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:24:03 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:24:03 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:24:03 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:24:03 :: Autoconnecting...
2016/05/23 21:24:03 :: Starting wireless autoconnect...
2016/05/23 21:24:03 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:24:03 :: scanning start
2016/05/23 21:24:03 :: scanning done
2016/05/23 21:24:03 :: found 0 networks:
2016/05/23 21:24:03 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:24:03 :: Forced disconnect on
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:24:03 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:24:03 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:24:03 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:24:03 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:24:03 :: attempting to set hostname with dhclient
2016/05/23 21:24:03 :: using dhcpcd or another supported client may work better
2016/05/23 21:24:03 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x714c3c86)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:24:03 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:24:03 :: /sbin/ip route flush dev eth0
2016/05/23 21:24:03 :: ifconfig eth0 down
2016/05/23 21:24:03 :: ifconfig eth0 up
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:24:03 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:24:03 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:24:04 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:24:04 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:24:04 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:24:04 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:24:04 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:24:04 :: Autoconnecting...
2016/05/23 21:24:04 :: Starting wireless autoconnect...
2016/05/23 21:24:04 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:24:04 :: scanning start
2016/05/23 21:24:04 :: scanning done
2016/05/23 21:24:04 :: found 0 networks:
2016/05/23 21:24:04 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:24:09 :: ifconfig eth0
2016/05/23 21:24:09 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:24:09 :: Autoconnecting...
2016/05/23 21:24:09 :: Starting wireless autoconnect...
2016/05/23 21:24:09 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:24:09 :: scanning start
2016/05/23 21:24:09 :: scanning done
2016/05/23 21:24:09 :: found 0 networks:
2016/05/23 21:24:09 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:24:14 :: ifconfig eth0
2016/05/23 21:24:14 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:24:14 :: Autoconnecting...
2016/05/23 21:24:14 :: Starting wireless autoconnect...
2016/05/23 21:24:14 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:24:14 :: scanning start
2016/05/23 21:24:14 :: scanning done
2016/05/23 21:24:14 :: found 0 networks:
2016/05/23 21:24:14 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:24:19 :: ifconfig eth0
2016/05/23 21:24:24 :: ifconfig eth0
2016/05/23 21:24:25 :: found default in configuration 1
2016/05/23 21:24:25 :: Reading wired profile wired-default
2016/05/23 21:24:25 :: found afterscript in configuration None
2016/05/23 21:24:25 :: found dhcphostname in configuration noahlub
2016/05/23 21:24:25 :: found postdisconnectscript in configuration None
2016/05/23 21:24:25 :: found dns_domain in configuration None
2016/05/23 21:24:25 :: found gateway in configuration None
2016/05/23 21:24:25 :: found use_global_dns in configuration False
2016/05/23 21:24:25 :: found lastused in configuration True
2016/05/23 21:24:25 :: found ip in configuration None
2016/05/23 21:24:25 :: found beforescript in configuration None
2016/05/23 21:24:25 :: found encryption_enabled in configuration False
2016/05/23 21:24:25 :: found broadcast in configuration None
2016/05/23 21:24:25 :: found netmask in configuration None
2016/05/23 21:24:25 :: found usedhcphostname in configuration 1
2016/05/23 21:24:25 :: found predisconnectscript in configuration None
2016/05/23 21:24:25 :: found enctype in configuration None
2016/05/23 21:24:25 :: found default in configuration 1
2016/05/23 21:24:25 :: found dns2 in configuration 8.8.4.4
2016/05/23 21:24:25 :: found search_domain in configuration None
2016/05/23 21:24:25 :: found use_static_dns in configuration True
2016/05/23 21:24:25 :: found dns3 in configuration None
2016/05/23 21:24:25 :: found profilename in configuration wired-default
2016/05/23 21:24:25 :: found dns1 in configuration 8.8.8.8
2016/05/23 21:24:25 :: found default in configuration 1
2016/05/23 21:24:25 :: saving wired profile wired-default
2016/05/23 21:24:25 :: scanning start
2016/05/23 21:24:25 :: scanning done
2016/05/23 21:24:25 :: found 0 networks:
2016/05/23 21:24:27 :: ifconfig eth0
2016/05/23 21:24:31 :: ifconfig eth0
2016/05/23 21:24:35 :: ifconfig eth0
2016/05/23 21:24:39 :: ifconfig eth0
2016/05/23 21:24:43 :: ifconfig eth0
2016/05/23 21:24:47 :: ifconfig eth0
2016/05/23 21:24:51 :: ifconfig eth0
2016/05/23 21:24:55 :: ifconfig eth0
2016/05/23 21:24:59 :: ifconfig eth0
2016/05/23 21:25:03 :: ifconfig eth0
2016/05/23 21:25:07 :: ifconfig eth0
2016/05/23 21:25:11 :: ifconfig eth0
2016/05/23 21:25:15 :: ifconfig eth0
2016/05/23 21:25:19 :: ifconfig eth0
2016/05/23 21:25:23 :: ifconfig eth0
2016/05/23 21:25:27 :: ifconfig eth0
2016/05/23 21:25:29 :: ifconfig eth0
2016/05/23 21:25:33 :: ifconfig eth0
2016/05/23 21:25:37 :: ifconfig eth0
2016/05/23 21:25:41 :: ifconfig eth0
2016/05/23 21:25:45 :: ifconfig eth0
2016/05/23 21:25:49 :: ifconfig eth0
2016/05/23 21:25:53 :: ifconfig eth0
2016/05/23 21:25:57 :: ifconfig eth0
2016/05/23 21:25:59 :: ifconfig eth0
2016/05/23 21:26:03 :: ifconfig eth0
2016/05/23 21:26:07 :: ifconfig eth0
2016/05/23 21:26:11 :: ifconfig eth0
2016/05/23 21:26:15 :: ifconfig eth0
2016/05/23 21:26:19 :: ifconfig eth0
2016/05/23 21:26:23 :: ifconfig eth0
2016/05/23 21:26:27 :: ifconfig eth0
2016/05/23 21:26:31 :: ifconfig eth0
2016/05/23 21:26:35 :: ifconfig eth0
2016/05/23 21:26:39 :: ifconfig eth0
2016/05/23 21:26:41 :: ifconfig eth0
2016/05/23 21:26:45 :: ifconfig eth0
2016/05/23 21:26:49 :: ifconfig eth0
2016/05/23 21:26:53 :: ifconfig eth0
2016/05/23 21:26:57 :: ifconfig eth0
2016/05/23 21:27:01 :: ifconfig eth0
2016/05/23 21:27:05 :: ifconfig eth0
2016/05/23 21:27:09 :: ifconfig eth0
2016/05/23 21:27:13 :: ifconfig eth0
2016/05/23 21:27:17 :: ifconfig eth0
2016/05/23 21:27:21 :: ifconfig eth0
2016/05/23 21:27:25 :: ifconfig eth0
2016/05/23 21:27:29 :: ifconfig eth0
2016/05/23 21:27:33 :: ifconfig eth0
2016/05/23 21:27:35 :: ifconfig eth0
2016/05/23 21:27:39 :: ifconfig eth0
2016/05/23 21:27:43 :: ifconfig eth0
2016/05/23 21:27:47 :: ifconfig eth0
2016/05/23 21:27:51 :: ifconfig eth0
2016/05/23 21:27:55 :: ifconfig eth0
2016/05/23 21:27:59 :: ifconfig eth0
2016/05/23 21:28:03 :: ifconfig eth0
2016/05/23 21:28:07 :: ifconfig eth0
2016/05/23 21:28:11 :: ifconfig eth0
2016/05/23 21:28:15 :: ifconfig eth0
2016/05/23 21:28:19 :: ifconfig eth0
2016/05/23 21:28:23 :: ifconfig eth0
2016/05/23 21:28:27 :: ifconfig eth0
2016/05/23 21:28:31 :: ifconfig eth0
2016/05/23 21:28:35 :: ifconfig eth0
2016/05/23 21:28:39 :: ifconfig eth0
2016/05/23 21:28:43 :: ifconfig eth0
2016/05/23 21:28:47 :: ifconfig eth0
2016/05/23 21:28:51 :: ifconfig eth0
2016/05/23 21:28:55 :: ifconfig eth0
2016/05/23 21:28:59 :: ifconfig eth0
2016/05/23 21:29:03 :: ifconfig eth0
2016/05/23 21:29:07 :: ifconfig eth0
2016/05/23 21:29:11 :: ifconfig eth0
2016/05/23 21:29:15 :: ifconfig eth0
2016/05/23 21:29:17 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:29:17 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:29:17 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:29:17 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:29:17 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:29:17 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:29:17 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:29:17 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:29:17 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:29:17 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:29:17 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:29:17 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:29:17 :: attempting to set hostname with dhclient
2016/05/23 21:29:17 :: using dhcpcd or another supported client may work better
2016/05/23 21:29:17 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x11511289)
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:29:18 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:29:18 :: /sbin/ip route flush dev eth0
2016/05/23 21:29:18 :: ifconfig eth0 down
2016/05/23 21:29:18 :: ifconfig eth0 up
2016/05/23 21:29:18 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:29:18 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:29:18 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:29:18 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:29:18 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:29:18 :: Forced disconnect on
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:29:18 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:29:18 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:29:18 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:29:18 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:29:18 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:29:18 :: attempting to set hostname with dhclient
2016/05/23 21:29:18 :: using dhcpcd or another supported client may work better
2016/05/23 21:29:18 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.3.1
Copyright 2004-2014 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/d0:50:99:13:1d:4e
Sending on   LPF/eth0/d0:50:99:13:1d:4e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67 (xid=0x6a666063)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2470: Failed to send 300 byte long packet over fallback interface.
invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:29:18 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:29:18 :: /sbin/ip route flush dev eth0
2016/05/23 21:29:18 :: ifconfig eth0 down
2016/05/23 21:29:18 :: ifconfig eth0 up
2016/05/23 21:29:19 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:29:19 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:29:19 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:29:19 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:29:19 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:29:19 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:29:19 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2016/05/23 21:29:19 :: ifconfig eth0
2016/05/23 21:29:21 :: ifconfig eth0
2016/05/23 21:29:25 :: ifconfig eth0
2016/05/23 21:29:29 :: ifconfig eth0
2016/05/23 21:29:31 :: ifconfig eth0
2016/05/23 21:29:35 :: ifconfig eth0
2016/05/23 21:29:39 :: ifconfig eth0
2016/05/23 21:29:43 :: ifconfig eth0
2016/05/23 21:29:47 :: ifconfig eth0
2016/05/23 21:29:51 :: ifconfig eth0
2016/05/23 21:29:55 :: ifconfig eth0
2016/05/23 21:29:59 :: ifconfig eth0
2016/05/23 21:30:03 :: ifconfig eth0
2016/05/23 21:30:07 :: ifconfig eth0
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2016/05/23 21:40:37 :: ---------------------------
2016/05/23 21:40:37 :: wicd initializing...
2016/05/23 21:40:37 :: ---------------------------
2016/05/23 21:40:37 :: wicd is version 1.7.2.4 768
2016/05/23 21:40:37 :: setting backend to external
2016/05/23 21:40:37 :: trying to load backend external
2016/05/23 21:40:37 :: successfully loaded backend external
2016/05/23 21:40:37 :: WARNING: No path found for dhcpcd
2016/05/23 21:40:37 :: WARNING: No path found for pump
2016/05/23 21:40:37 :: WARNING: No path found for udhcpc
2016/05/23 21:40:37 :: WARNING: No path found for kdesu
2016/05/23 21:40:37 :: WARNING: No path found for ktsuss
2016/05/23 21:40:37 :: trying to load backend external
2016/05/23 21:40:37 :: successfully loaded backend external
2016/05/23 21:40:37 :: WARNING: No path found for dhcpcd
2016/05/23 21:40:37 :: WARNING: No path found for pump
2016/05/23 21:40:37 :: WARNING: No path found for udhcpc
2016/05/23 21:40:37 :: WARNING: No path found for kdesu
2016/05/23 21:40:37 :: WARNING: No path found for ktsuss
2016/05/23 21:40:37 :: Couldn't detect a wireless interface.
2016/05/23 21:40:37 :: setting wireless interface None
2016/05/23 21:40:37 :: automatically detected wired interface eth0
2016/05/23 21:40:37 :: setting wired interface eth0
2016/05/23 21:40:37 :: setting wpa driver wext
2016/05/23 21:40:37 :: setting use global dns to False
2016/05/23 21:40:37 :: setting global dns
2016/05/23 21:40:37 :: global dns servers are None None None
2016/05/23 21:40:37 :: domain is None
2016/05/23 21:40:37 :: search domain is None
2016/05/23 21:40:37 :: setting automatically reconnect when connection drops True
2016/05/23 21:40:37 :: found wired_connect_mode in configuration 1
2016/05/23 21:40:37 :: found should_verify_ap in configuration 1
2016/05/23 21:40:37 :: Setting dhcp client to 0
2016/05/23 21:40:37 :: found show_never_connect in configuration True
2016/05/23 21:40:37 :: Wireless configuration file found...
2016/05/23 21:40:37 :: Wired configuration file found...
2016/05/23 21:40:37 :: chmoding configuration files 0600...
2016/05/23 21:40:37 :: chowning configuration files root:root...
2016/05/23 21:40:37 :: Using wireless interface...
2016/05/23 21:40:37 :: Using wired interface...eth0
2016/05/23 21:40:37 :: scanning start
2016/05/23 21:40:37 :: scanning done
2016/05/23 21:40:37 :: found 0 networks:
2016/05/23 21:40:42 :: ifconfig eth0
2016/05/23 21:40:42 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:40:42 :: Autoconnecting...
2016/05/23 21:40:42 :: Starting wireless autoconnect...
2016/05/23 21:40:42 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:40:42 :: scanning start
2016/05/23 21:40:42 :: scanning done
2016/05/23 21:40:42 :: found 0 networks:
2016/05/23 21:40:42 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:40:47 :: ifconfig eth0
2016/05/23 21:40:47 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:40:47 :: Autoconnecting...
2016/05/23 21:40:47 :: Starting wireless autoconnect...
2016/05/23 21:40:47 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:40:47 :: scanning start
2016/05/23 21:40:47 :: scanning done
2016/05/23 21:40:47 :: found 0 networks:
2016/05/23 21:40:47 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:40:52 :: ifconfig eth0
2016/05/23 21:40:52 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:40:52 :: Autoconnecting...
2016/05/23 21:40:52 :: Starting wireless autoconnect...
2016/05/23 21:40:52 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:40:52 :: scanning start
2016/05/23 21:40:52 :: scanning done
2016/05/23 21:40:52 :: found 0 networks:
2016/05/23 21:40:52 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:40:57 :: ifconfig eth0
2016/05/23 21:40:57 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:40:57 :: Autoconnecting...
2016/05/23 21:40:57 :: Starting wired autoconnect...
2016/05/23 21:40:57 :: found default in configuration 1
2016/05/23 21:40:57 :: Reading wired profile wired-default
2016/05/23 21:40:57 :: found afterscript in configuration None
2016/05/23 21:40:57 :: found dhcphostname in configuration noahlub
2016/05/23 21:40:57 :: found postdisconnectscript in configuration None
2016/05/23 21:40:57 :: found dns_domain in configuration None
2016/05/23 21:40:57 :: found gateway in configuration None
2016/05/23 21:40:57 :: found use_global_dns in configuration False
2016/05/23 21:40:57 :: found lastused in configuration True
2016/05/23 21:40:57 :: found encryption_enabled in configuration False
2016/05/23 21:40:57 :: found beforescript in configuration None
2016/05/23 21:40:57 :: found ip in configuration None
2016/05/23 21:40:57 :: found broadcast in configuration None
2016/05/23 21:40:57 :: found netmask in configuration None
2016/05/23 21:40:57 :: found usedhcphostname in configuration 1
2016/05/23 21:40:57 :: found predisconnectscript in configuration None
2016/05/23 21:40:57 :: found enctype in configuration None
2016/05/23 21:40:57 :: found default in configuration 1
2016/05/23 21:40:57 :: found dns2 in configuration 8.8.4.4
2016/05/23 21:40:57 :: found search_domain in configuration None
2016/05/23 21:40:57 :: found use_static_dns in configuration True
2016/05/23 21:40:57 :: found dns3 in configuration None
2016/05/23 21:40:57 :: found profilename in configuration wired-default
2016/05/23 21:40:57 :: found dns1 in configuration 8.8.8.8
2016/05/23 21:40:57 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:40:57 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:40:57 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:40:57 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:40:57 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:40:57 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:40:57 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:40:57 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:40:57 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:40:57 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:40:57 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:40:57 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:40:58 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:40:58 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:40:58 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:40:58 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:40:58 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:40:58 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:40:58 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:40:58 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:40:58 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:40:58 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:40:58 :: attempting to set hostname with dhclient
2016/05/23 21:40:58 :: using dhcpcd or another supported client may work better
2016/05/23 21:40:58 :: /sbin/dhclient -v -r eth0
2016/05/23 21:40:58 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:40:58 :: /sbin/ip route flush dev eth0
2016/05/23 21:40:58 :: ifconfig eth0 down
2016/05/23 21:40:58 :: ifconfig eth0 up
2016/05/23 21:40:59 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:40:59 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:40:59 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:40:59 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:40:59 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:40:59 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:40:59 :: wpa_cli -i eth0 terminate
2016/05/23 21:40:59 :: found lastused in configuration True
2016/05/23 21:41:00 :: Attempting to autoconnect with wired interface...
2016/05/23 21:41:00 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 21:41:00 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 21:41:00 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 21:41:00 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 21:41:00 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 21:41:00 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 21:41:00 :: Putting interface down
2016/05/23 21:41:00 :: ifconfig eth0 down
2016/05/23 21:41:01 :: Releasing DHCP leases...
2016/05/23 21:41:01 :: attempting to set hostname with dhclient
2016/05/23 21:41:01 :: using dhcpcd or another supported client may work better
2016/05/23 21:41:01 :: /sbin/dhclient -v -r eth0
2016/05/23 21:41:01 :: Setting false IP...
2016/05/23 21:41:01 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:41:01 :: Stopping wpa_supplicant
2016/05/23 21:41:01 :: wpa_cli -i eth0 terminate
2016/05/23 21:41:01 :: Flushing the routing table...
2016/05/23 21:41:01 :: /sbin/ip route flush dev eth0
2016/05/23 21:41:01 :: Putting interface up...
2016/05/23 21:41:01 :: ifconfig eth0 up
2016/05/23 21:41:03 :: Running DHCP with hostname noahlub
2016/05/23 21:41:03 :: attempting to set hostname with dhclient
2016/05/23 21:41:03 :: using dhcpcd or another supported client may work better
2016/05/23 21:41:03 :: /sbin/dhclient -v eth0
2016/05/23 21:41:03 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 21:41:03 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 21:41:03 :: All rights reserved.
2016/05/23 21:41:03 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 21:41:03 :: 
2016/05/23 21:41:03 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:41:03 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:41:03 :: Sending on   Socket/fallback
2016/05/23 21:41:03 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xbd6c1a67)
2016/05/23 21:41:06 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0xbd6c1a67)
2016/05/23 21:41:07 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x671a6cbd)
2016/05/23 21:41:07 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 21:41:07 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 21:41:07 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:41:07 :: RTNETLINK answers: File exists
2016/05/23 21:41:07 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 21:41:07 :: bound to 162.228.104.207 -- renewal in 274 seconds.
2016/05/23 21:41:07 :: DHCP connection successful
2016/05/23 21:41:07 :: Setting DNS : 8.8.8.8
2016/05/23 21:41:07 :: Setting DNS : 8.8.4.4
2016/05/23 21:41:07 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 21:41:07 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 21:41:07 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 21:41:07 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 21:41:07 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 21:41:07 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 21:41:11 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 21:41:11 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 21:41:11 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 21:41:11 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 21:41:11 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 21:41:11 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 21:41:11 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 21:41:11 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 21:41:11 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 21:41:11 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:41:11 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:41:11 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 21:41:11 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 21:41:11 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 21:41:12 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 21:41:12 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 21:41:12 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 21:41:12 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 21:41:12 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 21:41:12 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 21:41:12 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 21:41:12 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 21:41:12 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 21:41:12 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 21:41:12 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 21:41:12 :: Connecting thread exiting.
2016/05/23 21:41:12 :: ifconfig eth0
2016/05/23 21:41:12 :: IP Address is: 162.228.104.207
2016/05/23 21:41:12 :: Sending connection attempt result success
2016/05/23 21:41:14 :: ifconfig eth0
2016/05/23 21:41:17 :: ifconfig eth0
2016/05/23 21:41:22 :: ifconfig eth0
2016/05/23 21:41:27 :: ifconfig eth0
2016/05/23 21:41:32 :: ifconfig eth0
2016/05/23 21:41:37 :: ifconfig eth0
2016/05/23 21:41:42 :: ifconfig eth0
2016/05/23 21:41:47 :: ifconfig eth0
2016/05/23 21:41:52 :: ifconfig eth0
2016/05/23 21:41:57 :: ifconfig eth0
2016/05/23 21:42:02 :: ifconfig eth0
2016/05/23 21:42:07 :: ifconfig eth0
2016/05/23 21:42:12 :: ifconfig eth0
2016/05/23 21:42:17 :: ifconfig eth0
2016/05/23 21:42:22 :: ifconfig eth0
2016/05/23 21:42:27 :: ifconfig eth0
2016/05/23 21:42:32 :: ifconfig eth0
2016/05/23 21:42:37 :: ifconfig eth0
2016/05/23 21:42:42 :: ifconfig eth0
2016/05/23 21:42:47 :: ifconfig eth0
2016/05/23 21:42:52 :: ifconfig eth0
2016/05/23 21:42:57 :: ifconfig eth0
2016/05/23 21:43:02 :: ifconfig eth0
2016/05/23 21:43:07 :: ifconfig eth0
2016/05/23 21:43:12 :: ifconfig eth0
2016/05/23 21:43:17 :: ifconfig eth0
2016/05/23 21:43:22 :: ifconfig eth0
2016/05/23 21:43:27 :: ifconfig eth0
2016/05/23 21:43:32 :: ifconfig eth0
2016/05/23 21:43:37 :: ifconfig eth0
2016/05/23 21:43:42 :: ifconfig eth0
2016/05/23 21:43:47 :: ifconfig eth0
2016/05/23 21:43:52 :: ifconfig eth0
2016/05/23 21:43:57 :: ifconfig eth0
2016/05/23 21:44:02 :: ifconfig eth0
2016/05/23 21:44:07 :: ifconfig eth0
2016/05/23 21:44:12 :: ifconfig eth0
2016/05/23 21:44:17 :: ifconfig eth0
2016/05/23 21:44:17 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:44:17 :: Autoconnecting...
2016/05/23 21:44:17 :: Starting wired autoconnect...
2016/05/23 21:44:17 :: found default in configuration 1
2016/05/23 21:44:17 :: Reading wired profile wired-default
2016/05/23 21:44:17 :: found afterscript in configuration None
2016/05/23 21:44:17 :: found dhcphostname in configuration noahlub
2016/05/23 21:44:17 :: found postdisconnectscript in configuration None
2016/05/23 21:44:17 :: found dns_domain in configuration None
2016/05/23 21:44:17 :: found gateway in configuration None
2016/05/23 21:44:17 :: found use_global_dns in configuration False
2016/05/23 21:44:17 :: found lastused in configuration True
2016/05/23 21:44:17 :: found encryption_enabled in configuration False
2016/05/23 21:44:17 :: found beforescript in configuration None
2016/05/23 21:44:17 :: found ip in configuration None
2016/05/23 21:44:17 :: found broadcast in configuration None
2016/05/23 21:44:17 :: found netmask in configuration None
2016/05/23 21:44:17 :: found usedhcphostname in configuration 1
2016/05/23 21:44:17 :: found predisconnectscript in configuration None
2016/05/23 21:44:17 :: found enctype in configuration None
2016/05/23 21:44:17 :: found default in configuration 1
2016/05/23 21:44:17 :: found dns2 in configuration 8.8.4.4
2016/05/23 21:44:17 :: found search_domain in configuration None
2016/05/23 21:44:17 :: found use_static_dns in configuration True
2016/05/23 21:44:17 :: found dns3 in configuration None
2016/05/23 21:44:17 :: found profilename in configuration wired-default
2016/05/23 21:44:17 :: found dns1 in configuration 8.8.8.8
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:44:17 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:44:17 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:44:17 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:44:17 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:44:17 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:44:18 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:44:18 :: attempting to set hostname with dhclient
2016/05/23 21:44:18 :: using dhcpcd or another supported client may work better
2016/05/23 21:44:18 :: /sbin/dhclient -v -r eth0
2016/05/23 21:44:19 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:44:19 :: /sbin/ip route flush dev eth0
2016/05/23 21:44:19 :: ifconfig eth0 down
2016/05/23 21:44:19 :: ifconfig eth0 up
2016/05/23 21:44:19 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:44:19 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:44:19 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:44:19 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:44:19 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:44:19 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:44:19 :: wpa_cli -i eth0 terminate
2016/05/23 21:44:19 :: found lastused in configuration True
2016/05/23 21:44:19 :: Attempting to autoconnect with wired interface...
2016/05/23 21:44:19 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 21:44:19 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 21:44:19 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 21:44:19 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 21:44:19 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 21:44:19 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 21:44:19 :: Putting interface down
2016/05/23 21:44:19 :: ifconfig eth0 down
2016/05/23 21:44:19 :: Releasing DHCP leases...
2016/05/23 21:44:19 :: attempting to set hostname with dhclient
2016/05/23 21:44:19 :: using dhcpcd or another supported client may work better
2016/05/23 21:44:19 :: /sbin/dhclient -v -r eth0
2016/05/23 21:44:20 :: Setting false IP...
2016/05/23 21:44:20 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:44:20 :: Stopping wpa_supplicant
2016/05/23 21:44:20 :: wpa_cli -i eth0 terminate
2016/05/23 21:44:20 :: Flushing the routing table...
2016/05/23 21:44:20 :: /sbin/ip route flush dev eth0
2016/05/23 21:44:20 :: Putting interface up...
2016/05/23 21:44:20 :: ifconfig eth0 up
2016/05/23 21:44:21 :: Forced disconnect on
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:44:21 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:44:21 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:44:21 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:44:21 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:44:21 :: attempting to set hostname with dhclient
2016/05/23 21:44:21 :: using dhcpcd or another supported client may work better
2016/05/23 21:44:21 :: /sbin/dhclient -v -r eth0
2016/05/23 21:44:21 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:44:21 :: /sbin/ip route flush dev eth0
2016/05/23 21:44:21 :: ifconfig eth0 down
2016/05/23 21:44:21 :: ifconfig eth0 up
2016/05/23 21:44:21 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:44:21 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:44:21 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:44:21 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:44:21 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:44:21 :: wpa_cli -i eth0 terminate
2016/05/23 21:44:22 :: Running DHCP with hostname noahlub
2016/05/23 21:44:22 :: attempting to set hostname with dhclient
2016/05/23 21:44:22 :: using dhcpcd or another supported client may work better
2016/05/23 21:44:22 :: /sbin/dhclient -v eth0
2016/05/23 21:44:22 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 21:44:22 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 21:44:22 :: All rights reserved.
2016/05/23 21:44:22 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 21:44:22 :: 
2016/05/23 21:44:22 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:44:22 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:44:22 :: Sending on   Socket/fallback
2016/05/23 21:44:22 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xbfa107d)
2016/05/23 21:44:25 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0xbfa107d)
2016/05/23 21:44:32 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 (xid=0xbfa107d)
2016/05/23 21:44:32 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x7d10fa0b)
2016/05/23 21:44:32 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 21:44:33 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 21:44:33 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:44:33 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 21:44:33 :: bound to 162.228.104.207 -- renewal in 295 seconds.
2016/05/23 21:44:33 :: DHCP connection successful
2016/05/23 21:44:33 :: Setting DNS : 8.8.8.8
2016/05/23 21:44:33 :: Setting DNS : 8.8.4.4
2016/05/23 21:44:33 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 21:44:33 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 21:44:33 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 21:44:33 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 21:44:33 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 21:44:33 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 21:44:37 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 21:44:37 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 21:44:38 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 21:44:38 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 21:44:38 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 21:44:38 :: Connecting thread exiting.
2016/05/23 21:44:38 :: ifconfig eth0
2016/05/23 21:44:38 :: IP Address is: None
2016/05/23 21:44:39 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:44:39 :: scanning start
2016/05/23 21:44:39 :: scanning done
2016/05/23 21:44:39 :: found 0 networks:
2016/05/23 21:44:39 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:44:41 :: Sending connection attempt result success
2016/05/23 21:44:41 :: ifconfig eth0
2016/05/23 21:44:41 :: Forced disconnect on
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:44:41 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:44:41 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:44:41 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:44:41 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:44:41 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:44:42 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:44:42 :: attempting to set hostname with dhclient
2016/05/23 21:44:42 :: using dhcpcd or another supported client may work better
2016/05/23 21:44:42 :: /sbin/dhclient -v -r eth0
2016/05/23 21:44:43 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:44:43 :: /sbin/ip route flush dev eth0
2016/05/23 21:44:43 :: ifconfig eth0 down
2016/05/23 21:44:43 :: ifconfig eth0 up
2016/05/23 21:44:43 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:44:43 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:44:43 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:44:43 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:44:43 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:44:43 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:44:43 :: wpa_cli -i eth0 terminate
2016/05/23 21:44:46 :: ifconfig eth0
2016/05/23 21:44:51 :: ifconfig eth0
2016/05/23 21:44:56 :: ifconfig eth0
2016/05/23 21:45:01 :: ifconfig eth0
2016/05/23 21:45:06 :: ifconfig eth0
2016/05/23 21:45:06 :: found default in configuration 1
2016/05/23 21:45:06 :: Reading wired profile wired-default
2016/05/23 21:45:06 :: found afterscript in configuration None
2016/05/23 21:45:06 :: found dhcphostname in configuration noahlub
2016/05/23 21:45:06 :: found postdisconnectscript in configuration None
2016/05/23 21:45:06 :: found dns_domain in configuration None
2016/05/23 21:45:06 :: found gateway in configuration None
2016/05/23 21:45:06 :: found use_global_dns in configuration False
2016/05/23 21:45:06 :: found lastused in configuration True
2016/05/23 21:45:06 :: found encryption_enabled in configuration False
2016/05/23 21:45:06 :: found beforescript in configuration None
2016/05/23 21:45:06 :: found ip in configuration None
2016/05/23 21:45:06 :: found broadcast in configuration None
2016/05/23 21:45:06 :: found netmask in configuration None
2016/05/23 21:45:06 :: found usedhcphostname in configuration 1
2016/05/23 21:45:06 :: found predisconnectscript in configuration None
2016/05/23 21:45:06 :: found enctype in configuration None
2016/05/23 21:45:06 :: found default in configuration 1
2016/05/23 21:45:06 :: found dns2 in configuration 8.8.4.4
2016/05/23 21:45:06 :: found search_domain in configuration None
2016/05/23 21:45:06 :: found use_static_dns in configuration True
2016/05/23 21:45:06 :: found dns3 in configuration None
2016/05/23 21:45:06 :: found profilename in configuration wired-default
2016/05/23 21:45:06 :: found dns1 in configuration 8.8.8.8
2016/05/23 21:45:06 :: found default in configuration 1
2016/05/23 21:45:06 :: saving wired profile wired-default
2016/05/23 21:45:06 :: scanning start
2016/05/23 21:45:06 :: scanning done
2016/05/23 21:45:06 :: found 0 networks:
2016/05/23 21:45:09 :: ifconfig eth0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:45:09 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:45:09 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:45:09 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:45:09 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:45:09 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:45:09 :: attempting to set hostname with dhclient
2016/05/23 21:45:09 :: using dhcpcd or another supported client may work better
2016/05/23 21:45:09 :: /sbin/dhclient -v -r eth0
2016/05/23 21:45:10 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:45:10 :: /sbin/ip route flush dev eth0
2016/05/23 21:45:10 :: ifconfig eth0 down
2016/05/23 21:45:10 :: ifconfig eth0 up
2016/05/23 21:45:10 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:45:10 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:45:10 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:45:10 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:45:10 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:45:10 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:45:10 :: wpa_cli -i eth0 terminate
2016/05/23 21:45:10 :: found lastused in configuration True
2016/05/23 21:45:10 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 21:45:10 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 21:45:10 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 21:45:10 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 21:45:10 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 21:45:10 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 21:45:10 :: Putting interface down
2016/05/23 21:45:10 :: ifconfig eth0 down
2016/05/23 21:45:10 :: Releasing DHCP leases...
2016/05/23 21:45:10 :: attempting to set hostname with dhclient
2016/05/23 21:45:10 :: using dhcpcd or another supported client may work better
2016/05/23 21:45:10 :: /sbin/dhclient -v -r eth0
2016/05/23 21:45:10 :: Setting false IP...
2016/05/23 21:45:10 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:45:10 :: Stopping wpa_supplicant
2016/05/23 21:45:10 :: wpa_cli -i eth0 terminate
2016/05/23 21:45:10 :: Flushing the routing table...
2016/05/23 21:45:10 :: /sbin/ip route flush dev eth0
2016/05/23 21:45:10 :: Putting interface up...
2016/05/23 21:45:10 :: ifconfig eth0 up
2016/05/23 21:45:12 :: Running DHCP with hostname noahlub
2016/05/23 21:45:12 :: attempting to set hostname with dhclient
2016/05/23 21:45:12 :: using dhcpcd or another supported client may work better
2016/05/23 21:45:12 :: /sbin/dhclient -v eth0
2016/05/23 21:45:12 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 21:45:12 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 21:45:12 :: All rights reserved.
2016/05/23 21:45:12 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 21:45:12 :: 
2016/05/23 21:45:12 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:45:12 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:45:12 :: Sending on   Socket/fallback
2016/05/23 21:45:12 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x7558a052)
2016/05/23 21:45:15 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 (xid=0x7558a052)
2016/05/23 21:45:15 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x52a05875)
2016/05/23 21:45:15 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 21:45:15 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 21:45:15 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:45:15 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 21:45:15 :: bound to 162.228.104.207 -- renewal in 299 seconds.
2016/05/23 21:45:15 :: DHCP connection successful
2016/05/23 21:45:15 :: Setting DNS : 8.8.8.8
2016/05/23 21:45:15 :: Setting DNS : 8.8.4.4
2016/05/23 21:45:15 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 21:45:15 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 21:45:15 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 21:45:15 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 21:45:15 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 21:45:15 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 21:45:19 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 21:45:19 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 21:45:20 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 21:45:20 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 21:45:20 :: Connecting thread exiting.
2016/05/23 21:45:20 :: ifconfig eth0
2016/05/23 21:45:20 :: IP Address is: 162.228.104.207
2016/05/23 21:45:20 :: Sending connection attempt result success
2016/05/23 21:45:22 :: ifconfig eth0
2016/05/23 21:45:24 :: ifconfig eth0
2016/05/23 21:45:28 :: ifconfig eth0
2016/05/23 21:45:28 :: Forced disconnect on
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:45:28 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:45:28 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:45:28 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:45:28 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:45:28 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:45:28 :: attempting to set hostname with dhclient
2016/05/23 21:45:28 :: using dhcpcd or another supported client may work better
2016/05/23 21:45:28 :: /sbin/dhclient -v -r eth0
2016/05/23 21:45:29 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:45:29 :: /sbin/ip route flush dev eth0
2016/05/23 21:45:29 :: ifconfig eth0 down
2016/05/23 21:45:29 :: ifconfig eth0 up
2016/05/23 21:45:30 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:45:30 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:45:30 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:45:30 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:45:30 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:45:30 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:45:30 :: wpa_cli -i eth0 terminate
2016/05/23 21:45:32 :: ifconfig eth0
2016/05/23 21:45:34 :: ifconfig eth0
2016/05/23 21:45:38 :: ifconfig eth0
2016/05/23 21:45:40 :: ifconfig eth0
2016/05/23 21:45:44 :: ifconfig eth0
2016/05/23 21:45:46 :: ifconfig eth0
2016/05/23 21:45:50 :: ifconfig eth0
2016/05/23 21:45:52 :: ifconfig eth0
2016/05/23 21:45:56 :: ifconfig eth0
2016/05/23 21:45:58 :: ifconfig eth0
2016/05/23 21:46:02 :: ifconfig eth0
2016/05/23 21:46:04 :: ifconfig eth0
2016/05/23 21:46:08 :: ifconfig eth0
2016/05/23 21:46:10 :: ifconfig eth0
2016/05/23 21:46:14 :: ifconfig eth0
2016/05/23 21:46:16 :: ifconfig eth0
2016/05/23 21:46:20 :: ifconfig eth0
2016/05/23 21:46:22 :: ifconfig eth0
2016/05/23 21:46:26 :: ifconfig eth0
2016/05/23 21:46:28 :: ifconfig eth0
2016/05/23 21:46:30 :: ifconfig eth0
2016/05/23 21:46:34 :: ifconfig eth0
2016/05/23 21:46:36 :: ifconfig eth0
2016/05/23 21:46:40 :: ifconfig eth0
2016/05/23 21:46:42 :: ifconfig eth0
2016/05/23 21:46:46 :: ifconfig eth0
2016/05/23 21:46:48 :: ifconfig eth0
2016/05/23 21:46:52 :: ifconfig eth0
2016/05/23 21:46:54 :: ifconfig eth0
2016/05/23 21:46:58 :: ifconfig eth0
2016/05/23 21:47:00 :: ifconfig eth0
2016/05/23 21:47:04 :: ifconfig eth0
2016/05/23 21:47:06 :: ifconfig eth0
2016/05/23 21:47:10 :: ifconfig eth0
2016/05/23 21:47:12 :: ifconfig eth0
2016/05/23 21:47:16 :: ifconfig eth0
2016/05/23 21:47:18 :: ifconfig eth0
2016/05/23 21:47:22 :: ifconfig eth0
2016/05/23 21:47:24 :: ifconfig eth0
2016/05/23 21:47:28 :: ifconfig eth0
2016/05/23 21:47:30 :: ifconfig eth0
2016/05/23 21:47:34 :: ifconfig eth0
2016/05/23 21:47:36 :: ifconfig eth0
2016/05/23 21:47:40 :: ifconfig eth0
2016/05/23 21:47:42 :: ifconfig eth0
2016/05/23 21:47:46 :: ifconfig eth0
2016/05/23 21:47:48 :: ifconfig eth0
2016/05/23 21:47:52 :: ifconfig eth0
2016/05/23 21:47:54 :: ifconfig eth0
2016/05/23 21:47:56 :: ifconfig eth0
2016/05/23 21:48:00 :: ifconfig eth0
2016/05/23 21:48:02 :: ifconfig eth0
2016/05/23 21:48:06 :: ifconfig eth0
2016/05/23 21:48:08 :: ifconfig eth0
2016/05/23 21:48:12 :: ifconfig eth0
2016/05/23 21:48:14 :: ifconfig eth0
2016/05/23 21:48:18 :: ifconfig eth0
2016/05/23 21:48:23 :: ifconfig eth0
2016/05/23 21:48:26 :: Daemon going down, killing wicd-monitor...
2016/05/23 21:48:26 :: Removing PID file...
2016/05/23 21:48:26 :: Shutting down...
2016/05/23 21:48:26 :: Exception KeyError: KeyError(-1219873024,) in <module 'threading' from '/usr/lib/python2.7/threading.pyo'> ignored
2016/05/23 21:54:45 :: ---------------------------
2016/05/23 21:54:45 :: wicd initializing...
2016/05/23 21:54:45 :: ---------------------------
2016/05/23 21:54:45 :: wicd is version 1.7.2.4 768
2016/05/23 21:54:45 :: setting backend to external
2016/05/23 21:54:45 :: trying to load backend external
2016/05/23 21:54:45 :: successfully loaded backend external
2016/05/23 21:54:46 :: WARNING: No path found for dhcpcd
2016/05/23 21:54:46 :: WARNING: No path found for pump
2016/05/23 21:54:46 :: WARNING: No path found for udhcpc
2016/05/23 21:54:46 :: WARNING: No path found for kdesu
2016/05/23 21:54:46 :: WARNING: No path found for ktsuss
2016/05/23 21:54:46 :: trying to load backend external
2016/05/23 21:54:46 :: successfully loaded backend external
2016/05/23 21:54:46 :: WARNING: No path found for dhcpcd
2016/05/23 21:54:46 :: WARNING: No path found for pump
2016/05/23 21:54:46 :: WARNING: No path found for udhcpc
2016/05/23 21:54:46 :: WARNING: No path found for kdesu
2016/05/23 21:54:46 :: WARNING: No path found for ktsuss
2016/05/23 21:54:46 :: Couldn't detect a wireless interface.
2016/05/23 21:54:46 :: setting wireless interface None
2016/05/23 21:54:46 :: automatically detected wired interface eth0
2016/05/23 21:54:46 :: setting wired interface eth0
2016/05/23 21:54:46 :: setting wpa driver wext
2016/05/23 21:54:46 :: setting use global dns to False
2016/05/23 21:54:46 :: setting global dns
2016/05/23 21:54:46 :: global dns servers are None None None
2016/05/23 21:54:46 :: domain is None
2016/05/23 21:54:46 :: search domain is None
2016/05/23 21:54:46 :: setting automatically reconnect when connection drops True
2016/05/23 21:54:46 :: found wired_connect_mode in configuration 1
2016/05/23 21:54:46 :: found should_verify_ap in configuration 1
2016/05/23 21:54:46 :: Setting dhcp client to 0
2016/05/23 21:54:46 :: found show_never_connect in configuration True
2016/05/23 21:54:46 :: Wireless configuration file found...
2016/05/23 21:54:46 :: Wired configuration file found...
2016/05/23 21:54:46 :: chmoding configuration files 0600...
2016/05/23 21:54:46 :: chowning configuration files root:root...
2016/05/23 21:54:46 :: Using wireless interface...
2016/05/23 21:54:46 :: Using wired interface...eth0
2016/05/23 21:54:46 :: scanning start
2016/05/23 21:54:46 :: scanning done
2016/05/23 21:54:46 :: found 0 networks:
2016/05/23 21:54:51 :: ifconfig eth0
2016/05/23 21:54:51 :: ifconfig eth0 up
2016/05/23 21:54:53 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:54:53 :: Autoconnecting...
2016/05/23 21:54:53 :: Starting wireless autoconnect...
2016/05/23 21:54:53 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:54:53 :: scanning start
2016/05/23 21:54:53 :: scanning done
2016/05/23 21:54:53 :: found 0 networks:
2016/05/23 21:54:53 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:54:56 :: ifconfig eth0
2016/05/23 21:54:56 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:54:56 :: Autoconnecting...
2016/05/23 21:54:56 :: Starting wired autoconnect...
2016/05/23 21:54:56 :: found default in configuration 1
2016/05/23 21:54:56 :: Reading wired profile wired-default
2016/05/23 21:54:56 :: found afterscript in configuration None
2016/05/23 21:54:56 :: found dhcphostname in configuration noahlub
2016/05/23 21:54:56 :: found postdisconnectscript in configuration None
2016/05/23 21:54:56 :: found dns_domain in configuration None
2016/05/23 21:54:56 :: found gateway in configuration None
2016/05/23 21:54:56 :: found use_global_dns in configuration False
2016/05/23 21:54:56 :: found lastused in configuration True
2016/05/23 21:54:56 :: found ip in configuration None
2016/05/23 21:54:56 :: found beforescript in configuration None
2016/05/23 21:54:56 :: found encryption_enabled in configuration False
2016/05/23 21:54:56 :: found broadcast in configuration None
2016/05/23 21:54:56 :: found netmask in configuration None
2016/05/23 21:54:56 :: found usedhcphostname in configuration 1
2016/05/23 21:54:56 :: found predisconnectscript in configuration None
2016/05/23 21:54:56 :: found enctype in configuration None
2016/05/23 21:54:56 :: found default in configuration 1
2016/05/23 21:54:56 :: found dns2 in configuration 8.8.4.4
2016/05/23 21:54:56 :: found search_domain in configuration None
2016/05/23 21:54:56 :: found use_static_dns in configuration True
2016/05/23 21:54:56 :: found dns3 in configuration None
2016/05/23 21:54:56 :: found profilename in configuration wired-default
2016/05/23 21:54:56 :: found dns1 in configuration 8.8.8.8
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:54:56 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:54:56 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:54:56 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:54:56 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:54:56 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:54:56 :: attempting to set hostname with dhclient
2016/05/23 21:54:56 :: using dhcpcd or another supported client may work better
2016/05/23 21:54:56 :: /sbin/dhclient -v -r eth0
2016/05/23 21:54:57 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:54:57 :: /sbin/ip route flush dev eth0
2016/05/23 21:54:57 :: ifconfig eth0 down
2016/05/23 21:54:57 :: ifconfig eth0 up
2016/05/23 21:54:57 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:54:57 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:54:57 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:54:57 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:54:57 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:54:57 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:54:57 :: wpa_cli -i eth0 terminate
2016/05/23 21:54:57 :: found lastused in configuration True
2016/05/23 21:54:57 :: Attempting to autoconnect with wired interface...
2016/05/23 21:54:57 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 21:54:57 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 21:54:57 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 21:54:57 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 21:54:57 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 21:54:57 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 21:54:57 :: Putting interface down
2016/05/23 21:54:57 :: ifconfig eth0 down
2016/05/23 21:54:57 :: Releasing DHCP leases...
2016/05/23 21:54:57 :: attempting to set hostname with dhclient
2016/05/23 21:54:57 :: using dhcpcd or another supported client may work better
2016/05/23 21:54:57 :: /sbin/dhclient -v -r eth0
2016/05/23 21:54:57 :: Setting false IP...
2016/05/23 21:54:57 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:54:58 :: Stopping wpa_supplicant
2016/05/23 21:54:58 :: wpa_cli -i eth0 terminate
2016/05/23 21:54:58 :: Flushing the routing table...
2016/05/23 21:54:58 :: /sbin/ip route flush dev eth0
2016/05/23 21:54:58 :: Putting interface up...
2016/05/23 21:54:58 :: ifconfig eth0 up
2016/05/23 21:55:00 :: Running DHCP with hostname noahlub
2016/05/23 21:55:00 :: attempting to set hostname with dhclient
2016/05/23 21:55:00 :: using dhcpcd or another supported client may work better
2016/05/23 21:55:00 :: /sbin/dhclient -v eth0
2016/05/23 21:55:00 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 21:55:00 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 21:55:00 :: All rights reserved.
2016/05/23 21:55:00 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 21:55:00 :: 
2016/05/23 21:55:00 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:55:00 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 21:55:00 :: Sending on   Socket/fallback
2016/05/23 21:55:00 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xe6765f77)
2016/05/23 21:55:03 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0xe6765f77)
2016/05/23 21:55:03 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x775f76e6)
2016/05/23 21:55:03 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 21:55:06 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x775f76e6)
2016/05/23 21:55:06 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 21:55:06 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 21:55:06 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 21:55:06 :: bound to 162.228.104.207 -- renewal in 258 seconds.
2016/05/23 21:55:06 :: DHCP connection successful
2016/05/23 21:55:06 :: Setting DNS : 8.8.8.8
2016/05/23 21:55:06 :: Setting DNS : 8.8.4.4
2016/05/23 21:55:06 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 21:55:06 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 21:55:06 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 21:55:06 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 21:55:06 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 21:55:06 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 21:55:10 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 21:55:10 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 21:55:10 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 21:55:10 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 21:55:11 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 21:55:11 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 21:55:11 :: Connecting thread exiting.
2016/05/23 21:55:11 :: ifconfig eth0
2016/05/23 21:55:11 :: IP Address is: 162.228.104.207
2016/05/23 21:55:14 :: Sending connection attempt result success
2016/05/23 21:55:14 :: ifconfig eth0
2016/05/23 21:55:19 :: ifconfig eth0
2016/05/23 21:55:24 :: ifconfig eth0
2016/05/23 21:55:29 :: ifconfig eth0
2016/05/23 21:55:34 :: ifconfig eth0
2016/05/23 21:55:39 :: ifconfig eth0
2016/05/23 21:55:44 :: ifconfig eth0
2016/05/23 21:55:49 :: ifconfig eth0
2016/05/23 21:55:54 :: ifconfig eth0
2016/05/23 21:55:59 :: ifconfig eth0
2016/05/23 21:56:04 :: ifconfig eth0
2016/05/23 21:56:09 :: ifconfig eth0
2016/05/23 21:56:14 :: ifconfig eth0
2016/05/23 21:56:19 :: ifconfig eth0
2016/05/23 21:56:24 :: ifconfig eth0
2016/05/23 21:56:29 :: ifconfig eth0
2016/05/23 21:56:29 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:56:29 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:56:29 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:56:29 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:56:29 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:56:29 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:56:29 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:56:29 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:56:29 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:56:29 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:56:29 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:56:29 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:56:29 :: attempting to set hostname with dhclient
2016/05/23 21:56:29 :: using dhcpcd or another supported client may work better
2016/05/23 21:56:29 :: /sbin/dhclient -v -r eth0
2016/05/23 21:56:30 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:56:30 :: /sbin/ip route flush dev eth0
2016/05/23 21:56:30 :: ifconfig eth0 down
2016/05/23 21:56:31 :: ifconfig eth0 up
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:56:31 :: wpa_cli -i eth0 terminate
2016/05/23 21:56:31 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:56:31 :: Autoconnecting...
2016/05/23 21:56:31 :: Starting wireless autoconnect...
2016/05/23 21:56:31 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:56:31 :: scanning start
2016/05/23 21:56:31 :: scanning done
2016/05/23 21:56:31 :: found 0 networks:
2016/05/23 21:56:31 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:56:31 :: Forced disconnect on
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 21:56:31 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 21:56:31 :: attempting to set hostname with dhclient
2016/05/23 21:56:31 :: using dhcpcd or another supported client may work better
2016/05/23 21:56:31 :: /sbin/dhclient -v -r eth0
2016/05/23 21:56:31 :: ifconfig eth0 0.0.0.0 
2016/05/23 21:56:31 :: /sbin/ip route flush dev eth0
2016/05/23 21:56:31 :: ifconfig eth0 down
2016/05/23 21:56:31 :: ifconfig eth0 up
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 21:56:31 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 21:56:31 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 21:56:31 :: wpa_cli -i eth0 terminate
2016/05/23 21:56:31 :: ifconfig eth0
2016/05/23 21:56:31 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:56:31 :: Autoconnecting...
2016/05/23 21:56:31 :: Starting wireless autoconnect...
2016/05/23 21:56:31 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:56:31 :: scanning start
2016/05/23 21:56:31 :: scanning done
2016/05/23 21:56:31 :: found 0 networks:
2016/05/23 21:56:31 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:56:36 :: ifconfig eth0
2016/05/23 21:56:36 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:56:36 :: Autoconnecting...
2016/05/23 21:56:36 :: Starting wireless autoconnect...
2016/05/23 21:56:36 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:56:36 :: scanning start
2016/05/23 21:56:36 :: scanning done
2016/05/23 21:56:36 :: found 0 networks:
2016/05/23 21:56:36 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:56:41 :: ifconfig eth0
2016/05/23 21:56:41 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 21:56:41 :: Autoconnecting...
2016/05/23 21:56:41 :: Starting wireless autoconnect...
2016/05/23 21:56:41 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 21:56:41 :: scanning start
2016/05/23 21:56:41 :: scanning done
2016/05/23 21:56:41 :: found 0 networks:
2016/05/23 21:56:41 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 21:56:46 :: ifconfig eth0
2016/05/23 21:56:51 :: ifconfig eth0
2016/05/23 21:56:56 :: ifconfig eth0
2016/05/23 21:57:01 :: ifconfig eth0
2016/05/23 21:57:06 :: ifconfig eth0
2016/05/23 21:57:11 :: ifconfig eth0
2016/05/23 21:57:16 :: ifconfig eth0
2016/05/23 21:57:21 :: ifconfig eth0
2016/05/23 21:57:26 :: ifconfig eth0
2016/05/23 21:57:31 :: ifconfig eth0
2016/05/23 21:57:36 :: ifconfig eth0
2016/05/23 21:57:41 :: ifconfig eth0
2016/05/23 21:57:46 :: ifconfig eth0
2016/05/23 21:57:51 :: ifconfig eth0
2016/05/23 21:57:56 :: ifconfig eth0
2016/05/23 21:58:01 :: ifconfig eth0
2016/05/23 21:58:06 :: ifconfig eth0
2016/05/23 21:58:11 :: ifconfig eth0
2016/05/23 21:58:16 :: ifconfig eth0
2016/05/23 21:58:21 :: ifconfig eth0
2016/05/23 21:58:26 :: ifconfig eth0
2016/05/23 21:58:31 :: ifconfig eth0
2016/05/23 21:58:36 :: ifconfig eth0
2016/05/23 21:58:41 :: ifconfig eth0
2016/05/23 21:58:46 :: ifconfig eth0
2016/05/23 21:58:51 :: ifconfig eth0
2016/05/23 21:58:56 :: ifconfig eth0
2016/05/23 21:59:01 :: ifconfig eth0
2016/05/23 21:59:06 :: ifconfig eth0
2016/05/23 21:59:11 :: ifconfig eth0
2016/05/23 21:59:16 :: ifconfig eth0
2016/05/23 21:59:21 :: ifconfig eth0
2016/05/23 21:59:26 :: ifconfig eth0
2016/05/23 21:59:31 :: ifconfig eth0
2016/05/23 21:59:36 :: ifconfig eth0
2016/05/23 21:59:41 :: ifconfig eth0
2016/05/23 21:59:46 :: ifconfig eth0
2016/05/23 21:59:51 :: ifconfig eth0
2016/05/23 21:59:56 :: ifconfig eth0
2016/05/23 22:00:01 :: ifconfig eth0
2016/05/23 22:00:06 :: ifconfig eth0
2016/05/23 22:00:06 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 22:00:06 :: Autoconnecting...
2016/05/23 22:00:06 :: Starting wired autoconnect...
2016/05/23 22:00:06 :: found default in configuration 1
2016/05/23 22:00:06 :: Reading wired profile wired-default
2016/05/23 22:00:06 :: found afterscript in configuration None
2016/05/23 22:00:06 :: found dhcphostname in configuration noahlub
2016/05/23 22:00:06 :: found postdisconnectscript in configuration None
2016/05/23 22:00:06 :: found dns_domain in configuration None
2016/05/23 22:00:06 :: found gateway in configuration None
2016/05/23 22:00:06 :: found use_global_dns in configuration False
2016/05/23 22:00:06 :: found lastused in configuration True
2016/05/23 22:00:06 :: found ip in configuration None
2016/05/23 22:00:06 :: found beforescript in configuration None
2016/05/23 22:00:06 :: found encryption_enabled in configuration False
2016/05/23 22:00:06 :: found broadcast in configuration None
2016/05/23 22:00:06 :: found netmask in configuration None
2016/05/23 22:00:06 :: found usedhcphostname in configuration 1
2016/05/23 22:00:06 :: found predisconnectscript in configuration None
2016/05/23 22:00:06 :: found enctype in configuration None
2016/05/23 22:00:06 :: found default in configuration 1
2016/05/23 22:00:06 :: found dns2 in configuration 8.8.4.4
2016/05/23 22:00:06 :: found search_domain in configuration None
2016/05/23 22:00:06 :: found use_static_dns in configuration True
2016/05/23 22:00:06 :: found dns3 in configuration None
2016/05/23 22:00:06 :: found profilename in configuration wired-default
2016/05/23 22:00:06 :: found dns1 in configuration 8.8.8.8
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:00:06 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:00:06 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:00:06 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:00:06 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:00:06 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:00:06 :: attempting to set hostname with dhclient
2016/05/23 22:00:06 :: using dhcpcd or another supported client may work better
2016/05/23 22:00:06 :: /sbin/dhclient -v -r eth0
2016/05/23 22:00:07 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:00:07 :: /sbin/ip route flush dev eth0
2016/05/23 22:00:07 :: ifconfig eth0 down
2016/05/23 22:00:07 :: ifconfig eth0 up
2016/05/23 22:00:07 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:00:07 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:00:07 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:00:07 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:00:07 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:00:07 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:00:07 :: wpa_cli -i eth0 terminate
2016/05/23 22:00:07 :: found lastused in configuration True
2016/05/23 22:00:07 :: Attempting to autoconnect with wired interface...
2016/05/23 22:00:07 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 22:00:07 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 22:00:07 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 22:00:07 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 22:00:07 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 22:00:07 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 22:00:07 :: Putting interface down
2016/05/23 22:00:07 :: ifconfig eth0 down
2016/05/23 22:00:07 :: Releasing DHCP leases...
2016/05/23 22:00:07 :: attempting to set hostname with dhclient
2016/05/23 22:00:07 :: using dhcpcd or another supported client may work better
2016/05/23 22:00:07 :: /sbin/dhclient -v -r eth0
2016/05/23 22:00:07 :: Setting false IP...
2016/05/23 22:00:07 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:00:07 :: Stopping wpa_supplicant
2016/05/23 22:00:07 :: wpa_cli -i eth0 terminate
2016/05/23 22:00:07 :: Flushing the routing table...
2016/05/23 22:00:07 :: /sbin/ip route flush dev eth0
2016/05/23 22:00:07 :: Putting interface up...
2016/05/23 22:00:07 :: ifconfig eth0 up
2016/05/23 22:00:09 :: Running DHCP with hostname noahlub
2016/05/23 22:00:09 :: attempting to set hostname with dhclient
2016/05/23 22:00:09 :: using dhcpcd or another supported client may work better
2016/05/23 22:00:09 :: /sbin/dhclient -v eth0
2016/05/23 22:00:09 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 22:00:09 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 22:00:09 :: All rights reserved.
2016/05/23 22:00:09 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 22:00:09 :: 
2016/05/23 22:00:09 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:00:09 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:00:09 :: Sending on   Socket/fallback
2016/05/23 22:00:09 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x386f8f3f)
2016/05/23 22:00:12 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x386f8f3f)
2016/05/23 22:00:12 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x3f8f6f38)
2016/05/23 22:00:12 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 22:00:13 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 22:00:13 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 22:00:13 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 22:00:13 :: bound to 162.228.104.207 -- renewal in 268 seconds.
2016/05/23 22:00:13 :: DHCP connection successful
2016/05/23 22:00:13 :: Setting DNS : 8.8.8.8
2016/05/23 22:00:13 :: Setting DNS : 8.8.4.4
2016/05/23 22:00:13 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 22:00:13 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 22:00:13 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 22:00:13 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 22:00:13 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 22:00:13 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 22:00:17 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 22:00:17 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 22:00:18 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 22:00:18 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 22:00:18 :: Connecting thread exiting.
2016/05/23 22:00:18 :: ifconfig eth0
2016/05/23 22:00:18 :: IP Address is: 162.228.104.207
2016/05/23 22:00:18 :: Sending connection attempt result success
2016/05/23 22:00:20 :: ifconfig eth0
2016/05/23 22:00:23 :: ifconfig eth0
2016/05/23 22:00:28 :: ifconfig eth0
2016/05/23 22:00:33 :: ifconfig eth0
2016/05/23 22:00:38 :: ifconfig eth0
2016/05/23 22:00:43 :: ifconfig eth0
2016/05/23 22:00:48 :: ifconfig eth0
2016/05/23 22:00:53 :: ifconfig eth0
2016/05/23 22:00:58 :: ifconfig eth0
2016/05/23 22:01:03 :: ifconfig eth0
2016/05/23 22:01:03 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:01:03 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:01:03 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:01:03 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:01:03 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:01:03 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:01:03 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:01:03 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:01:03 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:01:03 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:01:03 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:01:03 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:01:03 :: attempting to set hostname with dhclient
2016/05/23 22:01:03 :: using dhcpcd or another supported client may work better
2016/05/23 22:01:03 :: /sbin/dhclient -v -r eth0
2016/05/23 22:01:05 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:01:05 :: /sbin/ip route flush dev eth0
2016/05/23 22:01:05 :: ifconfig eth0 down
2016/05/23 22:01:05 :: ifconfig eth0 up
2016/05/23 22:01:05 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:01:05 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:01:05 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:01:05 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:01:05 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:01:05 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:01:05 :: wpa_cli -i eth0 terminate
2016/05/23 22:01:05 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 22:01:05 :: Autoconnecting...
2016/05/23 22:01:05 :: Starting wireless autoconnect...
2016/05/23 22:01:05 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 22:01:05 :: scanning start
2016/05/23 22:01:05 :: scanning done
2016/05/23 22:01:05 :: found 0 networks:
2016/05/23 22:01:05 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 22:01:05 :: Forced disconnect on
2016/05/23 22:01:05 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:01:05 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:01:05 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:01:05 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:01:05 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:01:05 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:01:05 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:01:06 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:01:06 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:01:06 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:01:06 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:01:06 :: attempting to set hostname with dhclient
2016/05/23 22:01:06 :: using dhcpcd or another supported client may work better
2016/05/23 22:01:06 :: /sbin/dhclient -v -r eth0
2016/05/23 22:01:06 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:01:06 :: /sbin/ip route flush dev eth0
2016/05/23 22:01:06 :: ifconfig eth0 down
2016/05/23 22:01:06 :: ifconfig eth0 up
2016/05/23 22:01:06 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:01:06 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:01:06 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:01:06 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:01:06 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:01:06 :: wpa_cli -i eth0 terminate
2016/05/23 22:01:06 :: ifconfig eth0
2016/05/23 22:01:06 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 22:01:06 :: Autoconnecting...
2016/05/23 22:01:06 :: Starting wireless autoconnect...
2016/05/23 22:01:06 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 22:01:06 :: scanning start
2016/05/23 22:01:06 :: scanning done
2016/05/23 22:01:06 :: found 0 networks:
2016/05/23 22:01:06 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 22:01:11 :: ifconfig eth0
2016/05/23 22:01:11 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 22:01:11 :: Autoconnecting...
2016/05/23 22:01:11 :: Starting wireless autoconnect...
2016/05/23 22:01:11 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 22:01:11 :: scanning start
2016/05/23 22:01:11 :: scanning done
2016/05/23 22:01:11 :: found 0 networks:
2016/05/23 22:01:11 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 22:01:16 :: ifconfig eth0
2016/05/23 22:01:16 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 22:01:16 :: Autoconnecting...
2016/05/23 22:01:16 :: Starting wireless autoconnect...
2016/05/23 22:01:16 :: No wired connection present, attempting to autoconnect to wireless network
2016/05/23 22:01:16 :: scanning start
2016/05/23 22:01:16 :: scanning done
2016/05/23 22:01:16 :: found 0 networks:
2016/05/23 22:01:16 :: Unable to autoconnect, you'll have to manually connect
2016/05/23 22:01:21 :: ifconfig eth0
2016/05/23 22:01:26 :: ifconfig eth0
2016/05/23 22:01:31 :: ifconfig eth0
2016/05/23 22:01:36 :: ifconfig eth0
2016/05/23 22:01:41 :: ifconfig eth0
2016/05/23 22:01:46 :: ifconfig eth0
2016/05/23 22:01:51 :: ifconfig eth0
2016/05/23 22:01:56 :: ifconfig eth0
2016/05/23 22:02:01 :: ifconfig eth0
2016/05/23 22:02:06 :: ifconfig eth0
2016/05/23 22:02:11 :: ifconfig eth0
2016/05/23 22:02:16 :: ifconfig eth0
2016/05/23 22:02:21 :: ifconfig eth0
2016/05/23 22:02:26 :: ifconfig eth0
2016/05/23 22:02:31 :: ifconfig eth0
2016/05/23 22:02:36 :: ifconfig eth0
2016/05/23 22:02:41 :: ifconfig eth0
2016/05/23 22:02:46 :: ifconfig eth0
2016/05/23 22:02:51 :: ifconfig eth0
2016/05/23 22:02:56 :: ifconfig eth0
2016/05/23 22:03:01 :: ifconfig eth0
2016/05/23 22:03:06 :: ifconfig eth0
2016/05/23 22:03:11 :: ifconfig eth0
2016/05/23 22:03:16 :: ifconfig eth0
2016/05/23 22:03:21 :: ifconfig eth0
2016/05/23 22:03:26 :: ifconfig eth0
2016/05/23 22:03:31 :: ifconfig eth0
2016/05/23 22:03:36 :: ifconfig eth0
2016/05/23 22:03:41 :: ifconfig eth0
2016/05/23 22:03:46 :: ifconfig eth0
2016/05/23 22:03:51 :: ifconfig eth0
2016/05/23 22:03:56 :: ifconfig eth0
2016/05/23 22:04:01 :: ifconfig eth0
2016/05/23 22:04:06 :: ifconfig eth0
2016/05/23 22:04:11 :: ifconfig eth0
2016/05/23 22:04:16 :: ifconfig eth0
2016/05/23 22:04:21 :: ifconfig eth0
2016/05/23 22:04:26 :: ifconfig eth0
2016/05/23 22:04:31 :: ifconfig eth0
2016/05/23 22:04:36 :: ifconfig eth0
2016/05/23 22:04:36 :: GetCurrentNetworkID: Returning -1, current network not found
2016/05/23 22:04:36 :: Autoconnecting...
2016/05/23 22:04:36 :: Starting wired autoconnect...
2016/05/23 22:04:36 :: found default in configuration 1
2016/05/23 22:04:36 :: Reading wired profile wired-default
2016/05/23 22:04:36 :: found afterscript in configuration None
2016/05/23 22:04:36 :: found dhcphostname in configuration noahlub
2016/05/23 22:04:36 :: found postdisconnectscript in configuration None
2016/05/23 22:04:36 :: found dns_domain in configuration None
2016/05/23 22:04:36 :: found gateway in configuration None
2016/05/23 22:04:36 :: found use_global_dns in configuration False
2016/05/23 22:04:36 :: found lastused in configuration True
2016/05/23 22:04:36 :: found ip in configuration None
2016/05/23 22:04:36 :: found beforescript in configuration None
2016/05/23 22:04:36 :: found encryption_enabled in configuration False
2016/05/23 22:04:36 :: found broadcast in configuration None
2016/05/23 22:04:36 :: found netmask in configuration None
2016/05/23 22:04:36 :: found usedhcphostname in configuration 1
2016/05/23 22:04:36 :: found predisconnectscript in configuration None
2016/05/23 22:04:36 :: found enctype in configuration None
2016/05/23 22:04:36 :: found default in configuration 1
2016/05/23 22:04:36 :: found dns2 in configuration 8.8.4.4
2016/05/23 22:04:36 :: found search_domain in configuration None
2016/05/23 22:04:36 :: found use_static_dns in configuration True
2016/05/23 22:04:36 :: found dns3 in configuration None
2016/05/23 22:04:36 :: found profilename in configuration wired-default
2016/05/23 22:04:36 :: found dns1 in configuration 8.8.8.8
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:04:36 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:04:36 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:04:36 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:04:36 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:04:36 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:04:36 :: attempting to set hostname with dhclient
2016/05/23 22:04:36 :: using dhcpcd or another supported client may work better
2016/05/23 22:04:36 :: /sbin/dhclient -v -r eth0
2016/05/23 22:04:37 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:04:37 :: /sbin/ip route flush dev eth0
2016/05/23 22:04:37 :: ifconfig eth0 down
2016/05/23 22:04:37 :: ifconfig eth0 up
2016/05/23 22:04:37 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:04:37 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:04:37 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:04:37 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:04:37 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:04:37 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:04:37 :: wpa_cli -i eth0 terminate
2016/05/23 22:04:37 :: found lastused in configuration True
2016/05/23 22:04:37 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 22:04:37 :: Attempting to autoconnect with wired interface...
2016/05/23 22:04:37 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 22:04:37 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 22:04:37 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 22:04:37 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 22:04:37 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 22:04:37 :: Putting interface down
2016/05/23 22:04:37 :: ifconfig eth0 down
2016/05/23 22:04:37 :: Releasing DHCP leases...
2016/05/23 22:04:37 :: attempting to set hostname with dhclient
2016/05/23 22:04:37 :: using dhcpcd or another supported client may work better
2016/05/23 22:04:37 :: /sbin/dhclient -v -r eth0
2016/05/23 22:04:38 :: Setting false IP...
2016/05/23 22:04:38 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:04:38 :: Stopping wpa_supplicant
2016/05/23 22:04:38 :: wpa_cli -i eth0 terminate
2016/05/23 22:04:38 :: Flushing the routing table...
2016/05/23 22:04:38 :: /sbin/ip route flush dev eth0
2016/05/23 22:04:38 :: Putting interface up...
2016/05/23 22:04:38 :: ifconfig eth0 up
2016/05/23 22:04:40 :: Running DHCP with hostname noahlub
2016/05/23 22:04:40 :: attempting to set hostname with dhclient
2016/05/23 22:04:40 :: using dhcpcd or another supported client may work better
2016/05/23 22:04:40 :: /sbin/dhclient -v eth0
2016/05/23 22:04:40 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 22:04:40 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 22:04:40 :: All rights reserved.
2016/05/23 22:04:40 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 22:04:40 :: 
2016/05/23 22:04:40 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:04:40 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:04:40 :: Sending on   Socket/fallback
2016/05/23 22:04:40 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x37006601)
2016/05/23 22:04:43 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0x37006601)
2016/05/23 22:04:43 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x1660037)
2016/05/23 22:04:43 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 22:04:43 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 22:04:43 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 22:04:43 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 22:04:43 :: bound to 162.228.104.207 -- renewal in 248 seconds.
2016/05/23 22:04:43 :: DHCP connection successful
2016/05/23 22:04:43 :: Setting DNS : 8.8.8.8
2016/05/23 22:04:43 :: Setting DNS : 8.8.4.4
2016/05/23 22:04:43 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 22:04:43 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 22:04:43 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 22:04:43 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 22:04:43 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 22:04:43 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 22:04:47 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 22:04:47 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 22:04:47 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 22:04:47 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 22:04:47 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 22:04:47 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 22:04:47 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 22:04:47 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 22:04:47 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 22:04:47 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:04:47 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:04:47 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 22:04:48 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 22:04:48 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 22:04:48 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 22:04:48 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 22:04:48 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 22:04:48 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 22:04:48 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 22:04:48 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 22:04:48 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 22:04:48 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 22:04:48 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 22:04:48 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 22:04:48 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 22:04:48 :: Connecting thread exiting.
2016/05/23 22:04:48 :: ifconfig eth0
2016/05/23 22:04:48 :: IP Address is: 162.228.104.207
2016/05/23 22:04:48 :: Sending connection attempt result success
2016/05/23 22:04:50 :: ifconfig eth0
2016/05/23 22:04:52 :: ifconfig eth0
2016/05/23 22:04:54 :: ifconfig eth0
2016/05/23 22:04:56 :: ifconfig eth0
2016/05/23 22:04:58 :: ifconfig eth0
2016/05/23 22:04:59 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:04:59 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:04:59 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:04:59 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:04:59 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:04:59 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:04:59 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:04:59 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:04:59 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:04:59 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:04:59 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:04:59 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:04:59 :: attempting to set hostname with dhclient
2016/05/23 22:04:59 :: using dhcpcd or another supported client may work better
2016/05/23 22:04:59 :: /sbin/dhclient -v -r eth0
2016/05/23 22:05:01 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:05:01 :: /sbin/ip route flush dev eth0
2016/05/23 22:05:01 :: ifconfig eth0 down
2016/05/23 22:05:01 :: ifconfig eth0 up
2016/05/23 22:05:01 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:05:01 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:05:01 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:05:01 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:05:01 :: wpa_cli -i eth0 terminate
2016/05/23 22:05:01 :: Forced disconnect on
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:05:01 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:05:01 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:05:01 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:05:01 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:05:01 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:05:01 :: attempting to set hostname with dhclient
2016/05/23 22:05:01 :: using dhcpcd or another supported client may work better
2016/05/23 22:05:01 :: /sbin/dhclient -v -r eth0
2016/05/23 22:05:01 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:05:01 :: /sbin/ip route flush dev eth0
2016/05/23 22:05:01 :: ifconfig eth0 down
2016/05/23 22:05:01 :: ifconfig eth0 up
2016/05/23 22:05:02 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:05:02 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:05:02 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:05:02 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:05:02 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:05:02 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:05:02 :: wpa_cli -i eth0 terminate
2016/05/23 22:05:02 :: ifconfig eth0
2016/05/23 22:05:04 :: ifconfig eth0
2016/05/23 22:05:06 :: ifconfig eth0
2016/05/23 22:05:08 :: ifconfig eth0
2016/05/23 22:05:10 :: ifconfig eth0
2016/05/23 22:05:12 :: ifconfig eth0
2016/05/23 22:05:14 :: ifconfig eth0
2016/05/23 22:05:16 :: ifconfig eth0
2016/05/23 22:05:18 :: ifconfig eth0
2016/05/23 22:05:20 :: ifconfig eth0
2016/05/23 22:05:22 :: ifconfig eth0
2016/05/23 22:05:24 :: ifconfig eth0
2016/05/23 22:05:26 :: ifconfig eth0
2016/05/23 22:05:28 :: ifconfig eth0
2016/05/23 22:05:30 :: ifconfig eth0
2016/05/23 22:05:32 :: ifconfig eth0
2016/05/23 22:05:34 :: ifconfig eth0
2016/05/23 22:05:36 :: ifconfig eth0
2016/05/23 22:05:38 :: ifconfig eth0
2016/05/23 22:05:41 :: ifconfig eth0
2016/05/23 22:05:43 :: ifconfig eth0
2016/05/23 22:05:45 :: ifconfig eth0
2016/05/23 22:05:47 :: ifconfig eth0
2016/05/23 22:05:49 :: ifconfig eth0
2016/05/23 22:05:51 :: ifconfig eth0
2016/05/23 22:05:53 :: ifconfig eth0
2016/05/23 22:05:55 :: ifconfig eth0
2016/05/23 22:05:57 :: ifconfig eth0
2016/05/23 22:06:00 :: ifconfig eth0
2016/05/23 22:06:02 :: ifconfig eth0
2016/05/23 22:06:04 :: ifconfig eth0
2016/05/23 22:06:06 :: ifconfig eth0
2016/05/23 22:06:08 :: ifconfig eth0
2016/05/23 22:06:10 :: ifconfig eth0
2016/05/23 22:06:12 :: ifconfig eth0
2016/05/23 22:06:14 :: ifconfig eth0
2016/05/23 22:06:16 :: ifconfig eth0
2016/05/23 22:06:18 :: ifconfig eth0
2016/05/23 22:06:20 :: ifconfig eth0
2016/05/23 22:06:22 :: ifconfig eth0
2016/05/23 22:06:25 :: ifconfig eth0
2016/05/23 22:06:27 :: ifconfig eth0
2016/05/23 22:06:29 :: ifconfig eth0
2016/05/23 22:06:31 :: ifconfig eth0
2016/05/23 22:06:33 :: ifconfig eth0
2016/05/23 22:06:36 :: ifconfig eth0
2016/05/23 22:06:38 :: ifconfig eth0
2016/05/23 22:06:40 :: ifconfig eth0
2016/05/23 22:06:42 :: ifconfig eth0
2016/05/23 22:06:44 :: ifconfig eth0
2016/05/23 22:06:46 :: ifconfig eth0
2016/05/23 22:06:48 :: ifconfig eth0
2016/05/23 22:06:50 :: ifconfig eth0
2016/05/23 22:06:52 :: ifconfig eth0
2016/05/23 22:06:54 :: ifconfig eth0
2016/05/23 22:06:56 :: ifconfig eth0
2016/05/23 22:06:58 :: ifconfig eth0
2016/05/23 22:07:00 :: ifconfig eth0
2016/05/23 22:07:02 :: ifconfig eth0
2016/05/23 22:07:04 :: ifconfig eth0
2016/05/23 22:07:06 :: ifconfig eth0
2016/05/23 22:07:08 :: ifconfig eth0
2016/05/23 22:07:10 :: ifconfig eth0
2016/05/23 22:07:12 :: ifconfig eth0
2016/05/23 22:07:14 :: ifconfig eth0
2016/05/23 22:07:17 :: ifconfig eth0
2016/05/23 22:07:19 :: ifconfig eth0
2016/05/23 22:07:21 :: ifconfig eth0
2016/05/23 22:07:23 :: ifconfig eth0
2016/05/23 22:07:25 :: ifconfig eth0
2016/05/23 22:07:27 :: ifconfig eth0
2016/05/23 22:07:29 :: ifconfig eth0
2016/05/23 22:07:31 :: ifconfig eth0
2016/05/23 22:07:34 :: ifconfig eth0
2016/05/23 22:07:36 :: ifconfig eth0
2016/05/23 22:07:39 :: ifconfig eth0
2016/05/23 22:07:41 :: ifconfig eth0
2016/05/23 22:07:43 :: ifconfig eth0
2016/05/23 22:07:45 :: ifconfig eth0
2016/05/23 22:07:47 :: ifconfig eth0
2016/05/23 22:07:49 :: ifconfig eth0
2016/05/23 22:07:51 :: ifconfig eth0
2016/05/23 22:07:54 :: ifconfig eth0
2016/05/23 22:07:56 :: ifconfig eth0
2016/05/23 22:07:58 :: ifconfig eth0
2016/05/23 22:08:00 :: ifconfig eth0
2016/05/23 22:08:03 :: ifconfig eth0
2016/05/23 22:08:05 :: ifconfig eth0
2016/05/23 22:08:07 :: ifconfig eth0
2016/05/23 22:08:09 :: ifconfig eth0
2016/05/23 22:08:11 :: ifconfig eth0
2016/05/23 22:08:14 :: ifconfig eth0
2016/05/23 22:08:16 :: ifconfig eth0
2016/05/23 22:08:18 :: ifconfig eth0
2016/05/23 22:08:21 :: ifconfig eth0
2016/05/23 22:08:23 :: ifconfig eth0
2016/05/23 22:08:25 :: ifconfig eth0
2016/05/23 22:08:28 :: ifconfig eth0
2016/05/23 22:08:30 :: ifconfig eth0
2016/05/23 22:08:32 :: ifconfig eth0
2016/05/23 22:08:34 :: ifconfig eth0
2016/05/23 22:08:36 :: ifconfig eth0
2016/05/23 22:08:38 :: ifconfig eth0
2016/05/23 22:08:40 :: ifconfig eth0
2016/05/23 22:08:42 :: ifconfig eth0
2016/05/23 22:08:44 :: ifconfig eth0
2016/05/23 22:08:47 :: ifconfig eth0
2016/05/23 22:08:49 :: ifconfig eth0
2016/05/23 22:08:51 :: ifconfig eth0
2016/05/23 22:08:54 :: ifconfig eth0
2016/05/23 22:08:56 :: ifconfig eth0
2016/05/23 22:08:58 :: ifconfig eth0
2016/05/23 22:09:00 :: ifconfig eth0
2016/05/23 22:09:02 :: ifconfig eth0
2016/05/23 22:09:04 :: ifconfig eth0
2016/05/23 22:09:07 :: ifconfig eth0
2016/05/23 22:09:09 :: ifconfig eth0
2016/05/23 22:09:11 :: ifconfig eth0
2016/05/23 22:09:13 :: ifconfig eth0
2016/05/23 22:09:16 :: ifconfig eth0
2016/05/23 22:09:18 :: ifconfig eth0
2016/05/23 22:09:20 :: ifconfig eth0
2016/05/23 22:09:23 :: ifconfig eth0
2016/05/23 22:09:25 :: ifconfig eth0
2016/05/23 22:09:27 :: ifconfig eth0
2016/05/23 22:09:29 :: ifconfig eth0
2016/05/23 22:09:31 :: ifconfig eth0
2016/05/23 22:09:33 :: ifconfig eth0
2016/05/23 22:09:36 :: ifconfig eth0
2016/05/23 22:09:38 :: ifconfig eth0
2016/05/23 22:09:41 :: ifconfig eth0
2016/05/23 22:09:43 :: ifconfig eth0
2016/05/23 22:09:45 :: ifconfig eth0
2016/05/23 22:09:47 :: ifconfig eth0
2016/05/23 22:09:50 :: ifconfig eth0
2016/05/23 22:09:52 :: ifconfig eth0
2016/05/23 22:09:55 :: ifconfig eth0
2016/05/23 22:09:57 :: ifconfig eth0
2016/05/23 22:09:59 :: ifconfig eth0
2016/05/23 22:10:01 :: ifconfig eth0
2016/05/23 22:10:03 :: ifconfig eth0
2016/05/23 22:10:05 :: ifconfig eth0
2016/05/23 22:10:08 :: ifconfig eth0
2016/05/23 22:10:10 :: ifconfig eth0
2016/05/23 22:10:12 :: ifconfig eth0
2016/05/23 22:10:14 :: ifconfig eth0
2016/05/23 22:10:16 :: ifconfig eth0
2016/05/23 22:10:19 :: ifconfig eth0
2016/05/23 22:10:21 :: ifconfig eth0
2016/05/23 22:10:23 :: ifconfig eth0
2016/05/23 22:10:26 :: ifconfig eth0
2016/05/23 22:10:28 :: ifconfig eth0
2016/05/23 22:10:30 :: ifconfig eth0
2016/05/23 22:10:32 :: ifconfig eth0
2016/05/23 22:10:35 :: ifconfig eth0
2016/05/23 22:10:37 :: ifconfig eth0
2016/05/23 22:10:39 :: ifconfig eth0
2016/05/23 22:10:41 :: ifconfig eth0
2016/05/23 22:10:43 :: ifconfig eth0
2016/05/23 22:10:45 :: ifconfig eth0
2016/05/23 22:10:47 :: ifconfig eth0
2016/05/23 22:10:49 :: ifconfig eth0
2016/05/23 22:10:51 :: ifconfig eth0
2016/05/23 22:10:53 :: ifconfig eth0
2016/05/23 22:10:56 :: ifconfig eth0
2016/05/23 22:10:58 :: ifconfig eth0
2016/05/23 22:11:00 :: ifconfig eth0
2016/05/23 22:11:02 :: ifconfig eth0
2016/05/23 22:11:04 :: ifconfig eth0
2016/05/23 22:11:06 :: ifconfig eth0
2016/05/23 22:11:08 :: ifconfig eth0
2016/05/23 22:11:10 :: ifconfig eth0
2016/05/23 22:11:13 :: ifconfig eth0
2016/05/23 22:11:15 :: ifconfig eth0
2016/05/23 22:11:17 :: ifconfig eth0
2016/05/23 22:11:19 :: ifconfig eth0
2016/05/23 22:11:21 :: ifconfig eth0
2016/05/23 22:11:23 :: ifconfig eth0
2016/05/23 22:11:25 :: ifconfig eth0
2016/05/23 22:11:27 :: ifconfig eth0
2016/05/23 22:11:30 :: ifconfig eth0
2016/05/23 22:11:32 :: ifconfig eth0
2016/05/23 22:11:34 :: ifconfig eth0
2016/05/23 22:11:36 :: ifconfig eth0
2016/05/23 22:11:38 :: ifconfig eth0
2016/05/23 22:11:40 :: ifconfig eth0
2016/05/23 22:11:43 :: ifconfig eth0
2016/05/23 22:11:45 :: ifconfig eth0
2016/05/23 22:11:47 :: ifconfig eth0
2016/05/23 22:11:49 :: ifconfig eth0
2016/05/23 22:11:51 :: ifconfig eth0
2016/05/23 22:11:53 :: ifconfig eth0
2016/05/23 22:11:55 :: ifconfig eth0
2016/05/23 22:11:58 :: ifconfig eth0
2016/05/23 22:12:00 :: ifconfig eth0
2016/05/23 22:12:02 :: ifconfig eth0
2016/05/23 22:12:04 :: ifconfig eth0
2016/05/23 22:12:07 :: ifconfig eth0
2016/05/23 22:12:09 :: ifconfig eth0
2016/05/23 22:12:11 :: ifconfig eth0
2016/05/23 22:12:13 :: ifconfig eth0
2016/05/23 22:12:16 :: ifconfig eth0
2016/05/23 22:12:18 :: ifconfig eth0
2016/05/23 22:12:20 :: ifconfig eth0
2016/05/23 22:12:23 :: ifconfig eth0
2016/05/23 22:12:25 :: ifconfig eth0
2016/05/23 22:12:27 :: ifconfig eth0
2016/05/23 22:12:29 :: ifconfig eth0
2016/05/23 22:12:31 :: ifconfig eth0
2016/05/23 22:12:33 :: ifconfig eth0
2016/05/23 22:12:35 :: ifconfig eth0
2016/05/23 22:12:37 :: ifconfig eth0
2016/05/23 22:12:39 :: ifconfig eth0
2016/05/23 22:12:41 :: ifconfig eth0
2016/05/23 22:12:44 :: ifconfig eth0
2016/05/23 22:12:46 :: ifconfig eth0
2016/05/23 22:12:48 :: ifconfig eth0
2016/05/23 22:12:50 :: ifconfig eth0
2016/05/23 22:12:52 :: ifconfig eth0
2016/05/23 22:12:54 :: ifconfig eth0
2016/05/23 22:12:57 :: ifconfig eth0
2016/05/23 22:12:59 :: ifconfig eth0
2016/05/23 22:13:01 :: ifconfig eth0
2016/05/23 22:13:03 :: ifconfig eth0
2016/05/23 22:13:06 :: ifconfig eth0
2016/05/23 22:13:08 :: ifconfig eth0
2016/05/23 22:13:10 :: ifconfig eth0
2016/05/23 22:13:12 :: ifconfig eth0
2016/05/23 22:13:14 :: ifconfig eth0
2016/05/23 22:13:16 :: ifconfig eth0
2016/05/23 22:13:18 :: ifconfig eth0
2016/05/23 22:13:20 :: ifconfig eth0
2016/05/23 22:13:22 :: ifconfig eth0
2016/05/23 22:13:24 :: ifconfig eth0
2016/05/23 22:13:26 :: ifconfig eth0
2016/05/23 22:13:28 :: ifconfig eth0
2016/05/23 22:13:31 :: ifconfig eth0
2016/05/23 22:13:33 :: ifconfig eth0
2016/05/23 22:13:35 :: ifconfig eth0
2016/05/23 22:13:37 :: ifconfig eth0
2016/05/23 22:13:39 :: ifconfig eth0
2016/05/23 22:13:41 :: ifconfig eth0
2016/05/23 22:13:44 :: ifconfig eth0
2016/05/23 22:13:46 :: ifconfig eth0
2016/05/23 22:13:48 :: ifconfig eth0
2016/05/23 22:13:50 :: ifconfig eth0
2016/05/23 22:13:52 :: ifconfig eth0
2016/05/23 22:13:54 :: ifconfig eth0
2016/05/23 22:13:56 :: ifconfig eth0
2016/05/23 22:13:58 :: ifconfig eth0
2016/05/23 22:14:00 :: ifconfig eth0
2016/05/23 22:14:02 :: ifconfig eth0
2016/05/23 22:14:05 :: ifconfig eth0
2016/05/23 22:14:07 :: ifconfig eth0
2016/05/23 22:14:09 :: ifconfig eth0
2016/05/23 22:14:11 :: ifconfig eth0
2016/05/23 22:14:13 :: ifconfig eth0
2016/05/23 22:14:15 :: ifconfig eth0
2016/05/23 22:14:17 :: ifconfig eth0
2016/05/23 22:14:20 :: ifconfig eth0
2016/05/23 22:14:22 :: ifconfig eth0
2016/05/23 22:14:24 :: ifconfig eth0
2016/05/23 22:14:27 :: ifconfig eth0
2016/05/23 22:14:29 :: ifconfig eth0
2016/05/23 22:14:31 :: ifconfig eth0
2016/05/23 22:14:33 :: ifconfig eth0
2016/05/23 22:14:35 :: ifconfig eth0
2016/05/23 22:14:37 :: ifconfig eth0
2016/05/23 22:14:39 :: ifconfig eth0
2016/05/23 22:14:41 :: ifconfig eth0
2016/05/23 22:14:43 :: ifconfig eth0
2016/05/23 22:14:45 :: ifconfig eth0
2016/05/23 22:14:47 :: ifconfig eth0
2016/05/23 22:14:50 :: ifconfig eth0
2016/05/23 22:14:52 :: ifconfig eth0
2016/05/23 22:14:55 :: ifconfig eth0
2016/05/23 22:14:57 :: ifconfig eth0
2016/05/23 22:14:59 :: ifconfig eth0
2016/05/23 22:15:01 :: ifconfig eth0
2016/05/23 22:15:04 :: ifconfig eth0
2016/05/23 22:15:06 :: ifconfig eth0
2016/05/23 22:15:09 :: ifconfig eth0
2016/05/23 22:15:11 :: ifconfig eth0
2016/05/23 22:15:13 :: ifconfig eth0
2016/05/23 22:15:16 :: ifconfig eth0
2016/05/23 22:15:18 :: ifconfig eth0
2016/05/23 22:15:20 :: ifconfig eth0
2016/05/23 22:15:22 :: ifconfig eth0
2016/05/23 22:15:24 :: ifconfig eth0
2016/05/23 22:15:26 :: ifconfig eth0
2016/05/23 22:15:28 :: ifconfig eth0
2016/05/23 22:15:30 :: ifconfig eth0
2016/05/23 22:15:32 :: ifconfig eth0
2016/05/23 22:15:34 :: ifconfig eth0
2016/05/23 22:15:36 :: ifconfig eth0
2016/05/23 22:15:38 :: ifconfig eth0
2016/05/23 22:15:40 :: ifconfig eth0
2016/05/23 22:15:42 :: ifconfig eth0
2016/05/23 22:15:45 :: ifconfig eth0
2016/05/23 22:15:47 :: ifconfig eth0
2016/05/23 22:15:49 :: ifconfig eth0
2016/05/23 22:15:51 :: ifconfig eth0
2016/05/23 22:15:53 :: ifconfig eth0
2016/05/23 22:15:56 :: ifconfig eth0
2016/05/23 22:15:58 :: ifconfig eth0
2016/05/23 22:16:00 :: ifconfig eth0
2016/05/23 22:16:02 :: ifconfig eth0
2016/05/23 22:16:04 :: ifconfig eth0
2016/05/23 22:16:07 :: ifconfig eth0
2016/05/23 22:16:09 :: ifconfig eth0
2016/05/23 22:16:11 :: ifconfig eth0
2016/05/23 22:16:13 :: ifconfig eth0
2016/05/23 22:16:16 :: ifconfig eth0
2016/05/23 22:16:18 :: ifconfig eth0
2016/05/23 22:16:20 :: ifconfig eth0
2016/05/23 22:16:23 :: ifconfig eth0
2016/05/23 22:16:25 :: ifconfig eth0
2016/05/23 22:16:27 :: ifconfig eth0
2016/05/23 22:16:29 :: ifconfig eth0
2016/05/23 22:16:31 :: ifconfig eth0
2016/05/23 22:16:34 :: ifconfig eth0
2016/05/23 22:16:36 :: ifconfig eth0
2016/05/23 22:16:39 :: ifconfig eth0
2016/05/23 22:16:41 :: ifconfig eth0
2016/05/23 22:16:43 :: ifconfig eth0
2016/05/23 22:16:45 :: ifconfig eth0
2016/05/23 22:16:48 :: ifconfig eth0
2016/05/23 22:16:50 :: ifconfig eth0
2016/05/23 22:16:52 :: ifconfig eth0
2016/05/23 22:16:55 :: ifconfig eth0
2016/05/23 22:16:57 :: ifconfig eth0
2016/05/23 22:16:59 :: ifconfig eth0
2016/05/23 22:17:01 :: ifconfig eth0
2016/05/23 22:17:03 :: ifconfig eth0
2016/05/23 22:17:05 :: ifconfig eth0
2016/05/23 22:17:07 :: ifconfig eth0
2016/05/23 22:17:09 :: ifconfig eth0
2016/05/23 22:17:12 :: ifconfig eth0
2016/05/23 22:17:14 :: ifconfig eth0
2016/05/23 22:17:16 :: ifconfig eth0
2016/05/23 22:17:18 :: ifconfig eth0
2016/05/23 22:17:21 :: ifconfig eth0
2016/05/23 22:17:23 :: ifconfig eth0
2016/05/23 22:17:25 :: ifconfig eth0
2016/05/23 22:17:28 :: ifconfig eth0
2016/05/23 22:17:30 :: ifconfig eth0
2016/05/23 22:17:32 :: ifconfig eth0
2016/05/23 22:17:34 :: ifconfig eth0
2016/05/23 22:17:36 :: ifconfig eth0
2016/05/23 22:17:38 :: ifconfig eth0
2016/05/23 22:17:40 :: ifconfig eth0
2016/05/23 22:17:42 :: ifconfig eth0
2016/05/23 22:17:45 :: ifconfig eth0
2016/05/23 22:17:47 :: ifconfig eth0
2016/05/23 22:17:49 :: ifconfig eth0
2016/05/23 22:17:51 :: ifconfig eth0
2016/05/23 22:17:53 :: ifconfig eth0
2016/05/23 22:17:55 :: ifconfig eth0
2016/05/23 22:17:58 :: ifconfig eth0
2016/05/23 22:18:00 :: ifconfig eth0
2016/05/23 22:18:03 :: ifconfig eth0
2016/05/23 22:18:05 :: ifconfig eth0
2016/05/23 22:18:07 :: ifconfig eth0
2016/05/23 22:18:09 :: ifconfig eth0
2016/05/23 22:18:11 :: ifconfig eth0
2016/05/23 22:18:13 :: ifconfig eth0
2016/05/23 22:18:15 :: ifconfig eth0
2016/05/23 22:18:18 :: ifconfig eth0
2016/05/23 22:18:20 :: ifconfig eth0
2016/05/23 22:18:23 :: ifconfig eth0
2016/05/23 22:18:25 :: ifconfig eth0
2016/05/23 22:18:27 :: ifconfig eth0
2016/05/23 22:18:29 :: ifconfig eth0
2016/05/23 22:18:31 :: ifconfig eth0
2016/05/23 22:18:33 :: ifconfig eth0
2016/05/23 22:18:36 :: ifconfig eth0
2016/05/23 22:18:38 :: ifconfig eth0
2016/05/23 22:18:40 :: ifconfig eth0
2016/05/23 22:18:42 :: ifconfig eth0
2016/05/23 22:18:44 :: ifconfig eth0
2016/05/23 22:18:46 :: ifconfig eth0
2016/05/23 22:18:48 :: ifconfig eth0
2016/05/23 22:18:51 :: ifconfig eth0
2016/05/23 22:18:53 :: ifconfig eth0
2016/05/23 22:18:55 :: ifconfig eth0
2016/05/23 22:18:57 :: ifconfig eth0
2016/05/23 22:19:00 :: ifconfig eth0
2016/05/23 22:19:02 :: ifconfig eth0
2016/05/23 22:19:04 :: ifconfig eth0
2016/05/23 22:19:06 :: ifconfig eth0
2016/05/23 22:19:08 :: ifconfig eth0
2016/05/23 22:19:11 :: ifconfig eth0
2016/05/23 22:19:13 :: ifconfig eth0
2016/05/23 22:19:15 :: ifconfig eth0
2016/05/23 22:19:17 :: ifconfig eth0
2016/05/23 22:19:19 :: ifconfig eth0
2016/05/23 22:19:22 :: ifconfig eth0
2016/05/23 22:19:24 :: ifconfig eth0
2016/05/23 22:19:26 :: ifconfig eth0
2016/05/23 22:19:29 :: ifconfig eth0
2016/05/23 22:19:31 :: ifconfig eth0
2016/05/23 22:19:33 :: ifconfig eth0
2016/05/23 22:19:35 :: ifconfig eth0
2016/05/23 22:19:38 :: ifconfig eth0
2016/05/23 22:19:40 :: ifconfig eth0
2016/05/23 22:19:42 :: ifconfig eth0
2016/05/23 22:19:44 :: ifconfig eth0
2016/05/23 22:19:46 :: ifconfig eth0
2016/05/23 22:19:49 :: ifconfig eth0
2016/05/23 22:19:51 :: ifconfig eth0
2016/05/23 22:19:53 :: ifconfig eth0
2016/05/23 22:19:55 :: ifconfig eth0
2016/05/23 22:19:57 :: ifconfig eth0
2016/05/23 22:19:59 :: ifconfig eth0
2016/05/23 22:20:01 :: ifconfig eth0
2016/05/23 22:20:04 :: ifconfig eth0
2016/05/23 22:20:06 :: ifconfig eth0
2016/05/23 22:20:08 :: ifconfig eth0
2016/05/23 22:20:10 :: ifconfig eth0
2016/05/23 22:20:12 :: ifconfig eth0
2016/05/23 22:20:14 :: ifconfig eth0
2016/05/23 22:20:16 :: ifconfig eth0
2016/05/23 22:20:18 :: ifconfig eth0
2016/05/23 22:20:20 :: ifconfig eth0
2016/05/23 22:20:23 :: ifconfig eth0
2016/05/23 22:20:25 :: ifconfig eth0
2016/05/23 22:20:27 :: ifconfig eth0
2016/05/23 22:20:29 :: ifconfig eth0
2016/05/23 22:20:31 :: ifconfig eth0
2016/05/23 22:20:34 :: ifconfig eth0
2016/05/23 22:20:36 :: ifconfig eth0
2016/05/23 22:20:38 :: ifconfig eth0
2016/05/23 22:20:40 :: ifconfig eth0
2016/05/23 22:20:42 :: ifconfig eth0
2016/05/23 22:20:44 :: ifconfig eth0
2016/05/23 22:20:46 :: ifconfig eth0
2016/05/23 22:20:48 :: ifconfig eth0
2016/05/23 22:20:51 :: ifconfig eth0
2016/05/23 22:20:53 :: ifconfig eth0
2016/05/23 22:20:55 :: ifconfig eth0
2016/05/23 22:20:57 :: ifconfig eth0
2016/05/23 22:21:00 :: ifconfig eth0
2016/05/23 22:21:02 :: ifconfig eth0
2016/05/23 22:21:04 :: ifconfig eth0
2016/05/23 22:21:06 :: ifconfig eth0
2016/05/23 22:21:09 :: ifconfig eth0
2016/05/23 22:21:11 :: ifconfig eth0
2016/05/23 22:21:13 :: ifconfig eth0
2016/05/23 22:21:16 :: ifconfig eth0
2016/05/23 22:21:18 :: ifconfig eth0
2016/05/23 22:21:21 :: ifconfig eth0
2016/05/23 22:21:23 :: ifconfig eth0
2016/05/23 22:21:25 :: ifconfig eth0
2016/05/23 22:21:27 :: ifconfig eth0
2016/05/23 22:21:30 :: ifconfig eth0
2016/05/23 22:21:32 :: ifconfig eth0
2016/05/23 22:21:35 :: ifconfig eth0
2016/05/23 22:21:37 :: ifconfig eth0
2016/05/23 22:21:39 :: ifconfig eth0
2016/05/23 22:21:41 :: ifconfig eth0
2016/05/23 22:21:43 :: ifconfig eth0
2016/05/23 22:21:46 :: ifconfig eth0
2016/05/23 22:21:48 :: ifconfig eth0
2016/05/23 22:21:50 :: ifconfig eth0
2016/05/23 22:21:52 :: ifconfig eth0
2016/05/23 22:21:54 :: ifconfig eth0
2016/05/23 22:21:56 :: ifconfig eth0
2016/05/23 22:21:59 :: ifconfig eth0
2016/05/23 22:22:01 :: ifconfig eth0
2016/05/23 22:22:03 :: ifconfig eth0
2016/05/23 22:22:05 :: ifconfig eth0
2016/05/23 22:22:07 :: ifconfig eth0
2016/05/23 22:22:09 :: ifconfig eth0
2016/05/23 22:22:11 :: ifconfig eth0
2016/05/23 22:22:14 :: ifconfig eth0
2016/05/23 22:22:16 :: ifconfig eth0
2016/05/23 22:22:18 :: ifconfig eth0
2016/05/23 22:22:21 :: ifconfig eth0
2016/05/23 22:22:23 :: ifconfig eth0
2016/05/23 22:22:25 :: ifconfig eth0
2016/05/23 22:22:27 :: ifconfig eth0
2016/05/23 22:22:30 :: ifconfig eth0
2016/05/23 22:22:32 :: ifconfig eth0
2016/05/23 22:22:34 :: ifconfig eth0
2016/05/23 22:22:36 :: ifconfig eth0
2016/05/23 22:22:38 :: ifconfig eth0
2016/05/23 22:22:41 :: ifconfig eth0
2016/05/23 22:22:43 :: ifconfig eth0
2016/05/23 22:22:45 :: ifconfig eth0
2016/05/23 22:22:47 :: ifconfig eth0
2016/05/23 22:22:49 :: ifconfig eth0
2016/05/23 22:22:51 :: ifconfig eth0
2016/05/23 22:22:54 :: ifconfig eth0
2016/05/23 22:22:56 :: ifconfig eth0
2016/05/23 22:22:58 :: ifconfig eth0
2016/05/23 22:23:01 :: ifconfig eth0
2016/05/23 22:23:03 :: ifconfig eth0
2016/05/23 22:23:05 :: ifconfig eth0
2016/05/23 22:23:07 :: ifconfig eth0
2016/05/23 22:23:10 :: ifconfig eth0
2016/05/23 22:23:12 :: ifconfig eth0
2016/05/23 22:23:14 :: ifconfig eth0
2016/05/23 22:23:16 :: ifconfig eth0
2016/05/23 22:23:19 :: ifconfig eth0
2016/05/23 22:23:21 :: ifconfig eth0
2016/05/23 22:23:23 :: ifconfig eth0
2016/05/23 22:23:25 :: ifconfig eth0
2016/05/23 22:23:27 :: ifconfig eth0
2016/05/23 22:23:29 :: ifconfig eth0
2016/05/23 22:23:32 :: ifconfig eth0
2016/05/23 22:23:34 :: ifconfig eth0
2016/05/23 22:23:36 :: ifconfig eth0
2016/05/23 22:23:39 :: ifconfig eth0
2016/05/23 22:23:41 :: ifconfig eth0
2016/05/23 22:23:43 :: ifconfig eth0
2016/05/23 22:23:46 :: ifconfig eth0
2016/05/23 22:23:48 :: ifconfig eth0
2016/05/23 22:23:50 :: ifconfig eth0
2016/05/23 22:23:52 :: ifconfig eth0
2016/05/23 22:23:54 :: ifconfig eth0
2016/05/23 22:23:57 :: ifconfig eth0
2016/05/23 22:23:59 :: ifconfig eth0
2016/05/23 22:24:01 :: ifconfig eth0
2016/05/23 22:24:03 :: ifconfig eth0
2016/05/23 22:24:05 :: ifconfig eth0
2016/05/23 22:24:07 :: ifconfig eth0
2016/05/23 22:24:09 :: ifconfig eth0
2016/05/23 22:24:12 :: ifconfig eth0
2016/05/23 22:24:14 :: ifconfig eth0
2016/05/23 22:24:16 :: ifconfig eth0
2016/05/23 22:24:18 :: ifconfig eth0
2016/05/23 22:24:20 :: ifconfig eth0
2016/05/23 22:24:22 :: ifconfig eth0
2016/05/23 22:24:24 :: ifconfig eth0
2016/05/23 22:24:27 :: ifconfig eth0
2016/05/23 22:24:29 :: ifconfig eth0
2016/05/23 22:24:31 :: ifconfig eth0
2016/05/23 22:24:33 :: ifconfig eth0
2016/05/23 22:24:35 :: ifconfig eth0
2016/05/23 22:24:37 :: ifconfig eth0
2016/05/23 22:24:39 :: ifconfig eth0
2016/05/23 22:24:42 :: ifconfig eth0
2016/05/23 22:24:44 :: ifconfig eth0
2016/05/23 22:24:46 :: ifconfig eth0
2016/05/23 22:24:48 :: ifconfig eth0
2016/05/23 22:24:50 :: ifconfig eth0
2016/05/23 22:24:52 :: ifconfig eth0
2016/05/23 22:24:54 :: ifconfig eth0
2016/05/23 22:24:56 :: ifconfig eth0
2016/05/23 22:24:58 :: ifconfig eth0
2016/05/23 22:25:00 :: ifconfig eth0
2016/05/23 22:25:02 :: ifconfig eth0
2016/05/23 22:25:04 :: ifconfig eth0
2016/05/23 22:25:07 :: ifconfig eth0
2016/05/23 22:25:09 :: ifconfig eth0
2016/05/23 22:25:11 :: ifconfig eth0
2016/05/23 22:25:14 :: ifconfig eth0
2016/05/23 22:25:16 :: ifconfig eth0
2016/05/23 22:25:19 :: ifconfig eth0
2016/05/23 22:25:21 :: ifconfig eth0
2016/05/23 22:25:23 :: ifconfig eth0
2016/05/23 22:25:25 :: ifconfig eth0
2016/05/23 22:25:27 :: ifconfig eth0
2016/05/23 22:25:29 :: ifconfig eth0
2016/05/23 22:25:32 :: ifconfig eth0
2016/05/23 22:25:34 :: ifconfig eth0
2016/05/23 22:25:36 :: ifconfig eth0
2016/05/23 22:25:38 :: ifconfig eth0
2016/05/23 22:25:40 :: ifconfig eth0
2016/05/23 22:25:42 :: ifconfig eth0
2016/05/23 22:25:45 :: ifconfig eth0
2016/05/23 22:25:47 :: ifconfig eth0
2016/05/23 22:25:49 :: ifconfig eth0
2016/05/23 22:25:51 :: ifconfig eth0
2016/05/23 22:25:53 :: ifconfig eth0
2016/05/23 22:25:56 :: ifconfig eth0
2016/05/23 22:25:58 :: ifconfig eth0
2016/05/23 22:26:00 :: ifconfig eth0
2016/05/23 22:26:02 :: ifconfig eth0
2016/05/23 22:26:04 :: ifconfig eth0
2016/05/23 22:26:07 :: ifconfig eth0
2016/05/23 22:26:09 :: ifconfig eth0
2016/05/23 22:26:11 :: ifconfig eth0
2016/05/23 22:26:13 :: ifconfig eth0
2016/05/23 22:26:15 :: ifconfig eth0
2016/05/23 22:26:17 :: ifconfig eth0
2016/05/23 22:26:19 :: ifconfig eth0
2016/05/23 22:26:22 :: ifconfig eth0
2016/05/23 22:26:24 :: ifconfig eth0
2016/05/23 22:26:26 :: ifconfig eth0
2016/05/23 22:26:28 :: ifconfig eth0
2016/05/23 22:26:30 :: ifconfig eth0
2016/05/23 22:26:32 :: ifconfig eth0
2016/05/23 22:26:34 :: ifconfig eth0
2016/05/23 22:26:37 :: ifconfig eth0
2016/05/23 22:26:39 :: ifconfig eth0
2016/05/23 22:26:39 :: found default in configuration 1
2016/05/23 22:26:39 :: Reading wired profile wired-default
2016/05/23 22:26:39 :: found afterscript in configuration None
2016/05/23 22:26:39 :: found dhcphostname in configuration noahlub
2016/05/23 22:26:39 :: found postdisconnectscript in configuration None
2016/05/23 22:26:39 :: found dns_domain in configuration None
2016/05/23 22:26:39 :: found gateway in configuration None
2016/05/23 22:26:39 :: found use_global_dns in configuration False
2016/05/23 22:26:39 :: found lastused in configuration True
2016/05/23 22:26:39 :: found ip in configuration None
2016/05/23 22:26:39 :: found beforescript in configuration None
2016/05/23 22:26:39 :: found encryption_enabled in configuration False
2016/05/23 22:26:39 :: found broadcast in configuration None
2016/05/23 22:26:39 :: found netmask in configuration None
2016/05/23 22:26:39 :: found usedhcphostname in configuration 1
2016/05/23 22:26:39 :: found predisconnectscript in configuration None
2016/05/23 22:26:39 :: found enctype in configuration None
2016/05/23 22:26:39 :: found default in configuration 1
2016/05/23 22:26:39 :: found dns2 in configuration 8.8.4.4
2016/05/23 22:26:39 :: found search_domain in configuration None
2016/05/23 22:26:39 :: found use_static_dns in configuration True
2016/05/23 22:26:39 :: found dns3 in configuration None
2016/05/23 22:26:39 :: found profilename in configuration wired-default
2016/05/23 22:26:39 :: found dns1 in configuration 8.8.8.8
2016/05/23 22:26:39 :: found default in configuration 1
2016/05/23 22:26:39 :: saving wired profile wired-default
2016/05/23 22:26:40 :: scanning start
2016/05/23 22:26:40 :: scanning done
2016/05/23 22:26:40 :: found 0 networks:
2016/05/23 22:26:41 :: ifconfig eth0
2016/05/23 22:26:41 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:26:41 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:26:41 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:26:41 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:26:41 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:26:41 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:26:41 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:26:41 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:26:41 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:26:41 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:26:41 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:26:41 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:26:41 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:26:42 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:26:42 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:26:42 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:26:42 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:26:42 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:26:42 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:26:42 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:26:42 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:26:42 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:26:42 :: attempting to set hostname with dhclient
2016/05/23 22:26:42 :: using dhcpcd or another supported client may work better
2016/05/23 22:26:42 :: /sbin/dhclient -v -r eth0
2016/05/23 22:26:42 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:26:42 :: /sbin/ip route flush dev eth0
2016/05/23 22:26:42 :: ifconfig eth0 down
2016/05/23 22:26:42 :: ifconfig eth0 up
2016/05/23 22:26:42 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:26:42 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:26:42 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:26:42 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:26:42 :: wpa_cli -i eth0 terminate
2016/05/23 22:26:42 :: found lastused in configuration True
2016/05/23 22:26:42 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 22:26:42 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 22:26:42 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 22:26:42 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 22:26:42 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 22:26:42 :: Putting interface down
2016/05/23 22:26:42 :: ifconfig eth0 down
2016/05/23 22:26:42 :: Releasing DHCP leases...
2016/05/23 22:26:42 :: attempting to set hostname with dhclient
2016/05/23 22:26:42 :: using dhcpcd or another supported client may work better
2016/05/23 22:26:42 :: /sbin/dhclient -v -r eth0
2016/05/23 22:26:42 :: Setting false IP...
2016/05/23 22:26:42 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:26:43 :: Stopping wpa_supplicant
2016/05/23 22:26:43 :: wpa_cli -i eth0 terminate
2016/05/23 22:26:43 :: Flushing the routing table...
2016/05/23 22:26:43 :: /sbin/ip route flush dev eth0
2016/05/23 22:26:43 :: Putting interface up...
2016/05/23 22:26:43 :: ifconfig eth0 up
2016/05/23 22:26:44 :: trying to load backend ioctl
2016/05/23 22:26:44 :: WARNING: python-iwscan not found, falling back to using iwlist scan.
2016/05/23 22:26:44 :: WARNING: python-wpactrl not found, falling back to using wpa_cli.
2016/05/23 22:26:44 :: trying to load backend external
2016/05/23 22:26:44 :: found backend in configuration external
2016/05/23 22:26:45 :: Running DHCP with hostname noahlub
2016/05/23 22:26:45 :: attempting to set hostname with dhclient
2016/05/23 22:26:45 :: using dhcpcd or another supported client may work better
2016/05/23 22:26:45 :: /sbin/dhclient -v eth0
2016/05/23 22:26:45 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 22:26:45 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 22:26:45 :: All rights reserved.
2016/05/23 22:26:45 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 22:26:45 :: 
2016/05/23 22:26:45 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:26:45 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:26:45 :: Sending on   Socket/fallback
2016/05/23 22:26:45 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x82d0b933)
2016/05/23 22:26:48 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x82d0b933)
2016/05/23 22:26:51 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x82d0b933)
2016/05/23 22:26:52 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x33b9d082)
2016/05/23 22:26:52 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 22:26:52 :: setting use global dns to 0
2016/05/23 22:26:52 :: setting global dns
2016/05/23 22:26:52 :: global dns servers are   
2016/05/23 22:26:52 :: domain is 
2016/05/23 22:26:52 :: search domain is 
2016/05/23 22:26:52 :: setting wireless interface 
2016/05/23 22:26:52 :: setting wired interface eth0
2016/05/23 22:26:52 :: setting wpa driver wext
2016/05/23 22:26:52 :: setting automatically reconnect when connection drops 1
2016/05/23 22:26:52 :: setting backend to external
2016/05/23 22:26:52 :: Setting dhcp client to 0
2016/05/23 22:26:52 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 22:26:52 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 22:26:52 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 22:26:52 :: bound to 162.228.104.207 -- renewal in 265 seconds.
2016/05/23 22:26:52 :: DHCP connection successful
2016/05/23 22:26:52 :: Setting DNS : 8.8.8.8
2016/05/23 22:26:52 :: Setting DNS : 8.8.4.4
2016/05/23 22:26:52 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 22:26:52 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 22:26:52 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 22:26:52 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 22:26:52 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 22:26:52 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 22:26:56 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 22:26:56 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 22:26:57 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 22:26:57 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 22:26:57 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 22:26:57 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 22:26:57 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 22:26:57 :: Connecting thread exiting.
2016/05/23 22:26:57 :: ifconfig eth0
2016/05/23 22:26:57 :: IP Address is: 162.228.104.207
2016/05/23 22:26:57 :: Sending connection attempt result success
2016/05/23 22:26:59 :: ifconfig eth0
2016/05/23 22:27:01 :: ifconfig eth0
2016/05/23 22:27:03 :: ifconfig eth0
2016/05/23 22:27:05 :: ifconfig eth0
2016/05/23 22:27:07 :: ifconfig eth0
2016/05/23 22:27:09 :: ifconfig eth0
2016/05/23 22:27:11 :: ifconfig eth0
2016/05/23 22:27:13 :: ifconfig eth0
2016/05/23 22:27:15 :: ifconfig eth0
2016/05/23 22:27:17 :: ifconfig eth0
2016/05/23 22:27:19 :: ifconfig eth0
2016/05/23 22:27:21 :: ifconfig eth0
2016/05/23 22:27:23 :: ifconfig eth0
2016/05/23 22:27:25 :: ifconfig eth0
2016/05/23 22:27:27 :: ifconfig eth0
2016/05/23 22:27:29 :: ifconfig eth0
2016/05/23 22:27:31 :: ifconfig eth0
2016/05/23 22:27:33 :: ifconfig eth0
2016/05/23 22:27:35 :: ifconfig eth0
2016/05/23 22:27:38 :: ifconfig eth0
2016/05/23 22:27:40 :: ifconfig eth0
2016/05/23 22:27:42 :: ifconfig eth0
2016/05/23 22:27:44 :: ifconfig eth0
2016/05/23 22:27:46 :: ifconfig eth0
2016/05/23 22:27:48 :: ifconfig eth0
2016/05/23 22:27:50 :: ifconfig eth0
2016/05/23 22:27:52 :: ifconfig eth0
2016/05/23 22:27:54 :: ifconfig eth0
2016/05/23 22:27:56 :: ifconfig eth0
2016/05/23 22:27:58 :: ifconfig eth0
2016/05/23 22:28:00 :: ifconfig eth0
2016/05/23 22:28:02 :: ifconfig eth0
2016/05/23 22:28:04 :: ifconfig eth0
2016/05/23 22:28:06 :: ifconfig eth0
2016/05/23 22:28:08 :: ifconfig eth0
2016/05/23 22:28:10 :: ifconfig eth0
2016/05/23 22:28:12 :: ifconfig eth0
2016/05/23 22:28:14 :: ifconfig eth0
2016/05/23 22:28:16 :: ifconfig eth0
2016/05/23 22:28:18 :: ifconfig eth0
2016/05/23 22:28:20 :: ifconfig eth0
2016/05/23 22:28:22 :: ifconfig eth0
2016/05/23 22:28:24 :: ifconfig eth0
2016/05/23 22:28:26 :: ifconfig eth0
2016/05/23 22:28:28 :: ifconfig eth0
2016/05/23 22:28:30 :: ifconfig eth0
2016/05/23 22:28:33 :: ifconfig eth0
2016/05/23 22:28:35 :: ifconfig eth0
2016/05/23 22:28:37 :: ifconfig eth0
2016/05/23 22:28:39 :: ifconfig eth0
2016/05/23 22:28:41 :: ifconfig eth0
2016/05/23 22:28:43 :: ifconfig eth0
2016/05/23 22:28:45 :: ifconfig eth0
2016/05/23 22:28:47 :: ifconfig eth0
2016/05/23 22:28:49 :: ifconfig eth0
2016/05/23 22:28:51 :: ifconfig eth0
2016/05/23 22:28:53 :: ifconfig eth0
2016/05/23 22:28:55 :: ifconfig eth0
2016/05/23 22:28:58 :: ifconfig eth0
2016/05/23 22:29:00 :: ifconfig eth0
2016/05/23 22:29:02 :: ifconfig eth0
2016/05/23 22:29:04 :: ifconfig eth0
2016/05/23 22:29:06 :: ifconfig eth0
2016/05/23 22:29:08 :: ifconfig eth0
2016/05/23 22:29:10 :: ifconfig eth0
2016/05/23 22:29:12 :: ifconfig eth0
2016/05/23 22:29:14 :: ifconfig eth0
2016/05/23 22:29:16 :: ifconfig eth0
2016/05/23 22:29:18 :: ifconfig eth0
2016/05/23 22:29:20 :: ifconfig eth0
2016/05/23 22:29:22 :: ifconfig eth0
2016/05/23 22:29:24 :: ifconfig eth0
2016/05/23 22:29:26 :: ifconfig eth0
2016/05/23 22:29:28 :: ifconfig eth0
2016/05/23 22:29:30 :: ifconfig eth0
2016/05/23 22:29:32 :: ifconfig eth0
2016/05/23 22:29:34 :: ifconfig eth0
2016/05/23 22:29:36 :: ifconfig eth0
2016/05/23 22:29:38 :: ifconfig eth0
2016/05/23 22:29:40 :: ifconfig eth0
2016/05/23 22:29:42 :: ifconfig eth0
2016/05/23 22:29:44 :: ifconfig eth0
2016/05/23 22:29:47 :: ifconfig eth0
2016/05/23 22:29:49 :: ifconfig eth0
2016/05/23 22:29:51 :: ifconfig eth0
2016/05/23 22:29:53 :: ifconfig eth0
2016/05/23 22:29:55 :: ifconfig eth0
2016/05/23 22:29:57 :: ifconfig eth0
2016/05/23 22:29:59 :: ifconfig eth0
2016/05/23 22:30:01 :: ifconfig eth0
2016/05/23 22:30:03 :: ifconfig eth0
2016/05/23 22:30:05 :: ifconfig eth0
2016/05/23 22:30:07 :: ifconfig eth0
2016/05/23 22:30:09 :: ifconfig eth0
2016/05/23 22:30:11 :: ifconfig eth0
2016/05/23 22:30:13 :: ifconfig eth0
2016/05/23 22:30:15 :: ifconfig eth0
2016/05/23 22:30:17 :: ifconfig eth0
2016/05/23 22:30:19 :: ifconfig eth0
2016/05/23 22:30:21 :: ifconfig eth0
2016/05/23 22:30:23 :: ifconfig eth0
2016/05/23 22:30:25 :: ifconfig eth0
2016/05/23 22:30:27 :: ifconfig eth0
2016/05/23 22:30:30 :: ifconfig eth0
2016/05/23 22:30:32 :: ifconfig eth0
2016/05/23 22:30:34 :: ifconfig eth0
2016/05/23 22:30:37 :: ifconfig eth0
2016/05/23 22:30:39 :: ifconfig eth0
2016/05/23 22:30:41 :: ifconfig eth0
2016/05/23 22:30:43 :: ifconfig eth0
2016/05/23 22:30:45 :: ifconfig eth0
2016/05/23 22:30:47 :: ifconfig eth0
2016/05/23 22:30:49 :: ifconfig eth0
2016/05/23 22:30:51 :: ifconfig eth0
2016/05/23 22:30:53 :: ifconfig eth0
2016/05/23 22:30:55 :: ifconfig eth0
2016/05/23 22:30:57 :: ifconfig eth0
2016/05/23 22:30:59 :: ifconfig eth0
2016/05/23 22:31:01 :: ifconfig eth0
2016/05/23 22:31:03 :: ifconfig eth0
2016/05/23 22:31:05 :: ifconfig eth0
2016/05/23 22:31:07 :: ifconfig eth0
2016/05/23 22:31:09 :: ifconfig eth0
2016/05/23 22:31:11 :: ifconfig eth0
2016/05/23 22:31:13 :: ifconfig eth0
2016/05/23 22:31:15 :: ifconfig eth0
2016/05/23 22:31:17 :: ifconfig eth0
2016/05/23 22:31:19 :: ifconfig eth0
2016/05/23 22:31:21 :: ifconfig eth0
2016/05/23 22:31:23 :: ifconfig eth0
2016/05/23 22:31:25 :: ifconfig eth0
2016/05/23 22:31:28 :: ifconfig eth0
2016/05/23 22:31:30 :: ifconfig eth0
2016/05/23 22:31:32 :: ifconfig eth0
2016/05/23 22:31:34 :: ifconfig eth0
2016/05/23 22:31:36 :: ifconfig eth0
2016/05/23 22:31:38 :: ifconfig eth0
2016/05/23 22:31:40 :: ifconfig eth0
2016/05/23 22:31:42 :: ifconfig eth0
2016/05/23 22:31:44 :: ifconfig eth0
2016/05/23 22:31:46 :: ifconfig eth0
2016/05/23 22:31:48 :: ifconfig eth0
2016/05/23 22:31:50 :: ifconfig eth0
2016/05/23 22:31:52 :: ifconfig eth0
2016/05/23 22:31:54 :: ifconfig eth0
2016/05/23 22:31:56 :: ifconfig eth0
2016/05/23 22:31:58 :: ifconfig eth0
2016/05/23 22:32:00 :: ifconfig eth0
2016/05/23 22:32:02 :: ifconfig eth0
2016/05/23 22:32:04 :: ifconfig eth0
2016/05/23 22:32:06 :: ifconfig eth0
2016/05/23 22:32:08 :: ifconfig eth0
2016/05/23 22:32:10 :: ifconfig eth0
2016/05/23 22:32:13 :: ifconfig eth0
2016/05/23 22:32:15 :: ifconfig eth0
2016/05/23 22:32:17 :: ifconfig eth0
2016/05/23 22:32:19 :: ifconfig eth0
2016/05/23 22:32:21 :: ifconfig eth0
2016/05/23 22:32:23 :: ifconfig eth0
2016/05/23 22:32:26 :: ifconfig eth0
2016/05/23 22:32:28 :: ifconfig eth0
2016/05/23 22:32:29 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:32:29 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:32:29 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:32:29 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:32:29 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:32:29 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:32:29 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:32:29 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:32:29 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:32:29 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:32:29 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:32:29 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:32:29 :: attempting to set hostname with dhclient
2016/05/23 22:32:29 :: using dhcpcd or another supported client may work better
2016/05/23 22:32:29 :: /sbin/dhclient -v -r eth0
2016/05/23 22:32:30 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:32:30 :: /sbin/ip route flush dev eth0
2016/05/23 22:32:30 :: ifconfig eth0 down
2016/05/23 22:32:30 :: ifconfig eth0 up
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:32:31 :: wpa_cli -i eth0 terminate
2016/05/23 22:32:31 :: Forced disconnect on
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:32:31 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:32:31 :: attempting to set hostname with dhclient
2016/05/23 22:32:31 :: using dhcpcd or another supported client may work better
2016/05/23 22:32:31 :: /sbin/dhclient -v -r eth0
2016/05/23 22:32:31 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:32:31 :: /sbin/ip route flush dev eth0
2016/05/23 22:32:31 :: ifconfig eth0 down
2016/05/23 22:32:31 :: ifconfig eth0 up
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:32:31 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:32:31 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:32:31 :: wpa_cli -i eth0 terminate
2016/05/23 22:32:31 :: ifconfig eth0
2016/05/23 22:32:34 :: ifconfig eth0
2016/05/23 22:32:36 :: ifconfig eth0
2016/05/23 22:32:38 :: ifconfig eth0
2016/05/23 22:32:40 :: ifconfig eth0
2016/05/23 22:32:43 :: ifconfig eth0
2016/05/23 22:32:45 :: ifconfig eth0
2016/05/23 22:32:47 :: ifconfig eth0
2016/05/23 22:32:49 :: ifconfig eth0
2016/05/23 22:32:51 :: ifconfig eth0
2016/05/23 22:32:53 :: ifconfig eth0
2016/05/23 22:32:55 :: ifconfig eth0
2016/05/23 22:32:57 :: ifconfig eth0
2016/05/23 22:32:59 :: ifconfig eth0
2016/05/23 22:33:01 :: ifconfig eth0
2016/05/23 22:33:04 :: ifconfig eth0
2016/05/23 22:33:06 :: ifconfig eth0
2016/05/23 22:33:08 :: ifconfig eth0
2016/05/23 22:33:10 :: ifconfig eth0
2016/05/23 22:33:13 :: ifconfig eth0
2016/05/23 22:33:15 :: ifconfig eth0
2016/05/23 22:33:17 :: ifconfig eth0
2016/05/23 22:33:19 :: ifconfig eth0
2016/05/23 22:33:21 :: ifconfig eth0
2016/05/23 22:33:23 :: ifconfig eth0
2016/05/23 22:33:25 :: ifconfig eth0
2016/05/23 22:33:27 :: ifconfig eth0
2016/05/23 22:33:30 :: ifconfig eth0
2016/05/23 22:33:32 :: ifconfig eth0
2016/05/23 22:33:34 :: ifconfig eth0
2016/05/23 22:33:36 :: ifconfig eth0
2016/05/23 22:33:38 :: ifconfig eth0
2016/05/23 22:33:41 :: ifconfig eth0
2016/05/23 22:33:43 :: ifconfig eth0
2016/05/23 22:33:45 :: ifconfig eth0
2016/05/23 22:33:47 :: ifconfig eth0
2016/05/23 22:33:49 :: ifconfig eth0
2016/05/23 22:33:52 :: ifconfig eth0
2016/05/23 22:33:54 :: ifconfig eth0
2016/05/23 22:33:56 :: ifconfig eth0
2016/05/23 22:33:58 :: ifconfig eth0
2016/05/23 22:34:00 :: ifconfig eth0
2016/05/23 22:34:02 :: ifconfig eth0
2016/05/23 22:34:04 :: ifconfig eth0
2016/05/23 22:34:07 :: ifconfig eth0
2016/05/23 22:34:09 :: ifconfig eth0
2016/05/23 22:34:11 :: ifconfig eth0
2016/05/23 22:34:14 :: ifconfig eth0
2016/05/23 22:34:16 :: ifconfig eth0
2016/05/23 22:34:18 :: ifconfig eth0
2016/05/23 22:34:21 :: ifconfig eth0
2016/05/23 22:34:23 :: ifconfig eth0
2016/05/23 22:34:25 :: ifconfig eth0
2016/05/23 22:34:27 :: ifconfig eth0
2016/05/23 22:34:30 :: ifconfig eth0
2016/05/23 22:34:32 :: ifconfig eth0
2016/05/23 22:34:34 :: ifconfig eth0
2016/05/23 22:34:37 :: ifconfig eth0
2016/05/23 22:34:39 :: ifconfig eth0
2016/05/23 22:34:41 :: ifconfig eth0
2016/05/23 22:34:43 :: ifconfig eth0
2016/05/23 22:34:45 :: ifconfig eth0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:34:46 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:34:46 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:34:46 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:34:46 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:34:46 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:34:46 :: attempting to set hostname with dhclient
2016/05/23 22:34:46 :: using dhcpcd or another supported client may work better
2016/05/23 22:34:46 :: /sbin/dhclient -v -r eth0
2016/05/23 22:34:47 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:34:47 :: /sbin/ip route flush dev eth0
2016/05/23 22:34:47 :: ifconfig eth0 down
2016/05/23 22:34:47 :: ifconfig eth0 up
2016/05/23 22:34:47 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:34:47 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:34:47 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:34:47 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:34:47 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:34:47 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:34:47 :: wpa_cli -i eth0 terminate
2016/05/23 22:34:47 :: found lastused in configuration True
2016/05/23 22:34:47 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 22:34:47 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 22:34:47 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 22:34:47 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 22:34:47 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 22:34:47 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 22:34:47 :: Putting interface down
2016/05/23 22:34:47 :: ifconfig eth0 down
2016/05/23 22:34:47 :: Releasing DHCP leases...
2016/05/23 22:34:47 :: attempting to set hostname with dhclient
2016/05/23 22:34:47 :: using dhcpcd or another supported client may work better
2016/05/23 22:34:47 :: /sbin/dhclient -v -r eth0
2016/05/23 22:34:47 :: Setting false IP...
2016/05/23 22:34:47 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:34:48 :: Stopping wpa_supplicant
2016/05/23 22:34:48 :: wpa_cli -i eth0 terminate
2016/05/23 22:34:48 :: Flushing the routing table...
2016/05/23 22:34:48 :: /sbin/ip route flush dev eth0
2016/05/23 22:34:48 :: Putting interface up...
2016/05/23 22:34:48 :: ifconfig eth0 up
2016/05/23 22:34:48 :: rfkill: blocking wifi
2016/05/23 22:34:48 :: rfkill: blocking wlan
2016/05/23 22:34:48 :: rfkill: blocking wimax
2016/05/23 22:34:48 :: rfkill: blocking wwan
2016/05/23 22:34:50 :: Running DHCP with hostname noahlub
2016/05/23 22:34:50 :: attempting to set hostname with dhclient
2016/05/23 22:34:50 :: using dhcpcd or another supported client may work better
2016/05/23 22:34:50 :: /sbin/dhclient -v eth0
2016/05/23 22:34:50 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 22:34:50 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 22:34:50 :: All rights reserved.
2016/05/23 22:34:50 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 22:34:50 :: 
2016/05/23 22:34:50 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:34:50 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:34:50 :: Sending on   Socket/fallback
2016/05/23 22:34:50 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xb9d40801)
2016/05/23 22:34:50 :: found backend in configuration external
2016/05/23 22:34:53 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 (xid=0xb9d40801)
2016/05/23 22:34:53 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x108d4b9)
2016/05/23 22:34:53 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 22:34:53 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 22:34:53 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 22:34:53 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 22:34:53 :: bound to 162.228.104.207 -- renewal in 270 seconds.
2016/05/23 22:34:53 :: DHCP connection successful
2016/05/23 22:34:53 :: Setting DNS : 8.8.8.8
2016/05/23 22:34:53 :: Setting DNS : 8.8.4.4
2016/05/23 22:34:53 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 22:34:53 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 22:34:53 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 22:34:53 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 22:34:53 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 22:34:53 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 22:34:57 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 22:34:57 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 22:34:57 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 22:34:57 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 22:34:58 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 22:34:58 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 22:34:58 :: Connecting thread exiting.
2016/05/23 22:34:58 :: ifconfig eth0
2016/05/23 22:34:58 :: IP Address is: 162.228.104.207
2016/05/23 22:34:58 :: Sending connection attempt result success
2016/05/23 22:35:00 :: ifconfig eth0
2016/05/23 22:35:02 :: ifconfig eth0
2016/05/23 22:35:04 :: ifconfig eth0
2016/05/23 22:35:06 :: ifconfig eth0
2016/05/23 22:35:09 :: ifconfig eth0
2016/05/23 22:35:09 :: rfkill: blocking wifi
2016/05/23 22:35:09 :: rfkill: blocking wlan
2016/05/23 22:35:09 :: rfkill: blocking wimax
2016/05/23 22:35:09 :: rfkill: blocking wwan
2016/05/23 22:35:11 :: rfkill: blocking wifi
2016/05/23 22:35:11 :: rfkill: blocking wlan
2016/05/23 22:35:11 :: rfkill: blocking wimax
2016/05/23 22:35:11 :: rfkill: blocking wwan
2016/05/23 22:35:11 :: ifconfig eth0
2016/05/23 22:35:11 :: rfkill: blocking wifi
2016/05/23 22:35:11 :: rfkill: blocking wlan
2016/05/23 22:35:11 :: rfkill: blocking wimax
2016/05/23 22:35:11 :: rfkill: blocking wwan
2016/05/23 22:35:13 :: ifconfig eth0
2016/05/23 22:35:19 :: ifconfig eth0
2016/05/23 22:35:24 :: ifconfig eth0
2016/05/23 22:35:29 :: ifconfig eth0
2016/05/23 22:35:34 :: ifconfig eth0
2016/05/23 22:35:39 :: ifconfig eth0
2016/05/23 22:35:44 :: ifconfig eth0
2016/05/23 22:35:49 :: ifconfig eth0
2016/05/23 22:35:54 :: ifconfig eth0
2016/05/23 22:35:59 :: ifconfig eth0
2016/05/23 22:36:04 :: ifconfig eth0
2016/05/23 22:36:09 :: ifconfig eth0
2016/05/23 22:36:14 :: ifconfig eth0
2016/05/23 22:36:19 :: ifconfig eth0
2016/05/23 22:36:24 :: ifconfig eth0
2016/05/23 22:36:29 :: ifconfig eth0
2016/05/23 22:36:34 :: ifconfig eth0
2016/05/23 22:36:39 :: ifconfig eth0
2016/05/23 22:36:44 :: ifconfig eth0
2016/05/23 22:36:49 :: ifconfig eth0
2016/05/23 22:36:54 :: ifconfig eth0
2016/05/23 22:36:59 :: ifconfig eth0
2016/05/23 22:37:01 :: found default in configuration 1
2016/05/23 22:37:01 :: Reading wired profile wired-default
2016/05/23 22:37:01 :: found afterscript in configuration None
2016/05/23 22:37:01 :: found dhcphostname in configuration noahlub
2016/05/23 22:37:01 :: found postdisconnectscript in configuration None
2016/05/23 22:37:01 :: found dns_domain in configuration None
2016/05/23 22:37:01 :: found gateway in configuration None
2016/05/23 22:37:01 :: found use_global_dns in configuration False
2016/05/23 22:37:01 :: found lastused in configuration True
2016/05/23 22:37:01 :: found encryption_enabled in configuration False
2016/05/23 22:37:01 :: found beforescript in configuration None
2016/05/23 22:37:01 :: found ip in configuration None
2016/05/23 22:37:01 :: found broadcast in configuration None
2016/05/23 22:37:01 :: found netmask in configuration None
2016/05/23 22:37:01 :: found usedhcphostname in configuration 1
2016/05/23 22:37:01 :: found predisconnectscript in configuration None
2016/05/23 22:37:01 :: found enctype in configuration None
2016/05/23 22:37:01 :: found default in configuration 1
2016/05/23 22:37:01 :: found dns2 in configuration 8.8.4.4
2016/05/23 22:37:01 :: found search_domain in configuration None
2016/05/23 22:37:01 :: found use_static_dns in configuration True
2016/05/23 22:37:01 :: found dns3 in configuration None
2016/05/23 22:37:01 :: found profilename in configuration wired-default
2016/05/23 22:37:01 :: found dns1 in configuration 8.8.8.8
2016/05/23 22:37:01 :: found default in configuration 1
2016/05/23 22:37:01 :: saving wired profile wired-default
2016/05/23 22:37:01 :: scanning start
2016/05/23 22:37:01 :: scanning done
2016/05/23 22:37:01 :: found 0 networks:
2016/05/23 22:37:02 :: ifconfig eth0
2016/05/23 22:37:04 :: ifconfig eth0
2016/05/23 22:37:06 :: ifconfig eth0
2016/05/23 22:37:08 :: ifconfig eth0
2016/05/23 22:37:10 :: ifconfig eth0
2016/05/23 22:37:12 :: ifconfig eth0
2016/05/23 22:37:13 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:37:13 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:37:13 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:37:13 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:37:13 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:37:13 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:37:13 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:37:13 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:37:13 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:37:13 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:37:13 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:37:13 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:37:13 :: attempting to set hostname with dhclient
2016/05/23 22:37:13 :: using dhcpcd or another supported client may work better
2016/05/23 22:37:13 :: /sbin/dhclient -v -r eth0
2016/05/23 22:37:14 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:37:14 :: /sbin/ip route flush dev eth0
2016/05/23 22:37:14 :: ifconfig eth0 down
2016/05/23 22:37:14 :: ifconfig eth0 up
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:37:15 :: wpa_cli -i eth0 terminate
2016/05/23 22:37:15 :: Forced disconnect on
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:37:15 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:37:15 :: attempting to set hostname with dhclient
2016/05/23 22:37:15 :: using dhcpcd or another supported client may work better
2016/05/23 22:37:15 :: /sbin/dhclient -v -r eth0
2016/05/23 22:37:15 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:37:15 :: /sbin/ip route flush dev eth0
2016/05/23 22:37:15 :: ifconfig eth0 down
2016/05/23 22:37:15 :: ifconfig eth0 up
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:37:15 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:37:15 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:37:15 :: wpa_cli -i eth0 terminate
2016/05/23 22:37:15 :: ifconfig eth0
2016/05/23 22:37:18 :: ifconfig eth0
2016/05/23 22:37:20 :: ifconfig eth0
2016/05/23 22:37:22 :: ifconfig eth0
2016/05/23 22:37:24 :: ifconfig eth0
2016/05/23 22:37:26 :: ifconfig eth0
2016/05/23 22:37:28 :: ifconfig eth0
2016/05/23 22:37:30 :: ifconfig eth0
2016/05/23 22:37:32 :: ifconfig eth0
2016/05/23 22:37:34 :: ifconfig eth0
2016/05/23 22:37:36 :: ifconfig eth0
2016/05/23 22:37:38 :: ifconfig eth0
2016/05/23 22:37:40 :: ifconfig eth0
2016/05/23 22:37:42 :: ifconfig eth0
2016/05/23 22:37:44 :: ifconfig eth0
2016/05/23 22:37:46 :: ifconfig eth0
2016/05/23 22:37:48 :: ifconfig eth0
2016/05/23 22:37:50 :: ifconfig eth0
2016/05/23 22:37:52 :: ifconfig eth0
2016/05/23 22:37:54 :: ifconfig eth0
2016/05/23 22:37:56 :: ifconfig eth0
2016/05/23 22:37:58 :: ifconfig eth0
2016/05/23 22:38:00 :: ifconfig eth0
2016/05/23 22:38:02 :: ifconfig eth0
2016/05/23 22:38:04 :: ifconfig eth0
2016/05/23 22:38:06 :: ifconfig eth0
2016/05/23 22:38:08 :: ifconfig eth0
2016/05/23 22:38:10 :: ifconfig eth0
2016/05/23 22:38:12 :: ifconfig eth0
2016/05/23 22:38:14 :: ifconfig eth0
2016/05/23 22:38:16 :: ifconfig eth0
2016/05/23 22:38:18 :: ifconfig eth0
2016/05/23 22:38:20 :: ifconfig eth0
2016/05/23 22:38:22 :: ifconfig eth0
2016/05/23 22:38:24 :: ifconfig eth0
2016/05/23 22:38:26 :: ifconfig eth0
2016/05/23 22:38:28 :: ifconfig eth0
2016/05/23 22:38:31 :: ifconfig eth0
2016/05/23 22:38:33 :: ifconfig eth0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:38:34 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:38:34 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:38:34 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:38:34 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:38:34 :: attempting to set hostname with dhclient
2016/05/23 22:38:34 :: using dhcpcd or another supported client may work better
2016/05/23 22:38:34 :: /sbin/dhclient -v -r eth0
2016/05/23 22:38:34 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:38:34 :: /sbin/ip route flush dev eth0
2016/05/23 22:38:34 :: ifconfig eth0 down
2016/05/23 22:38:34 :: ifconfig eth0 up
2016/05/23 22:38:34 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:38:34 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:38:34 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:38:34 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:38:34 :: wpa_cli -i eth0 terminate
2016/05/23 22:38:34 :: found lastused in configuration True
2016/05/23 22:38:34 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 22:38:34 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 22:38:34 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 22:38:34 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 22:38:34 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 22:38:34 :: Putting interface down
2016/05/23 22:38:34 :: ifconfig eth0 down
2016/05/23 22:38:35 :: Releasing DHCP leases...
2016/05/23 22:38:35 :: attempting to set hostname with dhclient
2016/05/23 22:38:35 :: using dhcpcd or another supported client may work better
2016/05/23 22:38:35 :: /sbin/dhclient -v -r eth0
2016/05/23 22:38:35 :: Setting false IP...
2016/05/23 22:38:35 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:38:35 :: Stopping wpa_supplicant
2016/05/23 22:38:35 :: wpa_cli -i eth0 terminate
2016/05/23 22:38:35 :: Flushing the routing table...
2016/05/23 22:38:35 :: /sbin/ip route flush dev eth0
2016/05/23 22:38:35 :: Putting interface up...
2016/05/23 22:38:35 :: ifconfig eth0 up
2016/05/23 22:38:37 :: Running DHCP with hostname noahlub
2016/05/23 22:38:37 :: attempting to set hostname with dhclient
2016/05/23 22:38:37 :: using dhcpcd or another supported client may work better
2016/05/23 22:38:37 :: /sbin/dhclient -v eth0
2016/05/23 22:38:37 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 22:38:37 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 22:38:37 :: All rights reserved.
2016/05/23 22:38:37 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 22:38:37 :: 
2016/05/23 22:38:37 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:38:37 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:38:37 :: Sending on   Socket/fallback
2016/05/23 22:38:37 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x602a1371)
2016/05/23 22:38:40 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x602a1371)
2016/05/23 22:38:40 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x71132a60)
2016/05/23 22:38:40 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 22:38:40 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 22:38:40 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 22:38:40 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 22:38:40 :: bound to 162.228.104.207 -- renewal in 285 seconds.
2016/05/23 22:38:40 :: DHCP connection successful
2016/05/23 22:38:40 :: Setting DNS : 8.8.8.8
2016/05/23 22:38:40 :: Setting DNS : 8.8.4.4
2016/05/23 22:38:40 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 22:38:40 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 22:38:40 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 22:38:40 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 22:38:40 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 22:38:40 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 22:38:44 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 22:38:44 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 22:38:44 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 22:38:44 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 22:38:45 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 22:38:45 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 22:38:45 :: Connecting thread exiting.
2016/05/23 22:38:45 :: ifconfig eth0
2016/05/23 22:38:45 :: IP Address is: 162.228.104.207
2016/05/23 22:38:45 :: Sending connection attempt result success
2016/05/23 22:38:47 :: ifconfig eth0
2016/05/23 22:38:49 :: ifconfig eth0
2016/05/23 22:38:51 :: ifconfig eth0
2016/05/23 22:38:53 :: ifconfig eth0
2016/05/23 22:38:55 :: ifconfig eth0
2016/05/23 22:38:57 :: ifconfig eth0
2016/05/23 22:38:59 :: ifconfig eth0
2016/05/23 22:39:01 :: ifconfig eth0
2016/05/23 22:39:03 :: ifconfig eth0
2016/05/23 22:39:05 :: ifconfig eth0
2016/05/23 22:39:07 :: ifconfig eth0
2016/05/23 22:39:09 :: ifconfig eth0
2016/05/23 22:39:11 :: ifconfig eth0
2016/05/23 22:39:13 :: ifconfig eth0
2016/05/23 22:39:15 :: ifconfig eth0
2016/05/23 22:39:17 :: ifconfig eth0
2016/05/23 22:39:19 :: ifconfig eth0
2016/05/23 22:39:21 :: ifconfig eth0
2016/05/23 22:39:23 :: ifconfig eth0
2016/05/23 22:39:25 :: ifconfig eth0
2016/05/23 22:39:27 :: ifconfig eth0
2016/05/23 22:39:29 :: ifconfig eth0
2016/05/23 22:39:31 :: ifconfig eth0
2016/05/23 22:39:34 :: ifconfig eth0
2016/05/23 22:39:36 :: ifconfig eth0
2016/05/23 22:39:38 :: ifconfig eth0
2016/05/23 22:39:40 :: ifconfig eth0
2016/05/23 22:39:42 :: ifconfig eth0
2016/05/23 22:39:45 :: ifconfig eth0
2016/05/23 22:39:47 :: ifconfig eth0
2016/05/23 22:39:49 :: ifconfig eth0
2016/05/23 22:39:51 :: ifconfig eth0
2016/05/23 22:39:53 :: ifconfig eth0
2016/05/23 22:39:55 :: ifconfig eth0
2016/05/23 22:39:58 :: ifconfig eth0
2016/05/23 22:40:00 :: ifconfig eth0
2016/05/23 22:40:02 :: ifconfig eth0
2016/05/23 22:40:04 :: ifconfig eth0
2016/05/23 22:40:06 :: ifconfig eth0
2016/05/23 22:40:08 :: ifconfig eth0
2016/05/23 22:40:10 :: ifconfig eth0
2016/05/23 22:40:12 :: ifconfig eth0
2016/05/23 22:40:14 :: ifconfig eth0
2016/05/23 22:40:16 :: ifconfig eth0
2016/05/23 22:40:19 :: ifconfig eth0
2016/05/23 22:40:21 :: ifconfig eth0
2016/05/23 22:40:23 :: ifconfig eth0
2016/05/23 22:40:26 :: ifconfig eth0
2016/05/23 22:40:28 :: ifconfig eth0
2016/05/23 22:40:30 :: ifconfig eth0
2016/05/23 22:40:32 :: ifconfig eth0
2016/05/23 22:40:34 :: ifconfig eth0
2016/05/23 22:40:36 :: ifconfig eth0
2016/05/23 22:40:38 :: ifconfig eth0
2016/05/23 22:40:40 :: ifconfig eth0
2016/05/23 22:40:42 :: ifconfig eth0
2016/05/23 22:40:45 :: ifconfig eth0
2016/05/23 22:40:47 :: ifconfig eth0
2016/05/23 22:40:49 :: ifconfig eth0
2016/05/23 22:40:51 :: ifconfig eth0
2016/05/23 22:40:54 :: ifconfig eth0
2016/05/23 22:40:56 :: ifconfig eth0
2016/05/23 22:40:58 :: ifconfig eth0
2016/05/23 22:41:00 :: ifconfig eth0
2016/05/23 22:41:02 :: ifconfig eth0
2016/05/23 22:41:05 :: ifconfig eth0
2016/05/23 22:41:07 :: ifconfig eth0
2016/05/23 22:41:09 :: ifconfig eth0
2016/05/23 22:41:12 :: ifconfig eth0
2016/05/23 22:41:14 :: ifconfig eth0
2016/05/23 22:41:16 :: ifconfig eth0
2016/05/23 22:41:18 :: ifconfig eth0
2016/05/23 22:41:21 :: ifconfig eth0
2016/05/23 22:41:23 :: ifconfig eth0
2016/05/23 22:41:25 :: ifconfig eth0
2016/05/23 22:41:27 :: ifconfig eth0
2016/05/23 22:41:30 :: ifconfig eth0
2016/05/23 22:41:32 :: ifconfig eth0
2016/05/23 22:41:34 :: ifconfig eth0
2016/05/23 22:41:36 :: ifconfig eth0
2016/05/23 22:41:38 :: ifconfig eth0
2016/05/23 22:41:41 :: ifconfig eth0
2016/05/23 22:41:43 :: ifconfig eth0
2016/05/23 22:41:45 :: ifconfig eth0
2016/05/23 22:41:47 :: ifconfig eth0
2016/05/23 22:41:49 :: ifconfig eth0
2016/05/23 22:41:51 :: ifconfig eth0
2016/05/23 22:41:53 :: ifconfig eth0
2016/05/23 22:41:56 :: ifconfig eth0
2016/05/23 22:41:58 :: ifconfig eth0
2016/05/23 22:42:00 :: ifconfig eth0
2016/05/23 22:42:02 :: ifconfig eth0
2016/05/23 22:42:04 :: ifconfig eth0
2016/05/23 22:42:06 :: ifconfig eth0
2016/05/23 22:42:08 :: ifconfig eth0
2016/05/23 22:42:10 :: ifconfig eth0
2016/05/23 22:42:13 :: ifconfig eth0
2016/05/23 22:42:15 :: ifconfig eth0
2016/05/23 22:42:17 :: ifconfig eth0
2016/05/23 22:42:19 :: ifconfig eth0
2016/05/23 22:42:21 :: ifconfig eth0
2016/05/23 22:42:23 :: ifconfig eth0
2016/05/23 22:42:25 :: ifconfig eth0
2016/05/23 22:42:27 :: ifconfig eth0
2016/05/23 22:42:29 :: ifconfig eth0
2016/05/23 22:42:31 :: ifconfig eth0
2016/05/23 22:42:33 :: ifconfig eth0
2016/05/23 22:42:36 :: ifconfig eth0
2016/05/23 22:42:38 :: ifconfig eth0
2016/05/23 22:42:40 :: ifconfig eth0
2016/05/23 22:42:42 :: ifconfig eth0
2016/05/23 22:42:44 :: ifconfig eth0
2016/05/23 22:42:46 :: ifconfig eth0
2016/05/23 22:42:49 :: ifconfig eth0
2016/05/23 22:42:51 :: ifconfig eth0
2016/05/23 22:42:53 :: ifconfig eth0
2016/05/23 22:42:55 :: ifconfig eth0
2016/05/23 22:42:57 :: ifconfig eth0
2016/05/23 22:42:59 :: ifconfig eth0
2016/05/23 22:43:01 :: ifconfig eth0
2016/05/23 22:43:03 :: ifconfig eth0
2016/05/23 22:43:05 :: ifconfig eth0
2016/05/23 22:43:07 :: ifconfig eth0
2016/05/23 22:43:09 :: ifconfig eth0
2016/05/23 22:43:12 :: ifconfig eth0
2016/05/23 22:43:14 :: ifconfig eth0
2016/05/23 22:43:16 :: ifconfig eth0
2016/05/23 22:43:18 :: ifconfig eth0
2016/05/23 22:43:20 :: ifconfig eth0
2016/05/23 22:43:22 :: ifconfig eth0
2016/05/23 22:43:24 :: ifconfig eth0
2016/05/23 22:43:26 :: ifconfig eth0
2016/05/23 22:43:28 :: ifconfig eth0
2016/05/23 22:43:30 :: ifconfig eth0
2016/05/23 22:43:32 :: ifconfig eth0
2016/05/23 22:43:35 :: ifconfig eth0
2016/05/23 22:43:37 :: ifconfig eth0
2016/05/23 22:43:39 :: ifconfig eth0
2016/05/23 22:43:41 :: ifconfig eth0
2016/05/23 22:43:44 :: ifconfig eth0
2016/05/23 22:43:46 :: ifconfig eth0
2016/05/23 22:43:48 :: ifconfig eth0
2016/05/23 22:43:51 :: ifconfig eth0
2016/05/23 22:43:53 :: ifconfig eth0
2016/05/23 22:43:55 :: ifconfig eth0
2016/05/23 22:43:57 :: ifconfig eth0
2016/05/23 22:44:00 :: ifconfig eth0
2016/05/23 22:44:02 :: ifconfig eth0
2016/05/23 22:44:04 :: ifconfig eth0
2016/05/23 22:44:06 :: ifconfig eth0
2016/05/23 22:44:09 :: ifconfig eth0
2016/05/23 22:44:11 :: ifconfig eth0
2016/05/23 22:44:13 :: ifconfig eth0
2016/05/23 22:44:15 :: ifconfig eth0
2016/05/23 22:44:18 :: ifconfig eth0
2016/05/23 22:44:20 :: ifconfig eth0
2016/05/23 22:44:22 :: ifconfig eth0
2016/05/23 22:44:24 :: ifconfig eth0
2016/05/23 22:44:26 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:44:26 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:44:26 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:44:26 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:44:26 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:44:26 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:44:26 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:44:26 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:44:26 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:44:26 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:44:26 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:44:26 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:44:26 :: attempting to set hostname with dhclient
2016/05/23 22:44:26 :: using dhcpcd or another supported client may work better
2016/05/23 22:44:26 :: /sbin/dhclient -v -r eth0
2016/05/23 22:44:27 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:44:27 :: /sbin/ip route flush dev eth0
2016/05/23 22:44:27 :: ifconfig eth0 down
2016/05/23 22:44:27 :: ifconfig eth0 up
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:44:28 :: wpa_cli -i eth0 terminate
2016/05/23 22:44:28 :: Forced disconnect on
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:44:28 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:44:28 :: attempting to set hostname with dhclient
2016/05/23 22:44:28 :: using dhcpcd or another supported client may work better
2016/05/23 22:44:28 :: /sbin/dhclient -v -r eth0
2016/05/23 22:44:28 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:44:28 :: /sbin/ip route flush dev eth0
2016/05/23 22:44:28 :: ifconfig eth0 down
2016/05/23 22:44:28 :: ifconfig eth0 up
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:44:28 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:44:28 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:44:28 :: wpa_cli -i eth0 terminate
2016/05/23 22:44:28 :: ifconfig eth0
2016/05/23 22:44:31 :: ifconfig eth0
2016/05/23 22:44:33 :: ifconfig eth0
2016/05/23 22:44:35 :: ifconfig eth0
2016/05/23 22:44:37 :: ifconfig eth0
2016/05/23 22:44:39 :: ifconfig eth0
2016/05/23 22:44:42 :: ifconfig eth0
2016/05/23 22:44:44 :: ifconfig eth0
2016/05/23 22:44:46 :: ifconfig eth0
2016/05/23 22:44:48 :: ifconfig eth0
2016/05/23 22:44:50 :: ifconfig eth0
2016/05/23 22:44:52 :: ifconfig eth0
2016/05/23 22:44:54 :: ifconfig eth0
2016/05/23 22:44:56 :: ifconfig eth0
2016/05/23 22:44:58 :: ifconfig eth0
2016/05/23 22:45:01 :: ifconfig eth0
2016/05/23 22:45:03 :: ifconfig eth0
2016/05/23 22:45:05 :: ifconfig eth0
2016/05/23 22:45:07 :: ifconfig eth0
2016/05/23 22:45:09 :: ifconfig eth0
2016/05/23 22:45:11 :: ifconfig eth0
2016/05/23 22:45:14 :: ifconfig eth0
2016/05/23 22:45:16 :: ifconfig eth0
2016/05/23 22:45:18 :: ifconfig eth0
2016/05/23 22:45:20 :: ifconfig eth0
2016/05/23 22:45:22 :: ifconfig eth0
2016/05/23 22:45:24 :: ifconfig eth0
2016/05/23 22:45:26 :: ifconfig eth0
2016/05/23 22:45:28 :: ifconfig eth0
2016/05/23 22:45:31 :: ifconfig eth0
2016/05/23 22:45:33 :: ifconfig eth0
2016/05/23 22:45:35 :: ifconfig eth0
2016/05/23 22:45:37 :: ifconfig eth0
2016/05/23 22:45:39 :: ifconfig eth0
2016/05/23 22:45:41 :: ifconfig eth0
2016/05/23 22:45:43 :: ifconfig eth0
2016/05/23 22:45:46 :: ifconfig eth0
2016/05/23 22:45:48 :: ifconfig eth0
2016/05/23 22:45:50 :: ifconfig eth0
2016/05/23 22:45:52 :: ifconfig eth0
2016/05/23 22:45:54 :: ifconfig eth0
2016/05/23 22:45:56 :: ifconfig eth0
2016/05/23 22:45:59 :: ifconfig eth0
2016/05/23 22:46:01 :: ifconfig eth0
2016/05/23 22:46:03 :: ifconfig eth0
2016/05/23 22:46:05 :: ifconfig eth0
2016/05/23 22:46:07 :: ifconfig eth0
2016/05/23 22:46:10 :: ifconfig eth0
2016/05/23 22:46:12 :: ifconfig eth0
2016/05/23 22:46:14 :: ifconfig eth0
2016/05/23 22:46:16 :: ifconfig eth0
2016/05/23 22:46:18 :: ifconfig eth0
2016/05/23 22:46:20 :: ifconfig eth0
2016/05/23 22:46:22 :: ifconfig eth0
2016/05/23 22:46:25 :: ifconfig eth0
2016/05/23 22:46:27 :: ifconfig eth0
2016/05/23 22:46:29 :: ifconfig eth0
2016/05/23 22:46:31 :: ifconfig eth0
2016/05/23 22:46:34 :: ifconfig eth0
2016/05/23 22:46:36 :: ifconfig eth0
2016/05/23 22:46:38 :: ifconfig eth0
2016/05/23 22:46:40 :: ifconfig eth0
2016/05/23 22:46:42 :: ifconfig eth0
2016/05/23 22:46:44 :: ifconfig eth0
2016/05/23 22:46:47 :: ifconfig eth0
2016/05/23 22:46:49 :: ifconfig eth0
2016/05/23 22:46:51 :: ifconfig eth0
2016/05/23 22:46:53 :: ifconfig eth0
2016/05/23 22:46:55 :: ifconfig eth0
2016/05/23 22:46:57 :: ifconfig eth0
2016/05/23 22:46:59 :: ifconfig eth0
2016/05/23 22:47:02 :: ifconfig eth0
2016/05/23 22:47:04 :: ifconfig eth0
2016/05/23 22:47:06 :: ifconfig eth0
2016/05/23 22:47:08 :: ifconfig eth0
2016/05/23 22:47:11 :: ifconfig eth0
2016/05/23 22:47:13 :: ifconfig eth0
2016/05/23 22:47:15 :: ifconfig eth0
2016/05/23 22:47:17 :: ifconfig eth0
2016/05/23 22:47:19 :: ifconfig eth0
2016/05/23 22:47:21 :: ifconfig eth0
2016/05/23 22:47:23 :: ifconfig eth0
2016/05/23 22:47:25 :: ifconfig eth0
2016/05/23 22:47:25 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:47:25 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:47:25 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:47:25 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:47:25 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:47:25 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:47:25 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:47:25 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:47:25 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:47:25 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:47:26 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:47:26 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:47:26 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:47:26 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:47:26 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:47:26 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:47:26 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:47:26 :: attempting to set hostname with dhclient
2016/05/23 22:47:26 :: using dhcpcd or another supported client may work better
2016/05/23 22:47:26 :: /sbin/dhclient -v -r eth0
2016/05/23 22:47:26 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:47:26 :: /sbin/ip route flush dev eth0
2016/05/23 22:47:26 :: ifconfig eth0 down
2016/05/23 22:47:26 :: ifconfig eth0 up
2016/05/23 22:47:26 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:47:26 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:47:26 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:47:26 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:47:26 :: wpa_cli -i eth0 terminate
2016/05/23 22:47:26 :: found lastused in configuration True
2016/05/23 22:47:26 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 22:47:26 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 22:47:26 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 22:47:26 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 22:47:26 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 22:47:26 :: Putting interface down
2016/05/23 22:47:26 :: ifconfig eth0 down
2016/05/23 22:47:27 :: Releasing DHCP leases...
2016/05/23 22:47:27 :: attempting to set hostname with dhclient
2016/05/23 22:47:27 :: using dhcpcd or another supported client may work better
2016/05/23 22:47:27 :: /sbin/dhclient -v -r eth0
2016/05/23 22:47:27 :: Setting false IP...
2016/05/23 22:47:27 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:47:27 :: Stopping wpa_supplicant
2016/05/23 22:47:27 :: wpa_cli -i eth0 terminate
2016/05/23 22:47:27 :: Flushing the routing table...
2016/05/23 22:47:27 :: /sbin/ip route flush dev eth0
2016/05/23 22:47:27 :: Putting interface up...
2016/05/23 22:47:27 :: ifconfig eth0 up
2016/05/23 22:47:29 :: Running DHCP with hostname noahlub
2016/05/23 22:47:29 :: attempting to set hostname with dhclient
2016/05/23 22:47:29 :: using dhcpcd or another supported client may work better
2016/05/23 22:47:29 :: /sbin/dhclient -v eth0
2016/05/23 22:47:29 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 22:47:29 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 22:47:29 :: All rights reserved.
2016/05/23 22:47:29 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 22:47:29 :: 
2016/05/23 22:47:29 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:47:29 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 22:47:29 :: Sending on   Socket/fallback
2016/05/23 22:47:29 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x8053020c)
2016/05/23 22:47:32 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 (xid=0x8053020c)
2016/05/23 22:47:32 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0xc025380)
2016/05/23 22:47:32 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 22:47:32 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 22:47:33 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 22:47:33 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 22:47:33 :: bound to 162.228.104.207 -- renewal in 286 seconds.
2016/05/23 22:47:33 :: DHCP connection successful
2016/05/23 22:47:33 :: Setting DNS : 8.8.8.8
2016/05/23 22:47:33 :: Setting DNS : 8.8.4.4
2016/05/23 22:47:33 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 22:47:33 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 22:47:33 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 22:47:33 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 22:47:33 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 22:47:33 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 22:47:37 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 22:47:37 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 22:47:37 :: Connecting thread exiting.
2016/05/23 22:47:37 :: ifconfig eth0
2016/05/23 22:47:37 :: IP Address is: 162.228.104.207
2016/05/23 22:47:37 :: Sending connection attempt result success
2016/05/23 22:47:39 :: ifconfig eth0
2016/05/23 22:47:41 :: ifconfig eth0
2016/05/23 22:47:43 :: ifconfig eth0
2016/05/23 22:47:45 :: ifconfig eth0
2016/05/23 22:47:48 :: ifconfig eth0
2016/05/23 22:47:50 :: ifconfig eth0
2016/05/23 22:47:52 :: ifconfig eth0
2016/05/23 22:47:54 :: ifconfig eth0
2016/05/23 22:47:56 :: ifconfig eth0
2016/05/23 22:47:58 :: ifconfig eth0
2016/05/23 22:48:00 :: ifconfig eth0
2016/05/23 22:48:02 :: ifconfig eth0
2016/05/23 22:48:04 :: ifconfig eth0
2016/05/23 22:48:06 :: ifconfig eth0
2016/05/23 22:48:08 :: ifconfig eth0
2016/05/23 22:48:10 :: ifconfig eth0
2016/05/23 22:48:13 :: ifconfig eth0
2016/05/23 22:48:15 :: ifconfig eth0
2016/05/23 22:48:17 :: ifconfig eth0
2016/05/23 22:48:19 :: ifconfig eth0
2016/05/23 22:48:21 :: ifconfig eth0
2016/05/23 22:48:23 :: ifconfig eth0
2016/05/23 22:48:25 :: ifconfig eth0
2016/05/23 22:48:27 :: ifconfig eth0
2016/05/23 22:48:29 :: ifconfig eth0
2016/05/23 22:48:31 :: ifconfig eth0
2016/05/23 22:48:33 :: ifconfig eth0
2016/05/23 22:48:35 :: ifconfig eth0
2016/05/23 22:48:37 :: ifconfig eth0
2016/05/23 22:48:39 :: ifconfig eth0
2016/05/23 22:48:41 :: ifconfig eth0
2016/05/23 22:48:43 :: ifconfig eth0
2016/05/23 22:48:45 :: ifconfig eth0
2016/05/23 22:48:47 :: ifconfig eth0
2016/05/23 22:48:49 :: ifconfig eth0
2016/05/23 22:48:51 :: ifconfig eth0
2016/05/23 22:48:53 :: ifconfig eth0
2016/05/23 22:48:55 :: ifconfig eth0
2016/05/23 22:48:57 :: ifconfig eth0
2016/05/23 22:48:59 :: ifconfig eth0
2016/05/23 22:49:01 :: ifconfig eth0
2016/05/23 22:49:03 :: ifconfig eth0
2016/05/23 22:49:05 :: ifconfig eth0
2016/05/23 22:49:07 :: ifconfig eth0
2016/05/23 22:49:09 :: ifconfig eth0
2016/05/23 22:49:11 :: ifconfig eth0
2016/05/23 22:49:13 :: ifconfig eth0
2016/05/23 22:49:15 :: ifconfig eth0
2016/05/23 22:49:18 :: ifconfig eth0
2016/05/23 22:49:20 :: ifconfig eth0
2016/05/23 22:49:22 :: ifconfig eth0
2016/05/23 22:49:24 :: ifconfig eth0
2016/05/23 22:49:26 :: ifconfig eth0
2016/05/23 22:49:28 :: ifconfig eth0
2016/05/23 22:49:31 :: ifconfig eth0
2016/05/23 22:49:33 :: ifconfig eth0
2016/05/23 22:49:35 :: ifconfig eth0
2016/05/23 22:49:37 :: ifconfig eth0
2016/05/23 22:49:39 :: ifconfig eth0
2016/05/23 22:49:42 :: ifconfig eth0
2016/05/23 22:49:44 :: ifconfig eth0
2016/05/23 22:49:46 :: ifconfig eth0
2016/05/23 22:49:48 :: ifconfig eth0
2016/05/23 22:49:51 :: ifconfig eth0
2016/05/23 22:49:53 :: ifconfig eth0
2016/05/23 22:49:55 :: ifconfig eth0
2016/05/23 22:49:57 :: ifconfig eth0
2016/05/23 22:49:59 :: ifconfig eth0
2016/05/23 22:50:01 :: ifconfig eth0
2016/05/23 22:50:04 :: ifconfig eth0
2016/05/23 22:50:06 :: ifconfig eth0
2016/05/23 22:50:08 :: ifconfig eth0
2016/05/23 22:50:10 :: ifconfig eth0
2016/05/23 22:50:13 :: ifconfig eth0
2016/05/23 22:50:15 :: ifconfig eth0
2016/05/23 22:50:17 :: ifconfig eth0
2016/05/23 22:50:19 :: ifconfig eth0
2016/05/23 22:50:21 :: ifconfig eth0
2016/05/23 22:50:23 :: ifconfig eth0
2016/05/23 22:50:25 :: ifconfig eth0
2016/05/23 22:50:28 :: ifconfig eth0
2016/05/23 22:50:30 :: ifconfig eth0
2016/05/23 22:50:32 :: ifconfig eth0
2016/05/23 22:50:34 :: ifconfig eth0
2016/05/23 22:50:37 :: ifconfig eth0
2016/05/23 22:50:39 :: ifconfig eth0
2016/05/23 22:50:41 :: ifconfig eth0
2016/05/23 22:50:43 :: ifconfig eth0
2016/05/23 22:50:45 :: ifconfig eth0
2016/05/23 22:50:48 :: ifconfig eth0
2016/05/23 22:50:50 :: ifconfig eth0
2016/05/23 22:50:52 :: ifconfig eth0
2016/05/23 22:50:54 :: ifconfig eth0
2016/05/23 22:50:56 :: ifconfig eth0
2016/05/23 22:50:58 :: ifconfig eth0
2016/05/23 22:51:00 :: ifconfig eth0
2016/05/23 22:51:03 :: ifconfig eth0
2016/05/23 22:51:05 :: ifconfig eth0
2016/05/23 22:51:07 :: ifconfig eth0
2016/05/23 22:51:09 :: ifconfig eth0
2016/05/23 22:51:11 :: ifconfig eth0
2016/05/23 22:51:13 :: ifconfig eth0
2016/05/23 22:51:15 :: ifconfig eth0
2016/05/23 22:51:17 :: ifconfig eth0
2016/05/23 22:51:19 :: ifconfig eth0
2016/05/23 22:51:22 :: ifconfig eth0
2016/05/23 22:51:24 :: ifconfig eth0
2016/05/23 22:51:26 :: ifconfig eth0
2016/05/23 22:51:28 :: ifconfig eth0
2016/05/23 22:51:31 :: ifconfig eth0
2016/05/23 22:51:33 :: ifconfig eth0
2016/05/23 22:51:35 :: ifconfig eth0
2016/05/23 22:51:37 :: ifconfig eth0
2016/05/23 22:51:39 :: ifconfig eth0
2016/05/23 22:51:41 :: ifconfig eth0
2016/05/23 22:51:43 :: ifconfig eth0
2016/05/23 22:51:45 :: ifconfig eth0
2016/05/23 22:51:47 :: ifconfig eth0
2016/05/23 22:51:49 :: ifconfig eth0
2016/05/23 22:51:51 :: ifconfig eth0
2016/05/23 22:51:53 :: ifconfig eth0
2016/05/23 22:51:55 :: ifconfig eth0
2016/05/23 22:51:57 :: ifconfig eth0
2016/05/23 22:52:00 :: ifconfig eth0
2016/05/23 22:52:02 :: ifconfig eth0
2016/05/23 22:52:04 :: ifconfig eth0
2016/05/23 22:52:06 :: ifconfig eth0
2016/05/23 22:52:08 :: ifconfig eth0
2016/05/23 22:52:10 :: ifconfig eth0
2016/05/23 22:52:12 :: ifconfig eth0
2016/05/23 22:52:14 :: ifconfig eth0
2016/05/23 22:52:16 :: ifconfig eth0
2016/05/23 22:52:18 :: ifconfig eth0
2016/05/23 22:52:21 :: ifconfig eth0
2016/05/23 22:52:23 :: ifconfig eth0
2016/05/23 22:52:25 :: ifconfig eth0
2016/05/23 22:52:26 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:52:26 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:52:26 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:52:26 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:52:26 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:52:26 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:52:26 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:52:26 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:52:26 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:52:26 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:52:26 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:52:26 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:52:26 :: attempting to set hostname with dhclient
2016/05/23 22:52:26 :: using dhcpcd or another supported client may work better
2016/05/23 22:52:26 :: /sbin/dhclient -v -r eth0
2016/05/23 22:52:28 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:52:28 :: /sbin/ip route flush dev eth0
2016/05/23 22:52:28 :: ifconfig eth0 down
2016/05/23 22:52:28 :: ifconfig eth0 up
2016/05/23 22:52:28 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:52:28 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:52:28 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:52:28 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:52:28 :: wpa_cli -i eth0 terminate
2016/05/23 22:52:28 :: Forced disconnect on
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:52:28 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:52:28 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:52:28 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 22:52:28 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 22:52:28 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 22:52:28 :: attempting to set hostname with dhclient
2016/05/23 22:52:28 :: using dhcpcd or another supported client may work better
2016/05/23 22:52:28 :: /sbin/dhclient -v -r eth0
2016/05/23 22:52:28 :: ifconfig eth0 0.0.0.0 
2016/05/23 22:52:28 :: /sbin/ip route flush dev eth0
2016/05/23 22:52:28 :: ifconfig eth0 down
2016/05/23 22:52:29 :: ifconfig eth0 up
2016/05/23 22:52:29 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 22:52:29 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 22:52:29 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 22:52:29 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 22:52:29 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 22:52:29 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 22:52:29 :: wpa_cli -i eth0 terminate
2016/05/23 22:52:29 :: ifconfig eth0
2016/05/23 22:52:31 :: ifconfig eth0
2016/05/23 22:52:33 :: ifconfig eth0
2016/05/23 22:52:35 :: ifconfig eth0
2016/05/23 22:52:37 :: ifconfig eth0
2016/05/23 22:52:39 :: ifconfig eth0
2016/05/23 22:52:41 :: ifconfig eth0
2016/05/23 22:52:43 :: ifconfig eth0
2016/05/23 22:52:45 :: ifconfig eth0
2016/05/23 22:52:47 :: ifconfig eth0
2016/05/23 22:52:49 :: ifconfig eth0
2016/05/23 22:52:51 :: ifconfig eth0
2016/05/23 22:52:53 :: ifconfig eth0
2016/05/23 22:52:56 :: ifconfig eth0
2016/05/23 22:52:58 :: ifconfig eth0
2016/05/23 22:53:00 :: ifconfig eth0
2016/05/23 22:53:02 :: ifconfig eth0
2016/05/23 22:53:04 :: ifconfig eth0
2016/05/23 22:53:06 :: ifconfig eth0
2016/05/23 22:53:08 :: ifconfig eth0
2016/05/23 22:53:11 :: ifconfig eth0
2016/05/23 22:53:13 :: ifconfig eth0
2016/05/23 22:53:15 :: ifconfig eth0
2016/05/23 22:53:17 :: ifconfig eth0
2016/05/23 22:53:19 :: ifconfig eth0
2016/05/23 22:53:21 :: ifconfig eth0
2016/05/23 22:53:23 :: ifconfig eth0
2016/05/23 22:53:25 :: ifconfig eth0
2016/05/23 22:53:27 :: ifconfig eth0
2016/05/23 22:53:30 :: ifconfig eth0
2016/05/23 22:53:32 :: ifconfig eth0
2016/05/23 22:53:34 :: ifconfig eth0
2016/05/23 22:53:36 :: ifconfig eth0
2016/05/23 22:53:38 :: ifconfig eth0
2016/05/23 22:53:40 :: ifconfig eth0
2016/05/23 22:53:42 :: ifconfig eth0
2016/05/23 22:53:44 :: ifconfig eth0
2016/05/23 22:53:46 :: ifconfig eth0
2016/05/23 22:53:48 :: ifconfig eth0
2016/05/23 22:53:50 :: ifconfig eth0
2016/05/23 22:53:52 :: ifconfig eth0
2016/05/23 22:53:54 :: ifconfig eth0
2016/05/23 22:53:56 :: ifconfig eth0
2016/05/23 22:53:58 :: ifconfig eth0
2016/05/23 22:54:00 :: ifconfig eth0
2016/05/23 22:54:02 :: ifconfig eth0
2016/05/23 22:54:04 :: ifconfig eth0
2016/05/23 22:54:06 :: ifconfig eth0
2016/05/23 22:54:08 :: ifconfig eth0
2016/05/23 22:54:10 :: ifconfig eth0
2016/05/23 22:54:13 :: ifconfig eth0
2016/05/23 22:54:15 :: ifconfig eth0
2016/05/23 22:54:17 :: ifconfig eth0
2016/05/23 22:54:19 :: ifconfig eth0
2016/05/23 22:54:21 :: ifconfig eth0
2016/05/23 22:54:23 :: ifconfig eth0
2016/05/23 22:54:25 :: ifconfig eth0
2016/05/23 22:54:27 :: ifconfig eth0
2016/05/23 22:54:29 :: ifconfig eth0
2016/05/23 22:54:31 :: ifconfig eth0
2016/05/23 22:54:33 :: ifconfig eth0
2016/05/23 22:54:35 :: ifconfig eth0
2016/05/23 22:54:37 :: ifconfig eth0
2016/05/23 22:54:39 :: ifconfig eth0
2016/05/23 22:54:41 :: ifconfig eth0
2016/05/23 22:54:43 :: ifconfig eth0
2016/05/23 22:54:45 :: ifconfig eth0
2016/05/23 22:54:47 :: ifconfig eth0
2016/05/23 22:54:49 :: ifconfig eth0
2016/05/23 22:54:51 :: ifconfig eth0
2016/05/23 22:54:53 :: ifconfig eth0
2016/05/23 22:54:55 :: ifconfig eth0
2016/05/23 22:54:57 :: ifconfig eth0
2016/05/23 22:55:00 :: ifconfig eth0
2016/05/23 22:55:02 :: ifconfig eth0
2016/05/23 22:55:04 :: ifconfig eth0
2016/05/23 22:55:06 :: ifconfig eth0
2016/05/23 22:55:08 :: ifconfig eth0
2016/05/23 22:55:10 :: ifconfig eth0
2016/05/23 22:55:12 :: ifconfig eth0
2016/05/23 22:55:14 :: ifconfig eth0
2016/05/23 22:55:16 :: ifconfig eth0
2016/05/23 22:55:18 :: ifconfig eth0
2016/05/23 22:55:20 :: ifconfig eth0
2016/05/23 22:55:22 :: ifconfig eth0
2016/05/23 22:55:24 :: ifconfig eth0
2016/05/23 22:55:26 :: ifconfig eth0
2016/05/23 22:55:28 :: ifconfig eth0
2016/05/23 22:55:30 :: ifconfig eth0
2016/05/23 22:55:32 :: ifconfig eth0
2016/05/23 22:55:34 :: ifconfig eth0
2016/05/23 22:55:36 :: ifconfig eth0
2016/05/23 22:55:38 :: ifconfig eth0
2016/05/23 22:55:40 :: ifconfig eth0
2016/05/23 22:55:42 :: ifconfig eth0
2016/05/23 22:55:44 :: ifconfig eth0
2016/05/23 22:55:46 :: ifconfig eth0
2016/05/23 22:55:48 :: ifconfig eth0
2016/05/23 22:55:50 :: ifconfig eth0
2016/05/23 22:55:52 :: ifconfig eth0
2016/05/23 22:55:54 :: ifconfig eth0
2016/05/23 22:55:56 :: ifconfig eth0
2016/05/23 22:55:58 :: ifconfig eth0
2016/05/23 22:56:00 :: ifconfig eth0
2016/05/23 22:56:02 :: ifconfig eth0
2016/05/23 22:56:04 :: ifconfig eth0
2016/05/23 22:56:06 :: ifconfig eth0
2016/05/23 22:56:08 :: ifconfig eth0
2016/05/23 22:56:10 :: ifconfig eth0
2016/05/23 22:56:12 :: ifconfig eth0
2016/05/23 22:56:14 :: ifconfig eth0
2016/05/23 22:56:16 :: ifconfig eth0
2016/05/23 22:56:18 :: ifconfig eth0
2016/05/23 22:56:20 :: ifconfig eth0
2016/05/23 22:56:22 :: ifconfig eth0
2016/05/23 22:56:24 :: ifconfig eth0
2016/05/23 22:56:26 :: ifconfig eth0
2016/05/23 22:56:28 :: ifconfig eth0
2016/05/23 22:56:30 :: ifconfig eth0
2016/05/23 22:56:32 :: ifconfig eth0
2016/05/23 22:56:34 :: ifconfig eth0
2016/05/23 22:56:36 :: ifconfig eth0
2016/05/23 22:56:38 :: ifconfig eth0
2016/05/23 22:56:40 :: ifconfig eth0
2016/05/23 22:56:42 :: ifconfig eth0
2016/05/23 22:56:44 :: ifconfig eth0
2016/05/23 22:56:46 :: ifconfig eth0
2016/05/23 22:56:48 :: ifconfig eth0
2016/05/23 22:56:50 :: ifconfig eth0
2016/05/23 22:56:52 :: ifconfig eth0
2016/05/23 22:56:54 :: ifconfig eth0
2016/05/23 22:56:57 :: ifconfig eth0
2016/05/23 22:56:59 :: ifconfig eth0
2016/05/23 22:57:01 :: ifconfig eth0
2016/05/23 22:57:03 :: ifconfig eth0
2016/05/23 22:57:05 :: ifconfig eth0
2016/05/23 22:57:07 :: ifconfig eth0
2016/05/23 22:57:09 :: ifconfig eth0
2016/05/23 22:57:11 :: ifconfig eth0
2016/05/23 22:57:13 :: ifconfig eth0
2016/05/23 22:57:15 :: ifconfig eth0
2016/05/23 22:57:17 :: ifconfig eth0
2016/05/23 22:57:19 :: ifconfig eth0
2016/05/23 22:57:21 :: ifconfig eth0
2016/05/23 22:57:23 :: ifconfig eth0
2016/05/23 22:57:25 :: ifconfig eth0
2016/05/23 22:57:27 :: ifconfig eth0
2016/05/23 22:57:29 :: ifconfig eth0
2016/05/23 22:57:31 :: ifconfig eth0
2016/05/23 22:57:33 :: ifconfig eth0
2016/05/23 22:57:35 :: ifconfig eth0
2016/05/23 22:57:37 :: ifconfig eth0
2016/05/23 22:57:39 :: ifconfig eth0
2016/05/23 22:57:41 :: ifconfig eth0
2016/05/23 22:57:43 :: ifconfig eth0
2016/05/23 22:57:46 :: ifconfig eth0
2016/05/23 22:57:48 :: ifconfig eth0
2016/05/23 22:57:50 :: ifconfig eth0
2016/05/23 22:57:52 :: ifconfig eth0
2016/05/23 22:57:54 :: ifconfig eth0
2016/05/23 22:57:56 :: ifconfig eth0
2016/05/23 22:57:58 :: ifconfig eth0
2016/05/23 22:58:00 :: ifconfig eth0
2016/05/23 22:58:02 :: ifconfig eth0
2016/05/23 22:58:04 :: ifconfig eth0
2016/05/23 22:58:07 :: ifconfig eth0
2016/05/23 22:58:09 :: ifconfig eth0
2016/05/23 22:58:11 :: ifconfig eth0
2016/05/23 22:58:13 :: ifconfig eth0
2016/05/23 22:58:16 :: ifconfig eth0
2016/05/23 22:58:18 :: ifconfig eth0
2016/05/23 22:58:20 :: ifconfig eth0
2016/05/23 22:58:22 :: ifconfig eth0
2016/05/23 22:58:24 :: ifconfig eth0
2016/05/23 22:58:26 :: ifconfig eth0
2016/05/23 22:58:28 :: ifconfig eth0
2016/05/23 22:58:30 :: ifconfig eth0
2016/05/23 22:58:32 :: ifconfig eth0
2016/05/23 22:58:34 :: ifconfig eth0
2016/05/23 22:58:37 :: ifconfig eth0
2016/05/23 22:58:39 :: ifconfig eth0
2016/05/23 22:58:41 :: ifconfig eth0
2016/05/23 22:58:43 :: ifconfig eth0
2016/05/23 22:58:45 :: ifconfig eth0
2016/05/23 22:58:48 :: ifconfig eth0
2016/05/23 22:58:50 :: ifconfig eth0
2016/05/23 22:58:52 :: ifconfig eth0
2016/05/23 22:58:54 :: ifconfig eth0
2016/05/23 22:58:56 :: ifconfig eth0
2016/05/23 22:58:58 :: ifconfig eth0
2016/05/23 22:59:00 :: ifconfig eth0
2016/05/23 22:59:02 :: ifconfig eth0
2016/05/23 22:59:04 :: ifconfig eth0
2016/05/23 22:59:06 :: ifconfig eth0
2016/05/23 22:59:08 :: ifconfig eth0
2016/05/23 22:59:10 :: ifconfig eth0
2016/05/23 22:59:12 :: ifconfig eth0
2016/05/23 22:59:14 :: ifconfig eth0
2016/05/23 22:59:16 :: ifconfig eth0
2016/05/23 22:59:18 :: ifconfig eth0
2016/05/23 22:59:20 :: ifconfig eth0
2016/05/23 22:59:22 :: ifconfig eth0
2016/05/23 22:59:24 :: ifconfig eth0
2016/05/23 22:59:26 :: ifconfig eth0
2016/05/23 22:59:28 :: ifconfig eth0
2016/05/23 22:59:30 :: ifconfig eth0
2016/05/23 22:59:32 :: ifconfig eth0
2016/05/23 22:59:34 :: ifconfig eth0
2016/05/23 22:59:36 :: ifconfig eth0
2016/05/23 22:59:38 :: ifconfig eth0
2016/05/23 22:59:40 :: ifconfig eth0
2016/05/23 22:59:42 :: ifconfig eth0
2016/05/23 22:59:44 :: ifconfig eth0
2016/05/23 22:59:46 :: ifconfig eth0
2016/05/23 22:59:48 :: ifconfig eth0
2016/05/23 22:59:50 :: ifconfig eth0
2016/05/23 22:59:52 :: ifconfig eth0
2016/05/23 22:59:54 :: ifconfig eth0
2016/05/23 22:59:56 :: ifconfig eth0
2016/05/23 22:59:58 :: ifconfig eth0
2016/05/23 23:00:00 :: ifconfig eth0
2016/05/23 23:00:02 :: ifconfig eth0
2016/05/23 23:00:04 :: ifconfig eth0
2016/05/23 23:00:06 :: ifconfig eth0
2016/05/23 23:00:08 :: ifconfig eth0
2016/05/23 23:00:10 :: ifconfig eth0
2016/05/23 23:00:12 :: ifconfig eth0
2016/05/23 23:00:14 :: ifconfig eth0
2016/05/23 23:00:16 :: ifconfig eth0
2016/05/23 23:00:19 :: ifconfig eth0
2016/05/23 23:00:21 :: ifconfig eth0
2016/05/23 23:00:23 :: ifconfig eth0
2016/05/23 23:00:25 :: ifconfig eth0
2016/05/23 23:00:27 :: ifconfig eth0
2016/05/23 23:00:29 :: ifconfig eth0
2016/05/23 23:00:31 :: ifconfig eth0
2016/05/23 23:00:33 :: ifconfig eth0
2016/05/23 23:00:35 :: ifconfig eth0
2016/05/23 23:00:37 :: ifconfig eth0
2016/05/23 23:00:39 :: ifconfig eth0
2016/05/23 23:00:41 :: ifconfig eth0
2016/05/23 23:00:44 :: ifconfig eth0
2016/05/23 23:00:46 :: ifconfig eth0
2016/05/23 23:00:48 :: ifconfig eth0
2016/05/23 23:00:50 :: ifconfig eth0
2016/05/23 23:00:52 :: ifconfig eth0
2016/05/23 23:00:54 :: ifconfig eth0
2016/05/23 23:00:56 :: ifconfig eth0
2016/05/23 23:00:58 :: ifconfig eth0
2016/05/23 23:01:00 :: ifconfig eth0
2016/05/23 23:01:02 :: ifconfig eth0
2016/05/23 23:01:04 :: ifconfig eth0
2016/05/23 23:01:06 :: ifconfig eth0
2016/05/23 23:01:08 :: ifconfig eth0
2016/05/23 23:01:10 :: ifconfig eth0
2016/05/23 23:01:12 :: ifconfig eth0
2016/05/23 23:01:14 :: ifconfig eth0
2016/05/23 23:01:16 :: ifconfig eth0
2016/05/23 23:01:18 :: ifconfig eth0
2016/05/23 23:01:20 :: ifconfig eth0
2016/05/23 23:01:22 :: ifconfig eth0
2016/05/23 23:01:24 :: ifconfig eth0
2016/05/23 23:01:26 :: ifconfig eth0
2016/05/23 23:01:29 :: ifconfig eth0
2016/05/23 23:01:31 :: ifconfig eth0
2016/05/23 23:01:33 :: ifconfig eth0
2016/05/23 23:01:35 :: ifconfig eth0
2016/05/23 23:01:37 :: ifconfig eth0
2016/05/23 23:01:39 :: ifconfig eth0
2016/05/23 23:01:41 :: ifconfig eth0
2016/05/23 23:01:43 :: ifconfig eth0
2016/05/23 23:01:45 :: ifconfig eth0
2016/05/23 23:01:47 :: ifconfig eth0
2016/05/23 23:01:49 :: ifconfig eth0
2016/05/23 23:01:51 :: ifconfig eth0
2016/05/23 23:01:53 :: ifconfig eth0
2016/05/23 23:01:55 :: ifconfig eth0
2016/05/23 23:01:57 :: ifconfig eth0
2016/05/23 23:02:00 :: ifconfig eth0
2016/05/23 23:02:02 :: ifconfig eth0
2016/05/23 23:02:04 :: ifconfig eth0
2016/05/23 23:02:06 :: ifconfig eth0
2016/05/23 23:02:08 :: ifconfig eth0
2016/05/23 23:02:10 :: ifconfig eth0
2016/05/23 23:02:12 :: ifconfig eth0
2016/05/23 23:02:14 :: ifconfig eth0
2016/05/23 23:02:16 :: ifconfig eth0
2016/05/23 23:02:18 :: ifconfig eth0
2016/05/23 23:02:20 :: ifconfig eth0
2016/05/23 23:02:22 :: ifconfig eth0
2016/05/23 23:02:24 :: ifconfig eth0
2016/05/23 23:02:26 :: ifconfig eth0
2016/05/23 23:02:28 :: ifconfig eth0
2016/05/23 23:02:30 :: ifconfig eth0
2016/05/23 23:02:32 :: ifconfig eth0
2016/05/23 23:02:34 :: ifconfig eth0
2016/05/23 23:02:36 :: ifconfig eth0
2016/05/23 23:02:38 :: ifconfig eth0
2016/05/23 23:02:40 :: ifconfig eth0
2016/05/23 23:02:43 :: ifconfig eth0
2016/05/23 23:02:45 :: ifconfig eth0
2016/05/23 23:02:47 :: ifconfig eth0
2016/05/23 23:02:49 :: ifconfig eth0
2016/05/23 23:02:51 :: ifconfig eth0
2016/05/23 23:02:54 :: ifconfig eth0
2016/05/23 23:02:56 :: ifconfig eth0
2016/05/23 23:02:58 :: ifconfig eth0
2016/05/23 23:03:00 :: ifconfig eth0
2016/05/23 23:03:02 :: ifconfig eth0
2016/05/23 23:03:04 :: ifconfig eth0
2016/05/23 23:03:06 :: ifconfig eth0
2016/05/23 23:03:08 :: ifconfig eth0
2016/05/23 23:03:10 :: ifconfig eth0
2016/05/23 23:03:12 :: ifconfig eth0
2016/05/23 23:03:14 :: ifconfig eth0
2016/05/23 23:03:17 :: ifconfig eth0
2016/05/23 23:03:19 :: ifconfig eth0
2016/05/23 23:03:21 :: ifconfig eth0
2016/05/23 23:03:23 :: ifconfig eth0
2016/05/23 23:03:25 :: ifconfig eth0
2016/05/23 23:03:27 :: ifconfig eth0
2016/05/23 23:03:29 :: ifconfig eth0
2016/05/23 23:03:31 :: ifconfig eth0
2016/05/23 23:03:33 :: ifconfig eth0
2016/05/23 23:03:35 :: ifconfig eth0
2016/05/23 23:03:37 :: ifconfig eth0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:03:37 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:03:37 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:03:37 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:03:37 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:03:37 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:03:37 :: attempting to set hostname with dhclient
2016/05/23 23:03:37 :: using dhcpcd or another supported client may work better
2016/05/23 23:03:37 :: /sbin/dhclient -v -r eth0
2016/05/23 23:03:38 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:03:38 :: /sbin/ip route flush dev eth0
2016/05/23 23:03:38 :: ifconfig eth0 down
2016/05/23 23:03:38 :: ifconfig eth0 up
2016/05/23 23:03:38 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:03:38 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:03:38 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:03:38 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:03:38 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:03:38 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:03:38 :: wpa_cli -i eth0 terminate
2016/05/23 23:03:38 :: found lastused in configuration True
2016/05/23 23:03:38 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 23:03:38 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 23:03:38 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 23:03:38 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 23:03:38 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 23:03:38 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 23:03:38 :: Putting interface down
2016/05/23 23:03:38 :: ifconfig eth0 down
2016/05/23 23:03:38 :: Releasing DHCP leases...
2016/05/23 23:03:38 :: attempting to set hostname with dhclient
2016/05/23 23:03:38 :: using dhcpcd or another supported client may work better
2016/05/23 23:03:38 :: /sbin/dhclient -v -r eth0
2016/05/23 23:03:38 :: Setting false IP...
2016/05/23 23:03:38 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:03:38 :: Stopping wpa_supplicant
2016/05/23 23:03:38 :: wpa_cli -i eth0 terminate
2016/05/23 23:03:38 :: Flushing the routing table...
2016/05/23 23:03:38 :: /sbin/ip route flush dev eth0
2016/05/23 23:03:38 :: Putting interface up...
2016/05/23 23:03:38 :: ifconfig eth0 up
2016/05/23 23:03:40 :: Running DHCP with hostname noahlub
2016/05/23 23:03:40 :: attempting to set hostname with dhclient
2016/05/23 23:03:40 :: using dhcpcd or another supported client may work better
2016/05/23 23:03:40 :: /sbin/dhclient -v eth0
2016/05/23 23:03:40 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 23:03:40 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 23:03:40 :: All rights reserved.
2016/05/23 23:03:40 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 23:03:40 :: 
2016/05/23 23:03:41 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 23:03:41 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 23:03:41 :: Sending on   Socket/fallback
2016/05/23 23:03:41 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xd0f2f30a)
2016/05/23 23:03:44 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0xd0f2f30a)
2016/05/23 23:03:44 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0xaf3f2d0)
2016/05/23 23:03:44 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 23:03:44 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 23:03:45 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 23:03:45 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 23:03:45 :: bound to 162.228.104.207 -- renewal in 253 seconds.
2016/05/23 23:03:45 :: DHCP connection successful
2016/05/23 23:03:45 :: Setting DNS : 8.8.8.8
2016/05/23 23:03:45 :: Setting DNS : 8.8.4.4
2016/05/23 23:03:45 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 23:03:45 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 23:03:45 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 23:03:45 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 23:03:45 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 23:03:45 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 23:03:49 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 23:03:49 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 23:03:49 :: Connecting thread exiting.
2016/05/23 23:03:49 :: ifconfig eth0
2016/05/23 23:03:49 :: IP Address is: 162.228.104.207
2016/05/23 23:03:49 :: Sending connection attempt result success
2016/05/23 23:03:51 :: ifconfig eth0
2016/05/23 23:03:53 :: ifconfig eth0
2016/05/23 23:03:55 :: ifconfig eth0
2016/05/23 23:03:57 :: ifconfig eth0
2016/05/23 23:03:59 :: ifconfig eth0
2016/05/23 23:04:01 :: ifconfig eth0
2016/05/23 23:04:03 :: ifconfig eth0
2016/05/23 23:04:05 :: ifconfig eth0
2016/05/23 23:04:07 :: ifconfig eth0
2016/05/23 23:04:09 :: ifconfig eth0
2016/05/23 23:04:11 :: ifconfig eth0
2016/05/23 23:04:13 :: ifconfig eth0
2016/05/23 23:04:15 :: ifconfig eth0
2016/05/23 23:04:17 :: ifconfig eth0
2016/05/23 23:04:19 :: ifconfig eth0
2016/05/23 23:04:21 :: ifconfig eth0
2016/05/23 23:04:23 :: ifconfig eth0
2016/05/23 23:04:25 :: ifconfig eth0
2016/05/23 23:04:28 :: ifconfig eth0
2016/05/23 23:04:30 :: ifconfig eth0
2016/05/23 23:04:32 :: ifconfig eth0
2016/05/23 23:04:34 :: ifconfig eth0
2016/05/23 23:04:36 :: ifconfig eth0
2016/05/23 23:04:38 :: ifconfig eth0
2016/05/23 23:04:40 :: ifconfig eth0
2016/05/23 23:04:42 :: ifconfig eth0
2016/05/23 23:04:44 :: ifconfig eth0
2016/05/23 23:04:46 :: ifconfig eth0
2016/05/23 23:04:48 :: ifconfig eth0
2016/05/23 23:04:50 :: ifconfig eth0
2016/05/23 23:04:52 :: ifconfig eth0
2016/05/23 23:04:54 :: ifconfig eth0
2016/05/23 23:04:55 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:04:55 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:04:55 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:04:55 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:04:55 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:04:55 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:04:55 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:04:55 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:04:55 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:04:55 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:04:55 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:04:55 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:04:55 :: attempting to set hostname with dhclient
2016/05/23 23:04:55 :: using dhcpcd or another supported client may work better
2016/05/23 23:04:55 :: /sbin/dhclient -v -r eth0
2016/05/23 23:04:56 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:04:56 :: /sbin/ip route flush dev eth0
2016/05/23 23:04:56 :: ifconfig eth0 down
2016/05/23 23:04:56 :: ifconfig eth0 up
2016/05/23 23:04:57 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:04:57 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:04:57 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:04:57 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:04:57 :: wpa_cli -i eth0 terminate
2016/05/23 23:04:57 :: Forced disconnect on
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:04:57 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:04:57 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:04:57 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:04:57 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:04:57 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:04:57 :: attempting to set hostname with dhclient
2016/05/23 23:04:57 :: using dhcpcd or another supported client may work better
2016/05/23 23:04:57 :: /sbin/dhclient -v -r eth0
2016/05/23 23:04:57 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:04:57 :: /sbin/ip route flush dev eth0
2016/05/23 23:04:57 :: ifconfig eth0 down
2016/05/23 23:04:57 :: ifconfig eth0 up
2016/05/23 23:04:57 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:04:58 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:04:58 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:04:58 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:04:58 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:04:58 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:04:58 :: wpa_cli -i eth0 terminate
2016/05/23 23:04:58 :: ifconfig eth0
2016/05/23 23:05:00 :: ifconfig eth0
2016/05/23 23:05:03 :: ifconfig eth0
2016/05/23 23:05:05 :: ifconfig eth0
2016/05/23 23:05:07 :: ifconfig eth0
2016/05/23 23:05:09 :: ifconfig eth0
2016/05/23 23:05:11 :: ifconfig eth0
2016/05/23 23:05:13 :: ifconfig eth0
2016/05/23 23:05:15 :: ifconfig eth0
2016/05/23 23:05:17 :: ifconfig eth0
2016/05/23 23:05:19 :: ifconfig eth0
2016/05/23 23:05:22 :: ifconfig eth0
2016/05/23 23:05:24 :: ifconfig eth0
2016/05/23 23:05:26 :: ifconfig eth0
2016/05/23 23:05:28 :: ifconfig eth0
2016/05/23 23:05:30 :: ifconfig eth0
2016/05/23 23:05:32 :: ifconfig eth0
2016/05/23 23:05:34 :: ifconfig eth0
2016/05/23 23:05:36 :: ifconfig eth0
2016/05/23 23:05:38 :: ifconfig eth0
2016/05/23 23:05:40 :: ifconfig eth0
2016/05/23 23:05:42 :: ifconfig eth0
2016/05/23 23:05:44 :: ifconfig eth0
2016/05/23 23:05:46 :: ifconfig eth0
2016/05/23 23:05:48 :: ifconfig eth0
2016/05/23 23:05:50 :: ifconfig eth0
2016/05/23 23:05:52 :: ifconfig eth0
2016/05/23 23:05:54 :: ifconfig eth0
2016/05/23 23:05:56 :: ifconfig eth0
2016/05/23 23:05:58 :: ifconfig eth0
2016/05/23 23:06:00 :: ifconfig eth0
2016/05/23 23:06:02 :: ifconfig eth0
2016/05/23 23:06:04 :: ifconfig eth0
2016/05/23 23:06:06 :: ifconfig eth0
2016/05/23 23:06:08 :: ifconfig eth0
2016/05/23 23:06:10 :: ifconfig eth0
2016/05/23 23:06:12 :: ifconfig eth0
2016/05/23 23:06:14 :: ifconfig eth0
2016/05/23 23:06:16 :: ifconfig eth0
2016/05/23 23:06:18 :: ifconfig eth0
2016/05/23 23:06:20 :: ifconfig eth0
2016/05/23 23:06:22 :: ifconfig eth0
2016/05/23 23:06:24 :: ifconfig eth0
2016/05/23 23:06:26 :: ifconfig eth0
2016/05/23 23:06:28 :: ifconfig eth0
2016/05/23 23:06:30 :: ifconfig eth0
2016/05/23 23:06:33 :: ifconfig eth0
2016/05/23 23:06:35 :: ifconfig eth0
2016/05/23 23:06:37 :: ifconfig eth0
2016/05/23 23:06:39 :: ifconfig eth0
2016/05/23 23:06:41 :: ifconfig eth0
2016/05/23 23:06:43 :: ifconfig eth0
2016/05/23 23:06:45 :: ifconfig eth0
2016/05/23 23:06:47 :: ifconfig eth0
2016/05/23 23:06:49 :: ifconfig eth0
2016/05/23 23:06:51 :: ifconfig eth0
2016/05/23 23:06:53 :: ifconfig eth0
2016/05/23 23:06:55 :: ifconfig eth0
2016/05/23 23:06:57 :: ifconfig eth0
2016/05/23 23:06:59 :: ifconfig eth0
2016/05/23 23:07:01 :: ifconfig eth0
2016/05/23 23:07:03 :: ifconfig eth0
2016/05/23 23:07:05 :: ifconfig eth0
2016/05/23 23:07:07 :: ifconfig eth0
2016/05/23 23:07:09 :: ifconfig eth0
2016/05/23 23:07:11 :: ifconfig eth0
2016/05/23 23:07:13 :: ifconfig eth0
2016/05/23 23:07:15 :: ifconfig eth0
2016/05/23 23:07:17 :: ifconfig eth0
2016/05/23 23:07:19 :: ifconfig eth0
2016/05/23 23:07:21 :: ifconfig eth0
2016/05/23 23:07:23 :: ifconfig eth0
2016/05/23 23:07:25 :: ifconfig eth0
2016/05/23 23:07:27 :: ifconfig eth0
2016/05/23 23:07:29 :: ifconfig eth0
2016/05/23 23:07:31 :: ifconfig eth0
2016/05/23 23:07:33 :: ifconfig eth0
2016/05/23 23:07:35 :: ifconfig eth0
2016/05/23 23:07:38 :: ifconfig eth0
2016/05/23 23:07:40 :: ifconfig eth0
2016/05/23 23:07:42 :: ifconfig eth0
2016/05/23 23:07:44 :: ifconfig eth0
2016/05/23 23:07:46 :: ifconfig eth0
2016/05/23 23:07:49 :: ifconfig eth0
2016/05/23 23:07:51 :: ifconfig eth0
2016/05/23 23:07:53 :: ifconfig eth0
2016/05/23 23:07:55 :: ifconfig eth0
2016/05/23 23:07:57 :: ifconfig eth0
2016/05/23 23:07:59 :: ifconfig eth0
2016/05/23 23:08:01 :: ifconfig eth0
2016/05/23 23:08:03 :: ifconfig eth0
2016/05/23 23:08:05 :: ifconfig eth0
2016/05/23 23:08:07 :: ifconfig eth0
2016/05/23 23:08:09 :: ifconfig eth0
2016/05/23 23:08:11 :: ifconfig eth0
2016/05/23 23:08:13 :: ifconfig eth0
2016/05/23 23:08:15 :: ifconfig eth0
2016/05/23 23:08:17 :: ifconfig eth0
2016/05/23 23:08:19 :: ifconfig eth0
2016/05/23 23:08:21 :: ifconfig eth0
2016/05/23 23:08:24 :: ifconfig eth0
2016/05/23 23:08:26 :: ifconfig eth0
2016/05/23 23:08:28 :: ifconfig eth0
2016/05/23 23:08:30 :: ifconfig eth0
2016/05/23 23:08:32 :: ifconfig eth0
2016/05/23 23:08:32 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:08:32 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:08:32 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:08:32 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:08:32 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:08:32 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:08:32 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:08:32 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:08:32 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:08:32 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:08:32 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:08:33 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:08:33 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:08:33 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:08:33 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:08:33 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:08:33 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:08:33 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:08:33 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:08:33 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:08:33 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:08:33 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:08:33 :: attempting to set hostname with dhclient
2016/05/23 23:08:33 :: using dhcpcd or another supported client may work better
2016/05/23 23:08:33 :: /sbin/dhclient -v -r eth0
2016/05/23 23:08:34 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:08:34 :: /sbin/ip route flush dev eth0
2016/05/23 23:08:34 :: ifconfig eth0 down
2016/05/23 23:08:34 :: ifconfig eth0 up
2016/05/23 23:08:34 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:08:34 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:08:34 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:08:34 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:08:34 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:08:35 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:08:35 :: wpa_cli -i eth0 terminate
2016/05/23 23:08:35 :: found lastused in configuration True
2016/05/23 23:08:35 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 23:08:35 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 23:08:35 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 23:08:35 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 23:08:35 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 23:08:35 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 23:08:35 :: Putting interface down
2016/05/23 23:08:35 :: ifconfig eth0 down
2016/05/23 23:08:35 :: Releasing DHCP leases...
2016/05/23 23:08:35 :: attempting to set hostname with dhclient
2016/05/23 23:08:35 :: using dhcpcd or another supported client may work better
2016/05/23 23:08:35 :: /sbin/dhclient -v -r eth0
2016/05/23 23:08:35 :: Setting false IP...
2016/05/23 23:08:35 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:08:35 :: Stopping wpa_supplicant
2016/05/23 23:08:35 :: wpa_cli -i eth0 terminate
2016/05/23 23:08:35 :: Flushing the routing table...
2016/05/23 23:08:35 :: /sbin/ip route flush dev eth0
2016/05/23 23:08:35 :: Putting interface up...
2016/05/23 23:08:35 :: ifconfig eth0 up
2016/05/23 23:08:37 :: Running DHCP with hostname noahlub
2016/05/23 23:08:37 :: attempting to set hostname with dhclient
2016/05/23 23:08:37 :: using dhcpcd or another supported client may work better
2016/05/23 23:08:37 :: /sbin/dhclient -v eth0
2016/05/23 23:08:37 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 23:08:37 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 23:08:37 :: All rights reserved.
2016/05/23 23:08:37 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 23:08:37 :: 
2016/05/23 23:08:37 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 23:08:37 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 23:08:37 :: Sending on   Socket/fallback
2016/05/23 23:08:37 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x66c61129)
2016/05/23 23:08:40 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 (xid=0x66c61129)
2016/05/23 23:08:40 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0x2911c666)
2016/05/23 23:08:40 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 23:08:40 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 23:08:40 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 23:08:40 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 23:08:41 :: bound to 162.228.104.207 -- renewal in 227 seconds.
2016/05/23 23:08:41 :: DHCP connection successful
2016/05/23 23:08:41 :: Setting DNS : 8.8.8.8
2016/05/23 23:08:41 :: Setting DNS : 8.8.4.4
2016/05/23 23:08:41 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 23:08:41 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 23:08:41 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 23:08:41 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 23:08:41 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 23:08:41 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 23:08:45 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 23:08:45 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 23:08:46 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 23:08:46 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 23:08:46 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 23:08:46 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 23:08:46 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 23:08:46 :: Connecting thread exiting.
2016/05/23 23:08:46 :: ifconfig eth0
2016/05/23 23:08:46 :: IP Address is: 162.228.104.207
2016/05/23 23:08:46 :: Sending connection attempt result success
2016/05/23 23:08:48 :: ifconfig eth0
2016/05/23 23:08:50 :: ifconfig eth0
2016/05/23 23:08:52 :: ifconfig eth0
2016/05/23 23:08:54 :: ifconfig eth0
2016/05/23 23:08:56 :: ifconfig eth0
2016/05/23 23:08:58 :: ifconfig eth0
2016/05/23 23:09:00 :: ifconfig eth0
2016/05/23 23:09:02 :: ifconfig eth0
2016/05/23 23:09:04 :: ifconfig eth0
2016/05/23 23:09:06 :: ifconfig eth0
2016/05/23 23:09:08 :: ifconfig eth0
2016/05/23 23:09:10 :: ifconfig eth0
2016/05/23 23:09:12 :: ifconfig eth0
2016/05/23 23:09:14 :: ifconfig eth0
2016/05/23 23:09:16 :: ifconfig eth0
2016/05/23 23:09:19 :: ifconfig eth0
2016/05/23 23:09:21 :: ifconfig eth0
2016/05/23 23:09:23 :: ifconfig eth0
2016/05/23 23:09:25 :: ifconfig eth0
2016/05/23 23:09:27 :: ifconfig eth0
2016/05/23 23:09:29 :: ifconfig eth0
2016/05/23 23:09:31 :: ifconfig eth0
2016/05/23 23:09:33 :: ifconfig eth0
2016/05/23 23:09:36 :: ifconfig eth0
2016/05/23 23:09:38 :: ifconfig eth0
2016/05/23 23:09:40 :: ifconfig eth0
2016/05/23 23:09:42 :: ifconfig eth0
2016/05/23 23:09:44 :: ifconfig eth0
2016/05/23 23:09:46 :: ifconfig eth0
2016/05/23 23:09:48 :: ifconfig eth0
2016/05/23 23:09:50 :: ifconfig eth0
2016/05/23 23:09:52 :: ifconfig eth0
2016/05/23 23:09:54 :: ifconfig eth0
2016/05/23 23:09:56 :: ifconfig eth0
2016/05/23 23:09:58 :: ifconfig eth0
2016/05/23 23:10:00 :: ifconfig eth0
2016/05/23 23:10:02 :: ifconfig eth0
2016/05/23 23:10:04 :: ifconfig eth0
2016/05/23 23:10:06 :: ifconfig eth0
2016/05/23 23:10:08 :: ifconfig eth0
2016/05/23 23:10:10 :: ifconfig eth0
2016/05/23 23:10:12 :: ifconfig eth0
2016/05/23 23:10:14 :: ifconfig eth0
2016/05/23 23:10:16 :: ifconfig eth0
2016/05/23 23:10:19 :: ifconfig eth0
2016/05/23 23:10:21 :: ifconfig eth0
2016/05/23 23:10:23 :: ifconfig eth0
2016/05/23 23:10:25 :: ifconfig eth0
2016/05/23 23:10:27 :: ifconfig eth0
2016/05/23 23:10:29 :: ifconfig eth0
2016/05/23 23:10:31 :: ifconfig eth0
2016/05/23 23:10:32 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:10:32 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:10:32 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:10:32 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:10:32 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:10:32 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:10:32 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:10:32 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:10:32 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:10:32 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:10:32 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:10:32 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:10:32 :: attempting to set hostname with dhclient
2016/05/23 23:10:32 :: using dhcpcd or another supported client may work better
2016/05/23 23:10:32 :: /sbin/dhclient -v -r eth0
2016/05/23 23:10:33 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:10:33 :: /sbin/ip route flush dev eth0
2016/05/23 23:10:33 :: ifconfig eth0 down
2016/05/23 23:10:33 :: ifconfig eth0 up
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:10:34 :: wpa_cli -i eth0 terminate
2016/05/23 23:10:34 :: Forced disconnect on
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:10:34 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:10:34 :: attempting to set hostname with dhclient
2016/05/23 23:10:34 :: using dhcpcd or another supported client may work better
2016/05/23 23:10:34 :: /sbin/dhclient -v -r eth0
2016/05/23 23:10:34 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:10:34 :: /sbin/ip route flush dev eth0
2016/05/23 23:10:34 :: ifconfig eth0 down
2016/05/23 23:10:34 :: ifconfig eth0 up
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:10:34 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:10:34 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:10:34 :: wpa_cli -i eth0 terminate
2016/05/23 23:10:34 :: ifconfig eth0
2016/05/23 23:10:36 :: ifconfig eth0
2016/05/23 23:10:38 :: ifconfig eth0
2016/05/23 23:10:40 :: ifconfig eth0
2016/05/23 23:10:42 :: ifconfig eth0
2016/05/23 23:10:44 :: ifconfig eth0
2016/05/23 23:10:46 :: ifconfig eth0
2016/05/23 23:10:48 :: ifconfig eth0
2016/05/23 23:10:50 :: ifconfig eth0
2016/05/23 23:10:52 :: ifconfig eth0
2016/05/23 23:10:54 :: ifconfig eth0
2016/05/23 23:10:56 :: ifconfig eth0
2016/05/23 23:10:58 :: ifconfig eth0
2016/05/23 23:11:01 :: ifconfig eth0
2016/05/23 23:11:03 :: ifconfig eth0
2016/05/23 23:11:05 :: ifconfig eth0
2016/05/23 23:11:08 :: ifconfig eth0
2016/05/23 23:11:10 :: ifconfig eth0
2016/05/23 23:11:11 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:11:11 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:11:11 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:11:11 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:11:11 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:11:11 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:11:11 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:11:11 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:11:11 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:11:11 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:11:12 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2016/05/23 23:11:12 :: /etc/network/if-down.d/avahi-autoipd returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-down.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:11:12 :: /etc/network/if-down.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-down.d/postfix with params 
2016/05/23 23:11:12 :: /etc/network/if-down.d/postfix returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-down.d/resolvconf with params 
2016/05/23 23:11:12 :: /etc/network/if-down.d/resolvconf returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-down.d/upstart with params 
2016/05/23 23:11:12 :: /etc/network/if-down.d/upstart returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2016/05/23 23:11:12 :: /etc/network/if-down.d/wpasupplicant returned 0
2016/05/23 23:11:12 :: attempting to set hostname with dhclient
2016/05/23 23:11:12 :: using dhcpcd or another supported client may work better
2016/05/23 23:11:12 :: /sbin/dhclient -v -r eth0
2016/05/23 23:11:12 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:11:12 :: /sbin/ip route flush dev eth0
2016/05/23 23:11:12 :: ifconfig eth0 down
2016/05/23 23:11:12 :: ifconfig eth0 up
2016/05/23 23:11:12 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2016/05/23 23:11:12 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2016/05/23 23:11:12 :: /etc/network/if-post-down.d/wireless-tools returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2016/05/23 23:11:12 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2016/05/23 23:11:12 :: wpa_cli -i eth0 terminate
2016/05/23 23:11:12 :: found lastused in configuration True
2016/05/23 23:11:12 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2016/05/23 23:11:12 :: /etc/network/if-pre-up.d/ethtool returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2016/05/23 23:11:12 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2016/05/23 23:11:12 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2016/05/23 23:11:12 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2016/05/23 23:11:12 :: Putting interface down
2016/05/23 23:11:12 :: ifconfig eth0 down
2016/05/23 23:11:13 :: Releasing DHCP leases...
2016/05/23 23:11:13 :: attempting to set hostname with dhclient
2016/05/23 23:11:13 :: using dhcpcd or another supported client may work better
2016/05/23 23:11:13 :: /sbin/dhclient -v -r eth0
2016/05/23 23:11:13 :: Setting false IP...
2016/05/23 23:11:13 :: ifconfig eth0 0.0.0.0 
2016/05/23 23:11:13 :: Stopping wpa_supplicant
2016/05/23 23:11:13 :: wpa_cli -i eth0 terminate
2016/05/23 23:11:13 :: Flushing the routing table...
2016/05/23 23:11:13 :: /sbin/ip route flush dev eth0
2016/05/23 23:11:13 :: Putting interface up...
2016/05/23 23:11:13 :: ifconfig eth0 up
2016/05/23 23:11:15 :: Running DHCP with hostname noahlub
2016/05/23 23:11:15 :: attempting to set hostname with dhclient
2016/05/23 23:11:15 :: using dhcpcd or another supported client may work better
2016/05/23 23:11:15 :: /sbin/dhclient -v eth0
2016/05/23 23:11:15 :: Internet Systems Consortium DHCP Client 4.3.1
2016/05/23 23:11:15 :: Copyright 2004-2014 Internet Systems Consortium.
2016/05/23 23:11:15 :: All rights reserved.
2016/05/23 23:11:15 :: For info, please visit https://www.isc.org/software/dhcp/
2016/05/23 23:11:15 :: 
2016/05/23 23:11:15 :: Listening on LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 23:11:15 :: Sending on   LPF/eth0/d0:50:99:13:1d:4e
2016/05/23 23:11:15 :: Sending on   Socket/fallback
2016/05/23 23:11:15 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xe8db490b)
2016/05/23 23:11:18 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0xe8db490b)
2016/05/23 23:11:18 :: DHCPREQUEST of 162.228.104.207 on eth0 to 255.255.255.255 port 67 (xid=0xb49dbe8)
2016/05/23 23:11:18 :: DHCPOFFER of 162.228.104.207 from 192.168.1.254
2016/05/23 23:11:18 :: DHCPACK of 162.228.104.207 from 192.168.1.254
2016/05/23 23:11:18 :: invoke-rc.d: policy-rc.d denied execution of reload.
2016/05/23 23:11:18 :: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
2016/05/23 23:11:18 :: bound to 162.228.104.207 -- renewal in 233 seconds.
2016/05/23 23:11:18 :: DHCP connection successful
2016/05/23 23:11:18 :: Setting DNS : 8.8.8.8
2016/05/23 23:11:18 :: Setting DNS : 8.8.4.4
2016/05/23 23:11:18 :: ['/sbin/resolvconf', '-a', 'eth0']
2016/05/23 23:11:18 :: Executing /etc/network/if-up.d/000resolvconf with params 
2016/05/23 23:11:18 :: /etc/network/if-up.d/000resolvconf returned 0
2016/05/23 23:11:18 :: Executing /etc/network/if-up.d/00check-network-cable with params 
2016/05/23 23:11:18 :: /etc/network/if-up.d/00check-network-cable returned 2
2016/05/23 23:11:18 :: Executing /etc/network/if-up.d/10check-duplicate-ip with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/10check-duplicate-ip returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/20static-routes with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/20static-routes returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/30check-gateway with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/30check-gateway returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/avahi-autoipd with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/avahi-autoipd returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/avahi-daemon with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/avahi-daemon returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/clamav-freshclam-ifupdown with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/clamav-freshclam-ifupdown returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/ethtool with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/ethtool returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/miredo with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/miredo returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/ntpdate with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/ntpdate returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/openssh-server with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/openssh-server returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/postfix with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/postfix returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/upstart with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/upstart returned 0
2016/05/23 23:11:23 :: Executing /etc/network/if-up.d/wpasupplicant with params 
2016/05/23 23:11:23 :: /etc/network/if-up.d/wpasupplicant returned 0
2016/05/23 23:11:23 :: Connecting thread exiting.
2016/05/23 23:11:23 :: ifconfig eth0
2016/05/23 23:11:23 :: IP Address is: 162.228.104.207
2016/05/23 23:11:23 :: Sending connection attempt result success
2016/05/23 23:11:25 :: ifconfig eth0
2016/05/23 23:11:27 :: ifconfig eth0
2016/05/23 23:11:29 :: ifconfig eth0
2016/05/23 23:11:31 :: ifconfig eth0
2016/05/23 23:11:33 :: ifconfig eth0
2016/05/23 23:11:35 :: ifconfig eth0
2016/05/23 23:11:37 :: ifconfig eth0
2016/05/23 23:11:39 :: ifconfig eth0
2016/05/23 23:11:41 :: ifconfig eth0
2016/05/23 23:11:43 :: ifconfig eth0
2016/05/23 23:11:45 :: ifconfig eth0
2016/05/23 23:11:47 :: ifconfig eth0
2016/05/23 23:11:49 :: ifconfig eth0
2016/05/23 23:11:51 :: ifconfig eth0
2016/05/23 23:11:53 :: ifconfig eth0
2016/05/23 23:11:55 :: ifconfig eth0
2016/05/23 23:11:57 :: ifconfig eth0
2016/05/23 23:11:59 :: ifconfig eth0
2016/05/23 23:12:01 :: ifconfig eth0
2016/05/23 23:12:03 :: ifconfig eth0
2016/05/23 23:12:05 :: ifconfig eth0
2016/05/23 23:12:07 :: ifconfig eth0
2016/05/23 23:12:09 :: ifconfig eth0
2016/05/23 23:12:11 :: ifconfig eth0
2016/05/23 23:12:13 :: ifconfig eth0
2016/05/23 23:12:15 :: ifconfig eth0
2016/05/23 23:12:17 :: ifconfig eth0
2016/05/23 23:12:19 :: ifconfig eth0
2016/05/23 23:12:21 :: ifconfig eth0
2016/05/23 23:12:23 :: ifconfig eth0
2016/05/23 23:12:25 :: ifconfig eth0 [COLOR=#000000]2016/05/23 23:12:28 :: ifconfig eth0[/COLOR]
```

ifconfig -a
```
[COLOR=#000000]eth0      Link encap:Ethernet  HWaddr d0:50:99:13:1d:4e  [/COLOR]          inet addr:162.228.104.207  Bcast:162.228.107.255  Mask:255.255.252.0
          inet6 addr: 2602:30a:2e46:8cf0:d250:99ff:fe13:1d4e/64 Scope:Global
          inet6 addr: fe80::d250:99ff:fe13:1d4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1737 errors:0 dropped:1 overruns:0 frame:0
          TX packets:212228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152080 (152.0 KB)  TX bytes:177527091 (177.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:106733748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106733748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5349343254 (5.3 GB)  TX bytes:5349343254 (5.3 GB)

teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
lspci | grep Eth
```
[COLOR=#000000]03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)[/COLOR]
```

cat /etc/network/interfaces
```
[COLOR=#000000]# interfaces(5) file used by ifup(8) and ifdown(8)[/COLOR]auto eth0
iface eth0 inet dchp
```

---

### Post by lisati on 2016-05-24
Duplicate of [http://ubuntuforums.org/showthread.php?t=2325619](http://ubuntuforums.org/showthread.php?t=2325619) closed

---

