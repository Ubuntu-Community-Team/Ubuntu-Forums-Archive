---
title: "Unable to connect to an encrypted wireless network"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by amit1017 on 2008-11-27
Hi Guys...Sort of a newbie...Recently got a new Thinkpad T500 and set it up as dual boot with XP and Ubuntu 8.10.  Installation went fine.  But for some reason I am unable to connect to my encrypted wireless network.  I can connect to non-encrypted without any problems.  From the syslogs, it seems its failing in obtaining a dhcp address. Can you guys please help out?  thanks a lot.

Here are the log messages from /var/tmp/syslog:

Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'mySSID'. 
Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  dhclient started with pid 6890 
Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 27 08:49:44 amit-laptopT500 dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov 27 08:49:44 amit-laptopT500 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 27 08:49:44 amit-laptopT500 dhclient: All rights reserved.
Nov 27 08:49:44 amit-laptopT500 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 27 08:49:44 amit-laptopT500 dhclient: 
Nov 27 08:49:44 amit-laptopT500 dhclient: wmaster0: unknown hardware address type 801
Nov 27 08:49:44 amit-laptopT500 NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Nov 27 08:49:44 amit-laptopT500 dhclient: wmaster0: unknown hardware address type 801
Nov 27 08:49:44 amit-laptopT500 dhclient: Listening on LPF/wlan0/00:21:5d:4e:08:f8
Nov 27 08:49:44 amit-laptopT500 dhclient: Sending on   LPF/wlan0/00:21:5d:4e:08:f8
Nov 27 08:49:44 amit-laptopT500 dhclient: Sending on   Socket/fallback
Nov 27 08:49:46 amit-laptopT500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov 27 08:49:49 amit-laptopT500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov 27 08:49:57 amit-laptopT500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov 27 08:50:10 amit-laptopT500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Nov 27 08:50:28 amit-laptopT500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 6890 
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'Home'. 
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  (wlan0): device state change: 7 -> 6 
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Nov 27 08:50:29 amit-laptopT500 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov 27 08:52:53 amit-laptopT500 NetworkManager: <info>  (wlan0): device state change: 6 -> 3 
Nov 27 08:52:53 amit-laptopT500 NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

---

### Post by rlzyoner on 2008-11-27
What type of encryption is the network using, wep or wpa or other ?
There's a good howto on this forum somewhere for manual connection to encrypted networks, i think its by either kevdog or weiman, actually its in the stickys. Maybe check that out.
Whenever I have issues like your, i revery back to the terminal and connect manually and this usually does the trick

---

### Post by Bucky Ball on 2008-11-27
System->Administration->Network

Unlock, select Wireless connection->Properties. Untick 'Enable Roaming', fill in correct ESSID and security details, at 'Configuration', select 'Automatic Configuration (DHCP)'.

---

### Post by amit1017 on 2008-11-27
I have a WEP 128-bit encryption.  I will try to looking for the sticky.

Bucky:  I believe what you are talking about is in 8.04, not in 8.10.  I am unable to find the Roaming option.  Rest of the stuff is configured correctly.

---

