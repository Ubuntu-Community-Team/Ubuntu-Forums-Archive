---
title: "wireless keeps dropping every few minutes"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by dave_le_brun on 2014-08-28
as in the title, my latest wireless problem is that the network keeps dropping and reconnecting every few minutes.  I have installed WICD and TWO extracts from a log file are as below - one from a few days ago, and the second from today.  wireless problems are just a CONSTANT issue for me.  My windows laptop attaches fine.  

2014/08/24 20:15:26 :: iwconfig wlan0
2014/08/24 20:15:31 :: ifconfig eth0
2014/08/24 20:15:31 :: ifconfig wlan0
2014/08/24 20:15:31 :: iwconfig wlan0
2014/08/24 20:15:36 :: ifconfig eth0
2014/08/24 20:15:36 :: ifconfig wlan0
2014/08/24 20:15:36 :: iwconfig wlan0
2014/08/24 20:15:36 :: Forced disconnect on
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/avahi-autoipd returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/resolvconf with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/resolvconf returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/upstart with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/upstart returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/wpasupplicant returned 0
2014/08/24 20:15:36 :: attempting to set hostname with dhclient
2014/08/24 20:15:36 :: using dhcpcd or another supported client may work better
2014/08/24 20:15:36 :: /sbin/dhclient -v -r wlan0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/wlan0/fc:f8:ae:f4:8c:e2
Sending on   LPF/wlan0/fc:f8:ae:f4:8c:e2
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67 (xid=0x17b6f018)
2014/08/24 20:15:36 :: ifconfig wlan0 0.0.0.0 
2014/08/24 20:15:36 :: /sbin/ip route flush dev wlan0
2014/08/24 20:15:36 :: ifconfig wlan0 down
2014/08/24 20:15:36 :: ifconfig wlan0 up
2014/08/24 20:15:36 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2014/08/24 20:15:36 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2014/08/24 20:15:36 :: /etc/network/if-post-down.d/wireless-tools returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2014/08/24 20:15:36 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2014/08/24 20:15:36 :: wpa_cli -i wlan0 terminate
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/avahi-autoipd returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/resolvconf with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/resolvconf returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/upstart with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/upstart returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2014/08/24 20:15:36 :: /etc/network/if-down.d/wpasupplicant returned 0
2014/08/24 20:15:36 :: attempting to set hostname with dhclient
2014/08/24 20:15:36 :: using dhcpcd or another supported client may work better
2014/08/24 20:15:36 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/00:90:f5:f4:1d:9a
Sending on   LPF/eth0/00:90:f5:f4:1d:9a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.3 port 67 (xid=0x1aee8c80)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2365: Failed to send 300 byte long packet over fallback interface.
2014/08/24 20:15:36 :: ifconfig eth0 0.0.0.0 
2014/08/24 20:15:36 :: /sbin/ip route flush dev eth0
2014/08/24 20:15:36 :: ifconfig eth0 down
2014/08/24 20:15:36 :: ifconfig eth0 up
2014/08/24 20:15:36 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2014/08/24 20:15:36 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2014/08/24 20:15:36 :: /etc/network/if-post-down.d/wireless-tools returned 0
2014/08/24 20:15:36 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2014/08/24 20:15:36 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2014/08/24 20:15:36 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2014/08/24 20:15:41 :: ifconfig eth0
2014/08/24 20:15:41 :: ifconfig wlan0
2014/08/24 20:15:41 :: iwconfig wlan0
2014/08/24 20:15:46 :: ifconfig eth0
2014/08/24 20:15:46 :: ifconfig wlan0
2014/08/24 20:15:46 :: iwconfig wlan0
2014/08/24 20:15:51 :: ifconfig eth0


The second extract (from today) is as follows 

