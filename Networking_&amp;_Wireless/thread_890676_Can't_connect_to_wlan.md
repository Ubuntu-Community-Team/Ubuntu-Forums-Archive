---
title: "Can't connect to wlan"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Naatan on 2008-08-15
I just managed to get ndiswrapper working on my amd64 by disabling the restricted hardware drivers for networking, however I still can not connect to a wireless network.

It lists the wireless networks fine, but when I try to connect to one it simply fails, I've tried every type of authentication I could think of but no luck.. I also disabled all fancy settings on the router such as Super G Mode but no luck either.

My syslog shows the following:

```
Aug 15 09:52:21 nathan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Aug 15 09:52:21 nathan-laptop NetworkManager: <debug> [1218808341.176426] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'nathan-and-marie' 
Aug 15 09:52:21 nathan-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / nathan-and-marie 
Aug 15 09:52:21 nathan-laptop NetworkManager: <info>  Deactivating device wlan0. 
Aug 15 09:52:21 nathan-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 15 09:52:21 nathan-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 15 09:52:21 nathan-laptop NetworkManager: <info>  Deactivating device eth5. 
Aug 15 09:52:21 nathan-laptop dhclient: There is already a pid file /var/run/dhclient.eth5.pid with pid 8902
Aug 15 09:52:21 nathan-laptop dhclient: killed old client process, removed PID file
Aug 15 09:52:21 nathan-laptop kernel: [  686.999514] eth5: no IPv6 routers present
Aug 15 09:52:21 nathan-laptop dhclient: DHCPRELEASE on eth5 to 192.168.0.1 port 67
Aug 15 09:52:21 nathan-laptop avahi-daemon[5404]: Withdrawing address record for 192.168.0.101 on eth5.
Aug 15 09:52:21 nathan-laptop avahi-daemon[5404]: Leaving mDNS multicast group on interface eth5.IPv4 with address 192.168.0.101.
Aug 15 09:52:21 nathan-laptop avahi-daemon[5404]: Interface eth5.IPv4 no longer relevant for mDNS.
Aug 15 09:52:22 nathan-laptop avahi-daemon[5404]: Withdrawing address record for fe80::200:6cff:fe23:bf96 on eth5.
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) started... 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'nathan-and-marie' is encrypted, but NO valid key exists.  New key needed. 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'nathan-and-marie'. 
Aug 15 09:52:22 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 15 09:52:30 nathan-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'nathan-and-marie' received. 
Aug 15 09:52:30 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 15 09:52:30 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 15 09:52:30 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 15 09:52:30 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 15 09:52:30 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 15 09:52:30 nathan-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'nathan-and-marie' is encrypted, and a key exists.  No new key needed. 
Aug 15 09:52:31 nathan-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Aug 15 09:52:31 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was '0' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6e617468616e2d616e642d6d61726965' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  SUP: response was 'OK' 
Aug 15 09:52:32 nathan-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (nathan-and-marie) 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  Deactivating device wlan0. 
Aug 15 09:53:32 nathan-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth5'. 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  Will activate connection 'eth5'. 
Aug 15 09:53:32 nathan-laptop NetworkManager: <info>  Device eth5 activation scheduled...
```

Note the first message:

Aug 15 09:52:21 nathan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

Redhat?!?!?!

Does anyone know what might be going wrong here?

---

### Post by Naatan on 2008-08-15
After removing ath_pci from /etc/modules and adding ndiswrapper instead, then adding a blacklist for ath_pci and ath_hal to /etc/modprobe.d/blacklist everything is now working, thank god.

Sadly in my 2 days of help seeking on ubuntuforums no one has seemed to be able to give me any. :(

---

### Post by Naatan on 2008-08-16
Booted Ubuntu today and again it's not working :(

---

### Post by Naatan on 2008-08-16
bump

---

### Post by rafamg on 2008-08-19
Do you, by any chance, have VirtualBox OSE installed?. I have Madwifi drivers installed on my laptop and it was working great. I opened a VirtualBox session, wireless was going OK on the virtual side, but stopped working on the Hardy side. Once I shutdown the VBox session, the my wireless stopped working.

If I find anything else, I'll let you know.

---

### Post by Naatan on 2008-08-19
Thanks for your reply, no I don't have virtualbox installed.

My problems have returned after another reboot.. now it won't even show my connection anymore, how very tiring this is

---

### Post by rafamg on 2008-08-22
:confused: In my case, I got back home and connected there without problems, I got back to the office and the wireless started working again after bouncing the wi-fi router.

I'll keep trying to see if, in my case, it has something to do with VirtualBox, but right now is working again.

Good luck!

---

### Post by derakhshani on 2008-09-16
I have the same problem. Wireless was working fine.
I installed VirtualBox, and used it. Then I realized that wirelss is not working.

Did anyone find any solution to this problem?

---

