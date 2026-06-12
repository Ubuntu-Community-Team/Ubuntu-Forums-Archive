---
title: "[SOLVED] Trouble with wpc54G v2"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by eheldreth on 2007-12-14
I just installed Ubuntu 7.10 on my Dell Inspiron 5100.  Everything is working fine including the internal wired network card except for my wpc54g.  I installed ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk.  I then downloaded the XP drivers from Linksys.com.  I went to System->Administration->Windows Wireless Drivers and installed the XP drivers.  The card appears to be recognized and it sees both my routers in the connection manager.  When I click on one of the routers it attempts to connect but fails before it receives an address from DHCP.  I have deactivated encryption until I get this problem worked out and know the card is working.  I have also tested the card under Windows XP and it works fine.    I would appreciate any help you can give me.

> **ndiswrapper -l gives the following:**
lsbcmnds : driver installed
lstinds : driver installed
        device (104C:9066) present (alternate driver: acx)

> **sudo lshw -C network gives the following:**
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:39:3c:e3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.110 latency=32 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:66:b3:66:4d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
> 
**dhclient if_name gives the following:**
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
eheldreth@Frodo:/var/log$ sudo dhclient if_name
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
if_name: ERROR while getting interface flags: No such device
if_name: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


> **I have included the relevant portion from /var/log/syslog below:**
Dec 13 22:05:33 Frodo NetworkManager: <debug> [1197601533.240572] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Shadowrealm' 
Dec 13 22:05:33 Frodo NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Shadowrealm 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Deactivating device wlan0. 
Dec 13 22:05:33 Frodo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Dec 13 22:05:33 Frodo NetworkManager: <info>  Device wlan0 activation scheduled... 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Activation (wlan0) started... 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec 13 22:05:33 Frodo NetworkManager: <info>  Activation (wlan0/wireless): access point 'Shadowrealm' is unencrypted, no key needed. 
Dec 13 22:05:34 Frodo NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Dec 13 22:05:34 Frodo NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Dec 13 22:05:34 Frodo NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant3^I' 
Dec 13 22:05:34 Frodo kernel: [  149.918606] NET: Registered protocol family 17
Dec 13 22:05:34 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:05:34 Frodo NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Dec 13 22:05:35 Frodo NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Dec 13 22:05:36 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:05:36 Frodo NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec 13 22:05:37 Frodo NetworkManager: <info>  SUP: response was '0' 
Dec 13 22:05:37 Frodo NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 536861646f777265616c6d' 
Dec 13 22:05:37 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:05:37 Frodo NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Dec 13 22:05:38 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:05:38 Frodo NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec 13 22:05:38 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:05:38 Frodo NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec 13 22:05:47 Frodo NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Dec 13 22:05:57 Frodo NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Dec 13 22:05:58 Frodo NetworkManager: <info>  wlan0: link timed out. 
Dec 13 22:06:02 Frodo NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Dec 13 22:06:17 Frodo last message repeated 3 times
Dec 13 22:06:20 Frodo NetworkManager: <info>  wlan0: link timed out. 
Dec 13 22:06:22 Frodo NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Dec 13 22:06:32 Frodo last message repeated 2 times
Dec 13 22:06:35 Frodo NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Dec 13 22:06:35 Frodo NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Dec 13 22:06:36 Frodo NetworkManager: <info>  Activation (wlan0) failed for access point (Shadowrealm) 
Dec 13 22:06:36 Frodo NetworkManager: <info>  Activation (wlan0) failed. 
Dec 13 22:06:36 Frodo NetworkManager: <info>  Deactivating device wlan0. 
Dec 13 22:06:36 Frodo NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Dec 13 22:06:36 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:06:36 Frodo NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Dec 13 22:06:36 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:06:36 Frodo NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Dec 13 22:06:36 Frodo NetworkManager: <info>  SUP: response was 'OK' 
Dec 13 22:06:42 Frodo NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 

---

### Post by csat on 2007-12-16
There is no better tutorial for Broadcom network board than this one:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

and I also suggest you to try WICD as network manager.  Look for it at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Both work like a charm along my Dell 131 L.

---

### Post by eheldreth on 2007-12-16
> **csat said:**
> There is no better tutorial for Broadcom network board than this one:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

and I also suggest you to try WICD as network manager.  Look for it at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Both work like a charm along my Dell 131 L.


That's great man.  All I had to do was install WICD and it worked great.  Thanks a million.

---

### Post by csat on 2007-12-16
You're welcome!  Whenever possible go to "Thread tools" on top and change status of this message to SOLVED.

Cheers,

---