2014/08/28 21:40:51 :: GetCurrentNetworkID: Returning -1, current network not found
2014/08/28 21:40:56 :: ifconfig eth0
2014/08/28 21:40:56 :: ifconfig wlan0
2014/08/28 21:40:56 :: iwconfig wlan0
2014/08/28 21:40:56 :: GetCurrentNetworkID: Returning -1, current network not found
2014/08/28 21:41:01 :: ifconfig eth0
2014/08/28 21:41:01 :: ifconfig wlan0
2014/08/28 21:41:01 :: iwconfig wlan0
2014/08/28 21:41:01 :: GetCurrentNetworkID: Returning -1, current network not found
2014/08/28 21:41:06 :: ifconfig eth0
2014/08/28 21:41:06 :: ifconfig wlan0
2014/08/28 21:41:06 :: iwconfig wlan0
2014/08/28 21:41:06 :: GetCurrentNetworkID: Returning -1, current network not found
2014/08/28 21:41:11 :: ifconfig eth0
2014/08/28 21:41:11 :: ifconfig wlan0
2014/08/28 21:41:11 :: iwconfig wlan0
2014/08/28 21:41:11 :: Forced disconnect on
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/avahi-autoipd returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/resolvconf with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/resolvconf returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/upstart with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/upstart returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/wpasupplicant returned 0
2014/08/28 21:41:11 :: attempting to set hostname with dhclient
2014/08/28 21:41:11 :: using dhcpcd or another supported client may work better
2014/08/28 21:41:11 :: /sbin/dhclient -v -r wlan0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/wlan0/fc:f8:ae:f4:8c:e2
Sending on   LPF/wlan0/fc:f8:ae:f4:8c:e2
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67 (xid=0x48cb1dc1)
2014/08/28 21:41:11 :: ifconfig wlan0 0.0.0.0 
2014/08/28 21:41:11 :: /sbin/ip route flush dev wlan0
2014/08/28 21:41:11 :: ifconfig wlan0 down
2014/08/28 21:41:11 :: ifconfig wlan0 up
2014/08/28 21:41:11 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2014/08/28 21:41:11 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2014/08/28 21:41:11 :: /etc/network/if-post-down.d/wireless-tools returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2014/08/28 21:41:11 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2014/08/28 21:41:11 :: wpa_cli -i wlan0 terminate
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/avahi-autoipd returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/resolvconf with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/resolvconf returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/upstart with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/upstart returned 0
2014/08/28 21:41:11 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2014/08/28 21:41:11 :: /etc/network/if-down.d/wpasupplicant returned 0
2014/08/28 21:41:11 :: attempting to set hostname with dhclient
2014/08/28 21:41:11 :: using dhcpcd or another supported client may work better
2014/08/28 21:41:11 :: /sbin/dhclient -v -r eth0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/00:90:f5:f4:1d:9a
Sending on   LPF/eth0/00:90:f5:f4:1d:9a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.3 port 67 (xid=0xc26b084)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2365: Failed to send 300 byte long packet over fallback interface.
2014/08/28 21:41:11 :: ifconfig eth0 0.0.0.0 
2014/08/28 21:41:11 :: /sbin/ip route flush dev eth0
2014/08/28 21:41:11 :: ifconfig eth0 down
2014/08/28 21:41:12 :: ifconfig eth0 up
2014/08/28 21:41:12 :: Executing /etc/network/if-post-down.d/avahi-daemon with params 
2014/08/28 21:41:12 :: /etc/network/if-post-down.d/avahi-daemon returned 0
2014/08/28 21:41:12 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2014/08/28 21:41:12 :: /etc/network/if-post-down.d/wireless-tools returned 0
2014/08/28 21:41:12 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2014/08/28 21:41:12 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2014/08/28 21:41:12 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2014/08/28 21:41:16 :: ifconfig eth0
2014/08/28 21:41:16 :: ifconfig wlan0
2014/08/28 21:41:16 :: GetCurrentNetworkID: Returning -1, current network not found
2014/08/28 21:41:16 :: Autoconnecting...
2014/08/28 21:41:16 :: Starting wireless autoconnect...
2014/08/28 21:41:16 :: No wired connection present, attempting to autoconnect to wireless network
2014/08/28 21:41:16 :: scanning start
2014/08/28 21:41:16 :: ifconfig wlan0 up
2014/08/28 21:41:16 :: iwlist wlan0 scan
2014/08/28 21:41:17 :: scanning done
2014/08/28 21:41:17 :: found 4 networks:
2014/08/28 21:41:17 :: found afterscript in configuration None
2014/08/28 21:41:17 :: found dhcphostname in configuration dave-W65-67SH
2014/08/28 21:41:17 :: found postdisconnectscript in configuration None
2014/08/28 21:41:17 :: found dns_domain in configuration None
2014/08/28 21:41:17 :: found gateway in configuration None
2014/08/28 21:41:17 :: found use_global_dns in configuration False
2014/08/28 21:41:17 :: found ip in configuration None
2014/08/28 21:41:17 :: found beforescript in configuration None
2014/08/28 21:41:17 :: found psk in configuration 652edfae0ced5dad7385be3bd253161b79fd9140528ae272f568cc1b37b9816d
2014/08/28 21:41:17 :: found netmask in configuration None
2014/08/28 21:41:17 :: found key in configuration *****
2014/08/28 21:41:17 :: found usedhcphostname in configuration 0
2014/08/28 21:41:17 :: found predisconnectscript in configuration None
2014/08/28 21:41:17 :: found enctype in configuration wpa2
2014/08/28 21:41:17 :: found dns3 in configuration None
2014/08/28 21:41:17 :: found dns2 in configuration None
2014/08/28 21:41:17 :: found dns1 in configuration None
2014/08/28 21:41:17 :: found use_settings_globally in configuration False
2014/08/28 21:41:17 :: found use_static_dns in configuration False
2014/08/28 21:41:17 :: found automatic in configuration 0
2014/08/28 21:41:17 :: found search_domain in configuration None
2014/08/28 21:41:17 :: found dhcphostname in configuration dave-W65-67SH
2014/08/28 21:41:17 :: found ip in configuration None
2014/08/28 21:41:17 :: found dns_domain in configuration None
2014/08/28 21:41:17 :: found gateway in configuration None
2014/08/28 21:41:17 :: found use_global_dns in configuration 0
2014/08/28 21:41:17 :: found netmask in configuration None
2014/08/28 21:41:17 :: found key in configuration *****
2014/08/28 21:41:17 :: found usedhcphostname in configuration 0
2014/08/28 21:41:17 :: found enctype in configuration wpa2
2014/08/28 21:41:17 :: found dns3 in configuration None
2014/08/28 21:41:17 :: found dns2 in configuration None
2014/08/28 21:41:17 :: found dns1 in configuration None
2014/08/28 21:41:17 :: found use_settings_globally in configuration 0
2014/08/28 21:41:17 :: found use_static_dns in configuration 0
2014/08/28 21:41:17 :: found search_domain in configuration None
2014/08/28 21:41:17 :: found beforescript in configuration None
2014/08/28 21:41:17 :: found afterscript in configuration None
2014/08/28 21:41:17 :: found predisconnectscript in configuration None
2014/08/28 21:41:17 :: found postdisconnectscript in configuration None
2014/08/28 21:41:17 :: Dining_Room has profile
2014/08/28 21:41:17 :: kitchen_adsl has profile
2014/08/28 21:41:17 :: Unable to autoconnect, you'll have to manually connect
2014/08/28 21:41:17 :: iwconfig wlan0
2014/08/28 21:41:21 :: ifconfig eth0
2014/08/28 21:41:21 :: ifconfig wlan0
2014/08/28 21:41:21 :: GetCurrentNetworkID: Returning -1, current network not found
2014/08/28 21:41:21 :: Autoconnecting...
2014/08/28 21:41:21 :: Starting wireless autoconnect...
2014/08/28 21:41:21 :: No wired connection present, attempting to autoconnect to wireless network
2014/08/28 21:41:21 :: scanning start
2014/08/28 21:41:21 :: ifconfig wlan0 up
2014/08/28 21:41:21 :: iwlist wlan0 scan
2014/08/28 21:41:22 :: scanning done
2014/08/28 21:41:22 :: found 4 networks:
2014/08/28 21:41:22 :: found afterscript in configuration None
2014/08/28 21:41:22 :: found dhcphostname in configuration dave-W65-67SH
2014/08/28 21:41:22 :: found postdisconnectscript in configuration None
2014/08/28 21:41:22 :: found dns_domain in configuration None
2014/08/28 21:41:22 :: found gateway in configuration None
2014/08/28 21:41:22 :: found use_global_dns in configuration False
2014/08/28 21:41:22 :: found ip in configuration None
2014/08/28 21:41:22 :: found beforescript in configuration None
2014/08/28 21:41:22 :: found psk in configuration 652edfae0ced5dad7385be3bd253161b79fd9140528ae272f568cc1b37b9816d
2014/08/28 21:41:22 :: found netmask in configuration None
2014/08/28 21:41:22 :: found key in configuration *****
2014/08/28 21:41:22 :: found usedhcphostname in configuration 0
2014/08/28 21:41:22 :: found predisconnectscript in configuration None
2014/08/28 21:41:22 :: found enctype in configuration wpa2
2014/08/28 21:41:22 :: found dns3 in configuration None
2014/08/28 21:41:22 :: found dns2 in configuration None
2014/08/28 21:41:22 :: found dns1 in configuration None
2014/08/28 21:41:22 :: found use_settings_globally in configuration False
2014/08/28 21:41:22 :: found use_static_dns in configuration False
2014/08/28 21:41:22 :: found automatic in configuration 0
2014/08/28 21:41:22 :: found search_domain in configuration None
2014/08/28 21:41:22 :: found dhcphostname in configuration dave-W65-67SH
2014/08/28 21:41:22 :: found ip in configuration None
2014/08/28 21:41:22 :: found dns_domain in configuration None
2014/08/28 21:41:22 :: found gateway in configuration None
2014/08/28 21:41:22 :: found use_global_dns in configuration 0
2014/08/28 21:41:22 :: found netmask in configuration None
2014/08/28 21:41:22 :: found key in configuration *****
2014/08/28 21:41:22 :: found usedhcphostname in configuration 0
2014/08/28 21:41:22 :: found enctype in configuration wpa2
2014/08/28 21:41:22 :: found dns3 in configuration None
2014/08/28 21:41:22 :: found dns2 in configuration None
2014/08/28 21:41:22 :: found dns1 in configuration None
2014/08/28 21:41:22 :: found use_settings_globally in configuration 0
2014/08/28 21:41:22 :: found use_static_dns in configuration 0
2014/08/28 21:41:22 :: found search_domain in configuration None
2014/08/28 21:41:22 :: found beforescript in configuration None
2014/08/28 21:41:22 :: found afterscript in configuration None
2014/08/28 21:41:22 :: found predisconnectscript in configuration None
2014/08/28 21:41:22 :: found postdisconnectscript in configuration None
2014/08/28 21:41:22 :: Dining_Room has profile
2014/08/28 21:41:22 :: kitchen_adsl has profile
2014/08/28 21:41:22 :: Unable to autoconnect, you'll have to manually connect
2014/08/28 21:41:22 :: iwconfig wlan0
2014/08/28 21:41:26 :: ifconfig eth0
2014/08/28 21:41:26 :: ifconfig wlan0
2014/08/28 21:41:26 :: iwconfig wlan0
2014/08/28 21:41:31 :: ifconfig eth0
2014/08/28 21:41:31 :: ifconfig wlan0
2014/08/28 21:41:31 :: iwconfig wlan0
2014/08/28 21:41:36 :: ifconfig eth0
2014/08/28 21:41:36 :: ifconfig wlan0
2014/08/28 21:41:36 :: iwconfig wlan0
2014/08/28 21:41:41 :: ifconfig eth0


I right-clicked the wireless icon (bottom right) and directed the PC to connect to 'dining_room', which it did without trouble.  It has not disconnected since.  

Basically, the system rarely remains attached to any wireless network (I have 4 networks at home, on various channels) for any length of time (but if proving me wrong this evening).  Could someone possibly explain what is happening in the above message streams, so that when they happen next time I am prepared ...
thanks

---

### Post by wildmanne39 on 2014-08-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Click on the wireless script in my signature and follow the directions for running it then post the file here in code tags or attach as a zip file.
Thanks

---

### Post by dave_le_brun on 2014-09-01
Good point.  Attached is a tar file as requested.  No joy finding clues elsewhere.
regards
Dave

---

