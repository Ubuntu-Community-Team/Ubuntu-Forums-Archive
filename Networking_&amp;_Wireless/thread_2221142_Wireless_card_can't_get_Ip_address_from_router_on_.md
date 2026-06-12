---
title: "Wireless card can't get Ip address from router on Ubuntu 14"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by MintyFreshLinux on 2014-04-30
So a couple weeks back I set up Ubuntu 14.04 on my secondary hard drive, and I set up wireless with ndiswrapper and my realtek rtl8190 using a tutorial i found [here]("http://ubuntuforums.org/showthread.php?t=1433401"). After that I could see the wireless networks but I could not connect to them, I asked for help on the forums and one of the forums member chili555 helped me out a lot (you can see that thread [here]("http://ubuntuforums.org/showthread.php?t=2218515"); thanks again chili). Unfortunately I'am not at an end of my wireless troubles it seems. What happens now is that my wireless card seems to have trouble acquiring an IP address, which makes my boot time SUPER long.  Sometimes, my computer won't connect until I log in and run a sudo dhclient -v wlan0 or a sudo ifdown wlan0 && sudo ifup -v wlan0, then it might connect and I can go on my merry way. Sometimes even running these commands don't work and my wireless card will get stuck broadcasting for an ip address,  and then I'll have reboot a second time and then I can usually connect. The time I spend sometimes trying to troubleshoot this thing really cuts into my work time so I'm hoping I can finally nip this in the butt for good. I'll post the syslog I captured while I was stuck trying to get an IP address. I'll post my syslog and my /etc/network/interface config file here : 

/etc/network/interfaces
```

auto loiface lo inet loopback


auto wlan0
iface wlan0 inet dhcp
wpa-ssid 2WIRE201
wpa-psk 5848477459

```









syslog
```
Apr 27 09:54:53 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.Apr 27 09:54:53 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:55:13 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:55:13 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:55:13 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:55:13 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:55:30 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:55:30 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:55:30 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:55:30 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:55:50 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:55:50 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:55:50 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:55:50 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:55:57 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:55:57 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:55:57 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:55:57 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:56:11 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:56:11 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:56:11 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:56:11 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:56:22 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:56:22 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:56:22 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:56:22 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:56:29 anthony-vm dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 27 09:56:29 anthony-vm dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 27 09:56:29 anthony-vm dhclient: All rights reserved.
Apr 27 09:56:29 anthony-vm dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 27 09:56:29 anthony-vm dhclient: 
Apr 27 09:56:29 anthony-vm dhclient: Listening on LPF/wlan0/00:08:54:9c:8b:8f
Apr 27 09:56:29 anthony-vm dhclient: Sending on   LPF/wlan0/00:08:54:9c:8b:8f
Apr 27 09:56:29 anthony-vm dhclient: Sending on   Socket/fallback
Apr 27 09:56:29 anthony-vm dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67 (xid=0x7e79fa8b)
Apr 27 09:56:29 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:56:29 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:56:29 anthony-vm dhclient: dhclient.c:2365: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:56:29 anthony-vm avahi-daemon[820]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr 27 09:56:29 anthony-vm avahi-daemon[820]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::208:54ff:fe9c:8b8f.
Apr 27 09:56:29 anthony-vm dhclient: receive_packet failed on wlan0: Network is down
Apr 27 09:56:29 anthony-vm avahi-daemon[820]: Withdrawing address record for fe80::208:54ff:fe9c:8b8f on wlan0.
Apr 27 09:56:29 anthony-vm wpa_supplicant[22470]: Successfully initialized wpa_supplicant
Apr 27 09:56:29 anthony-vm wpa_supplicant[22470]: nl80211: Driver does not support authentication/association or connect commands
Apr 27 09:51:54 anthony-vm wpa_supplicant[22172]: wlan0: WPA: Group rekeying completed with 60:c3:97:b4:73:f9 [GTK=CCMP]
Apr 27 09:56:29 anthony-vm wpa_supplicant[22172]: wlan0: CTRL-EVENT-TERMINATING 
Apr 27 09:56:29 anthony-vm dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 27 09:56:29 anthony-vm dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 27 09:56:29 anthony-vm dhclient: All rights reserved.
Apr 27 09:56:29 anthony-vm dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 27 09:56:29 anthony-vm dhclient: 
Apr 27 09:56:29 anthony-vm kernel: [24162.209322] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 09:56:29 anthony-vm dhclient: Listening on LPF/wlan0/00:08:54:9c:8b:8f
Apr 27 09:56:29 anthony-vm dhclient: Sending on   LPF/wlan0/00:08:54:9c:8b:8f
Apr 27 09:56:29 anthony-vm dhclient: Sending on   Socket/fallback
Apr 27 09:56:29 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x2ab3ebac)
Apr 27 09:56:32 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x2ab3ebac)
Apr 27 09:56:29 anthony-vm dhclient: receive_packet failed on wlan0: Network is down
Apr 27 09:56:33 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:56:33 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:56:33 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:56:33 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:56:39 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:56:39 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:56:39 anthony-vm kernel: [24172.469992] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 27 09:56:39 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:56:39 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:56:40 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x2ab3ebac)
Apr 27 09:56:40 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:56:41 anthony-vm avahi-daemon[820]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::208:54ff:fe9c:8b8f.
Apr 27 09:56:41 anthony-vm avahi-daemon[820]: New relevant interface wlan0.IPv6 for mDNS.
Apr 27 09:56:41 anthony-vm avahi-daemon[820]: Registering new address record for fe80::208:54ff:fe9c:8b8f on wlan0.*.
Apr 27 09:56:42 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:56:44 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 09:56:44 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:56:44 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:56:44 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:56:44 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:56:52 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x2ab3ebac)
Apr 27 09:56:56 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 09:56:56 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 09:56:58 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:56:58 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:56:58 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:56:58 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:57:05 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x2ab3ebac)
Apr 27 09:57:06 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:57:06 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:57:06 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:57:06 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:57:07 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:57:09 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:57:11 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 09:57:16 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:57:16 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:57:16 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:57:16 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:57:19 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x2ab3ebac)
Apr 27 09:57:23 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 09:57:23 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 09:57:31 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:57:31 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:57:31 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:57:31 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:57:33 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:57:33 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:57:33 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:57:33 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:57:34 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:57:38 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17 (xid=0x2ab3ebac)
Apr 27 09:57:36 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:57:38 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 09:57:39 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:57:39 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:57:39 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:57:39 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:57:50 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 09:57:50 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 09:57:53 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:57:53 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:57:53 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:57:53 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:57:55 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x2ab3ebac)
Apr 27 09:58:00 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:58:01 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:58:01 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:58:01 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:58:02 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:58:04 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:58:05 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 09:58:07 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x2ab3ebac)
Apr 27 09:58:14 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:58:14 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:58:14 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:58:14 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:58:16 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x2ab3ebac)
Apr 27 09:58:18 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 09:58:18 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 09:58:27 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x2ab3ebac)
Apr 27 09:58:28 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:58:28 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:58:28 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:58:28 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:58:29 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:58:31 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:58:33 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 09:58:34 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:58:34 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:58:34 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:58:34 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:58:45 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 09:58:45 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 09:58:46 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x2ab3ebac)
Apr 27 09:58:47 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:58:47 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:58:47 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:58:47 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:58:55 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:58:55 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:58:55 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:58:55 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:58:56 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:58:58 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:58:58 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:58:58 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:58:58 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:58:59 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x2ab3ebac)
Apr 27 09:58:58 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:59:00 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 09:59:12 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 09:59:12 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 09:59:17 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x2ab3ebac)
Apr 27 09:59:18 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:59:18 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:59:18 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:59:18 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:59:22 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:59:22 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:59:22 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:59:22 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:59:23 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:59:27 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x2ab3ebac)
Apr 27 09:59:25 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:59:27 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 09:59:27 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:59:27 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:59:27 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:59:27 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:59:36 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:59:36 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:59:36 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:59:36 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:59:39 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 09:59:39 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 09:59:46 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:59:46 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 09:59:46 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 09:59:46 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:59:48 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x2ab3ebac)
Apr 27 09:59:49 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 09:59:49 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 09:59:49 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:59:49 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 09:59:50 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 09:59:52 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 09:59:54 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:00:04 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:00:04 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 10:00:04 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 10:00:04 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 10:00:04 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x2ab3ebac)
Apr 27 10:00:06 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:00:06 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:00:14 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x2ab3ebac)
Apr 27 10:00:16 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:00:17 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:00:17 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:00:17 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:00:18 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:00:20 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:00:21 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:00:22 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:00:22 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 10:00:22 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 10:00:22 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 10:00:28 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x2ab3ebac)
Apr 27 10:00:33 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:00:33 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 10:00:33 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 10:00:33 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 10:00:34 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:00:34 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:00:36 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x2ab3ebac)
Apr 27 10:00:44 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:00:44 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:00:44 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:00:44 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:00:45 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:00:47 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:00:47 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 10:00:47 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 10:00:47 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 10:00:47 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x2ab3ebac)
Apr 27 10:00:47 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:00:49 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:00:56 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x2ab3ebac)
Apr 27 10:01:01 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:01:01 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:01:06 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:01:06 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 10:01:06 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 10:01:06 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 10:01:08 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x2ab3ebac)
Apr 27 10:01:11 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:01:11 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:01:11 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:01:11 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:01:12 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:01:14 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:01:16 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:01:21 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x2ab3ebac)
Apr 27 10:01:23 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:01:23 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 10:01:23 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 10:01:23 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 10:01:28 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:01:28 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:01:30 anthony-vm dhclient: No DHCPOFFERS received.
Apr 27 10:01:30 anthony-vm dhclient: No working leases in persistent database - sleeping.
Apr 27 10:01:30 anthony-vm avahi-autoipd(wlan0)[22608]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 27 10:01:30 anthony-vm avahi-autoipd(wlan0)[22608]: Successfully called chroot().
Apr 27 10:01:30 anthony-vm avahi-autoipd(wlan0)[22608]: Successfully dropped root privileges.
Apr 27 10:01:30 anthony-vm avahi-autoipd(wlan0)[22608]: Starting with address 169.254.8.124
Apr 27 10:01:32 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:01:32 anthony-vm dhclient: send_packet: Network is unreachable
Apr 27 10:01:32 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.
Apr 27 10:01:32 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 10:01:36 anthony-vm avahi-autoipd(wlan0)[22608]: Callout BIND, address 169.254.8.124 on interface wlan0
Apr 27 10:01:36 anthony-vm avahi-daemon[820]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.124.
Apr 27 10:01:36 anthony-vm avahi-daemon[820]: New relevant interface wlan0.IPv4 for mDNS.
Apr 27 10:01:36 anthony-vm avahi-daemon[820]: Registering new address record for 169.254.8.124 on wlan0.IPv4.
Apr 27 10:01:38 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:01:38 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:01:38 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:01:38 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:01:39 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:01:40 anthony-vm avahi-autoipd(wlan0)[22608]: Successfully claimed IP address 169.254.8.124
Apr 27 10:01:40 anthony-vm ntpdate[22657]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Apr 27 10:01:40 anthony-vm ntpdate[22657]: no servers can be used, exiting
Apr 27 10:01:41 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:01:43 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:01:44 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 10:01:55 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:01:55 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:02:05 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:02:06 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:02:06 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:02:06 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:02:07 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:02:09 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:02:12 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:02:24 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:02:24 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:02:34 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:02:35 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:02:35 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:02:35 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:02:36 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:02:38 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:02:39 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:02:51 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:02:51 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:03:02 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:03:02 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:03:02 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:03:02 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:03:03 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:03:05 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:03:06 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:03:19 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:03:19 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:03:29 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:03:29 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:03:29 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:03:29 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:03:30 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:03:32 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:03:34 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:03:46 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:03:46 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:03:56 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:03:56 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:03:56 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:03:56 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:03:57 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:03:59 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:04:01 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:04:13 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:04:13 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:04:23 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:04:24 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:04:24 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:04:24 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:04:25 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:04:27 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:04:28 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:04:40 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:04:40 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:04:50 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:04:51 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:04:51 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:04:51 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:04:52 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:04:54 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:04:55 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:05:08 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:05:08 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:05:18 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:05:18 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:05:18 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:05:18 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:05:18 anthony-vm dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 27 10:05:18 anthony-vm dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 27 10:05:18 anthony-vm dhclient: All rights reserved.
Apr 27 10:05:18 anthony-vm dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 27 10:05:18 anthony-vm dhclient: Usage: dhclient [-4|-6] [-SNTP1dvrx] [-nw] [-p <port>] [-D LL|LLT]#012                [-s server-addr] [-cf config-file] [-lf lease-file]#012                [-pf pid-file] [--no-pid] [-e VAR=val]#012                [-sf script-file] [interface]
Apr 27 10:05:19 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:05:21 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:05:23 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:05:31 anthony-vm dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 27 10:05:31 anthony-vm dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 27 10:05:31 anthony-vm dhclient: All rights reserved.
Apr 27 10:05:31 anthony-vm dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 27 10:05:31 anthony-vm dhclient: Usage: dhclient [-4|-6] [-SNTP1dvrx] [-nw] [-p <port>] [-D LL|LLT]#012                [-s server-addr] [-cf config-file] [-lf lease-file]#012                [-pf pid-file] [--no-pid] [-e VAR=val]#012                [-sf script-file] [interface]
Apr 27 10:05:35 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:05:35 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:05:45 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:05:45 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:05:45 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:05:45 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:05:46 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:05:48 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:05:50 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:06:02 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:06:02 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:06:12 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:06:13 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:06:13 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:06:13 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:06:14 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:06:16 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:06:17 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:06:30 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:06:30 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:06:40 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:06:41 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:06:41 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:06:41 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:06:42 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:06:44 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:06:46 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:06:58 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:06:58 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:07:08 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:07:08 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:07:08 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:07:08 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:07:09 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:07:11 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:07:13 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:07:25 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:07:25 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:07:35 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:07:35 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:07:35 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:07:35 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:07:36 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:07:38 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:07:40 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:07:42 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x2db98884)
Apr 27 10:07:45 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 (xid=0x2db98884)
Apr 27 10:07:49 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x2db98884)
Apr 27 10:07:52 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:07:52 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:07:55 anthony-vm dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67 (xid=0x2a85ecd5)
Apr 27 10:07:55 anthony-vm avahi-autoipd(wlan0)[22608]: Got SIGTERM, quitting.
Apr 27 10:07:55 anthony-vm avahi-autoipd(wlan0)[22608]: Callout STOP, address 169.254.8.124 on interface wlan0
Apr 27 10:07:55 anthony-vm avahi-daemon[820]: Withdrawing address record for 169.254.8.124 on wlan0.
Apr 27 10:07:55 anthony-vm avahi-daemon[820]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.124.
Apr 27 10:07:55 anthony-vm avahi-daemon[820]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 27 10:07:57 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x2db98884)
Apr 27 10:08:00 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x3fc63321)
Apr 27 10:08:02 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:08:02 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:08:02 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:08:02 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:08:03 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 (xid=0x3fc63321)
Apr 27 10:08:03 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:08:06 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x2db98884)
Apr 27 10:08:05 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:08:07 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:08:07 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x3fc63321)
Apr 27 10:08:18 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x3fc63321)
Apr 27 10:08:19 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:08:19 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:08:22 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x2db98884)
Apr 27 10:08:29 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:08:30 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:08:30 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:08:30 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:08:31 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:08:33 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x3fc63321)
Apr 27 10:08:33 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:08:34 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:08:36 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17 (xid=0x2db98884)
Apr 27 10:08:45 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x3fc63321)
Apr 27 10:08:47 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:08:47 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:08:53 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x2db98884)
Apr 27 10:08:57 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:08:57 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:08:57 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:08:57 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:08:58 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:08:58 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x3fc63321)
Apr 27 10:09:00 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:09:02 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:09:09 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x3fc63321)
Apr 27 10:09:14 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:09:14 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:09:23 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x3fc63321)
Apr 27 10:09:24 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:09:24 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:09:24 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:09:24 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:09:25 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:09:27 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:09:29 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:09:30 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x3fc63321)
Apr 27 10:09:13 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x2db98884)
Apr 27 10:09:33 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x2db98884)
Apr 27 10:09:39 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x3fc63321)
Apr 27 10:09:41 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:09:41 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:09:51 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:09:51 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x2db98884)
Apr 27 10:09:51 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:09:51 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:09:51 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:09:52 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:09:54 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x3fc63321)
Apr 27 10:09:54 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:09:56 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:10:04 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17 (xid=0x3fc63321)
Apr 27 10:10:04 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x2db98884)
Apr 27 10:10:08 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:10:08 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:10:15 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x2db98884)
Apr 27 10:10:18 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:10:19 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:10:19 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:10:19 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:10:20 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:10:21 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x3fc63321)
Apr 27 10:10:22 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:10:23 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:10:28 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x3fc63321)
Apr 27 10:10:29 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x2db98884)
Apr 27 10:10:36 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:10:36 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:10:37 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x3fc63321)
Apr 27 10:10:38 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x2db98884)
Apr 27 10:10:46 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:10:46 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:10:46 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:10:46 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:10:47 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:10:48 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x3fc63321)
Apr 27 10:10:49 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:10:51 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:10:54 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x2db98884)
Apr 27 10:11:03 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:11:03 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:11:07 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x2db98884)
Apr 27 10:11:09 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x3fc63321)
Apr 27 10:11:13 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:11:13 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:11:13 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:11:13 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:11:14 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:11:16 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x3fc63321)
Apr 27 10:11:16 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:11:18 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:11:25 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x2db98884)
Apr 27 10:11:30 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:11:30 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:11:28 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x3fc63321)
Apr 27 10:11:40 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x3fc63321)
Apr 27 10:11:40 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:11:40 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:11:40 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:11:40 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:11:41 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:11:45 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x2db98884)
Apr 27 10:11:43 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:11:45 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:11:54 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x3fc63321)
Apr 27 10:11:57 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:11:57 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:12:01 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x2db98884)
Apr 27 10:12:07 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:12:08 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:12:08 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:12:08 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:12:09 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:12:11 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:12:12 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:12:15 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x3fc63321)
Apr 27 10:12:20 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x2db98884)
Apr 27 10:12:24 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:12:24 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:12:27 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x2db98884)
Apr 27 10:12:31 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x3fc63321)
Apr 27 10:12:34 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:12:35 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:12:35 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:12:35 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:12:36 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:12:38 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:12:39 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:12:42 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1 (xid=0x2db98884)
Apr 27 10:12:43 anthony-vm dhclient: No DHCPOFFERS received.
Apr 27 10:12:43 anthony-vm dhclient: No working leases in persistent database - sleeping.
Apr 27 10:12:43 anthony-vm avahi-autoipd(wlan0)[22945]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 27 10:12:43 anthony-vm avahi-autoipd(wlan0)[22945]: Successfully called chroot().
Apr 27 10:12:43 anthony-vm avahi-autoipd(wlan0)[22945]: Successfully dropped root privileges.
Apr 27 10:12:43 anthony-vm avahi-autoipd(wlan0)[22945]: Starting with address 169.254.8.124
Apr 27 10:12:48 anthony-vm avahi-autoipd(wlan0)[22945]: Callout BIND, address 169.254.8.124 on interface wlan0
Apr 27 10:12:48 anthony-vm avahi-daemon[820]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.124.
Apr 27 10:12:48 anthony-vm avahi-daemon[820]: New relevant interface wlan0.IPv4 for mDNS.
Apr 27 10:12:48 anthony-vm avahi-daemon[820]: Registering new address record for 169.254.8.124 on wlan0.IPv4.
Apr 27 10:12:50 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x3fc63321)
Apr 27 10:12:52 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:12:52 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:12:52 anthony-vm avahi-autoipd(wlan0)[22945]: Successfully claimed IP address 169.254.8.124
Apr 27 10:13:01 anthony-vm dhclient: No DHCPOFFERS received.
Apr 27 10:13:01 anthony-vm dhclient: No working leases in persistent database - sleeping.
Apr 27 10:13:02 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:13:02 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:13:02 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:13:02 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:13:03 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:13:05 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:13:07 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:13:19 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:13:19 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:13:29 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:13:29 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:13:29 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:13:29 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:13:30 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:13:32 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:13:34 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:13:46 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:13:46 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:13:56 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:13:57 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:13:57 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:13:57 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:13:58 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:14:00 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:14:01 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:14:13 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:14:13 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:14:24 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:14:24 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:14:24 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:14:24 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:14:25 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:14:27 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:14:29 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:14:41 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:14:41 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:14:51 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:14:51 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:14:51 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:14:51 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:14:52 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:14:54 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:14:56 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:15:08 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:15:08 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:15:18 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:15:18 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:15:18 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:15:18 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:15:18 anthony-vm kernel: [25291.853248] Chrome_IOThread[2390]: segfault at ffffcb78cde82634 ip 00007fcf36c35e3c sp 00007fcf1a1d37c0 error 5 in chrome[7fcf35bab000+4f41000]
Apr 27 10:15:19 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:15:21 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:15:23 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:15:35 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:15:35 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:15:45 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:15:46 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:15:46 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:15:46 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:15:47 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:15:49 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:15:50 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:16:03 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:16:03 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:16:13 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:16:13 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:16:13 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:16:13 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:16:14 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:16:16 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:16:18 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:16:21 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x5527a3f1)
Apr 27 10:16:24 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x5527a3f1)
Apr 27 10:16:30 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x5527a3f1)
Apr 27 10:16:30 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:16:30 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:16:40 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:16:40 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:16:40 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:16:40 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:16:41 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:16:45 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x5527a3f1)
Apr 27 10:16:43 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:16:45 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:16:55 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x5527a3f1)
Apr 27 10:16:57 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:16:57 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:17:01 anthony-vm CRON[23984]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 27 10:17:07 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:17:07 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:17:07 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:17:07 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:17:08 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:17:10 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:17:12 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:17:16 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x5527a3f1)
Apr 27 10:17:24 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:17:24 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:17:29 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x5527a3f1)
Apr 27 10:17:34 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:17:35 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:17:35 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:17:35 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:17:36 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:17:38 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x5527a3f1)
Apr 27 10:17:38 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:17:39 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:17:51 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x5527a3f1)
Apr 27 10:17:52 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:17:52 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:18:02 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:18:02 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:18:02 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:18:02 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:18:03 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:18:05 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:18:07 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:18:11 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x5527a3f1)
Apr 27 10:18:18 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x5527a3f1)
Apr 27 10:18:19 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:18:19 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:18:29 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:18:29 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:18:29 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:18:29 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:18:30 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:18:32 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:18:34 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:18:38 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x5527a3f1)
Apr 27 10:18:45 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x5527a3f1)
Apr 27 10:18:46 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:18:46 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:18:54 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x1df9d0f2)
Apr 27 10:18:56 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:18:56 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:18:56 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:18:56 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:18:57 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x1df9d0f2)
Apr 27 10:18:57 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:18:59 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x5527a3f1)
Apr 27 10:18:59 anthony-vm wpa_supplicant[22476]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
Apr 27 10:19:01 anthony-vm wpa_supplicant[22476]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Apr 27 10:19:05 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x1df9d0f2)
Apr 27 10:19:13 anthony-vm wpa_supplicant[22476]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 27 10:19:13 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
Apr 27 10:19:18 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x1df9d0f2)
Apr 27 10:19:18 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x5527a3f1)
Apr 27 10:19:23 anthony-vm wpa_supplicant[22476]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
Apr 27 10:19:24 anthony-vm wpa_supplicant[22476]: wlan0: Associated with 60:c3:97:b4:73:f9
Apr 27 10:19:24 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
Apr 27 10:19:24 anthony-vm wpa_supplicant[22476]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
Apr 27 10:19:24 anthony-vm wpa_supplicant[22476]: wlan0: WPA: Group rekeying completed with 60:c3:97:b4:73:f9 [GTK=CCMP]
Apr 27 10:19:31 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x1df9d0f2)
Apr 27 10:19:32 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 255.255.255.255 port 67 (xid=0x1df9d0f2)
Apr 27 10:19:32 anthony-vm dhclient: DHCPOFFER of 192.168.1.72 from 192.168.1.254
Apr 27 10:19:32 anthony-vm dhclient: DHCPACK of 192.168.1.72 from 192.168.1.254
Apr 27 10:19:32 anthony-vm avahi-autoipd(wlan0)[22945]: Got SIGTERM, quitting.
Apr 27 10:19:32 anthony-vm avahi-autoipd(wlan0)[22945]: Callout STOP, address 169.254.8.124 on interface wlan0
Apr 27 10:19:32 anthony-vm avahi-daemon[820]: Withdrawing address record for 169.254.8.124 on wlan0.
Apr 27 10:19:32 anthony-vm avahi-daemon[820]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.124.
Apr 27 10:19:32 anthony-vm avahi-daemon[820]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 27 10:19:32 anthony-vm avahi-daemon[820]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.72.
Apr 27 10:19:32 anthony-vm avahi-daemon[820]: New relevant interface wlan0.IPv4 for mDNS.
Apr 27 10:19:32 anthony-vm avahi-daemon[820]: Registering new address record for 192.168.1.72 on wlan0.IPv4.
Apr 27 10:19:33 anthony-vm dhclient: bound to 192.168.1.72 -- renewal in 36787 seconds.
Apr 27 10:19:33 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x5527a3f1)
Apr 27 10:19:33 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 255.255.255.255 port 67 (xid=0x5527a3f1)
Apr 27 10:19:33 anthony-vm dhclient: DHCPOFFER of 192.168.1.72 from 192.168.1.254
Apr 27 10:19:33 anthony-vm dhclient: DHCPACK of 192.168.1.72 from 192.168.1.254
Apr 27 10:19:34 anthony-vm dhclient: bound to 192.168.1.72 -- renewal in 36942 seconds.
Apr 27 10:22:35 anthony-vm dbus[769]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr 27 10:22:35 anthony-vm dbus[769]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

---

### Post by chili555 on 2014-04-30
> auto loiface lo inet loopback


auto wlan0
iface wlan0 inet dhcp
wpa-ssid 2WIRE201
wpa-psk 5848477459I hope you meant:```
auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet dhcp
wpa-ssid 2WIRE201
wpa-psk 5848477459
```If not, please change it.> Apr 27 09:54:53 anthony-vm dhclient: send_packet: please consult README file regarding broadcast address.Apr 27 09:54:53 anthony-vm dhclient: dhclient.c:2277: Failed to send 300 byte long packet over fallback interface.
Apr 27 09:55:13 anthony-vm dhclient: DHCPREQUEST of 192.168.1.72 on wlan0 to 192.168.1.254 port 67 (xid=0x8c0b29)
Apr 27 09:55:13 anthony-vm dhclient: send_packet: Network is unreachableYikes! 

Is Network Manager completely devoid of any wireless details, since you are using /etc/network/interfaces? It should be  blank. 

If you make changes, reboot and let's continue.

---

### Post by MintyFreshLinux on 2014-05-01
I made the changes, then I rebooted, as soon the OS booted I had internet access, then I rebooted again to be sure that the issue was fixed and then I was without internet again, I had to do a sudo dhclient -v wlan0 to grab and IP address and It took about 15 minutes or so before it did.

---

### Post by chili555 on 2014-05-01
> **MintyFreshLinux said:**
> I made the changes, then I rebooted, as soon the OS booted I had internet access, then I rebooted again to be sure that the issue was fixed and then I was without internet again, I had to do a sudo dhclient -v wlan0 to grab and IP address and It took about 15 minutes or so before it did.Let's see some diagnostics.```
sudo ifdown wlan0 && sudo ifup -v wlan0
```The flag -v for verbose should produce some interesting clues. Also:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```

---

### Post by MintyFreshLinux on 2014-05-02
Here's my results:

```
anthony@anthony-vm:~$ cat /var/log/syslog | grep -e wlan0 -e etwork | tail -n20 May  2 11:08:11 anthony-vm avahi-daemon[810]: Withdrawing address record for fe80::208:54ff:fe9c:8b8f on wlan0.May  2 11:07:33 anthony-vm wpa_supplicant[715]: wlan0: WPA: Group rekeying completed with 60:c3:97:b4:73:f9 [GTK=CCMP]
May  2 11:08:11 anthony-vm wpa_supplicant[715]: wlan0: CTRL-EVENT-TERMINATING 
May  2 11:08:12 anthony-vm kernel: [  226.566897] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  2 11:08:12 anthony-vm dhclient: Listening on LPF/wlan0/00:08:54:9c:8b:8f
May  2 11:08:12 anthony-vm dhclient: Sending on   LPF/wlan0/00:08:54:9c:8b:8f
May  2 11:08:12 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x3c04fbaa)
May  2 11:08:15 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 (xid=0x3c04fbaa)
May  2 11:08:20 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x3c04fbaa)
May  2 11:08:22 anthony-vm wpa_supplicant[2891]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
May  2 11:08:23 anthony-vm wpa_supplicant[2891]: wlan0: Associated with 60:c3:97:b4:73:f9
May  2 11:08:23 anthony-vm kernel: [  236.895584] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  2 11:08:23 anthony-vm wpa_supplicant[2891]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  2 11:08:23 anthony-vm wpa_supplicant[2891]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
May  2 11:08:24 anthony-vm wpa_supplicant[2891]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  2 11:08:25 anthony-vm avahi-daemon[810]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::208:54ff:fe9c:8b8f.
May  2 11:08:25 anthony-vm avahi-daemon[810]: New relevant interface wlan0.IPv6 for mDNS.
May  2 11:08:25 anthony-vm avahi-daemon[810]: Registering new address record for fe80::208:54ff:fe9c:8b8f on wlan0.*.
May  2 11:08:26 anthony-vm wpa_supplicant[2891]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
May  2 11:08:27 anthony-vm wpa_supplicant[2891]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet



```

---

### Post by chili555 on 2014-05-02
There is nothing remarkable; that is, fixable there. How about the other command? Also:```
dmesg | grep -e wlan -e 80211
```

---

### Post by MintyFreshLinux on 2014-05-03
> **chili555 said:**
> There is nothing remarkable; that is, fixable there. How about the other command? Also:```
dmesg | grep -e wlan -e 80211
```

Not sure if this is any better
```
anthony@anthony-vm:~$ dmesg | grep -e wlan -e 80211[   12.626375] wlan0: ethernet device 00:08:54:9c:8b:8f using NDIS driver: net819xp, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8190 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8190.5.conf
[   12.626404] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   13.247524] cfg80211: Calling CRDA to update world regulatory domain
[   13.248207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.251211] cfg80211: World regulatory domain updated:
[   13.251213] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.251215] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.251216] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.251217] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.251218] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.251219] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.583259] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  510.257374] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  520.482179] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
anthony@anthony-vm:~$ 



```

---

### Post by MintyFreshLinux on 2014-05-05
Are we out of ideas? Should I look up another log file?

---

### Post by chili555 on 2014-05-05
I agree with you that the most recent log is no more informative. I only have a few suggestions remaining. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

You might also disable IPv6 in Network Manager: 
[https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png) This illustration is for wired ethernet, but we want wireless.

After you make these changes, reboot and let us see:```
cat /var/log/syslog | grep -e wlan0 -e etwork | tail -n20 
```

---

### Post by MintyFreshLinux on 2014-05-08
```
anthony@anthony-vm:~$ cat /var/log/syslog | grep -e wlan0 -e etwork | tail -n20May  8 12:56:34 anthony-vm kernel: [  133.053661] type=1400 audit(1399568194.413:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1070 comm="apparmor_parser"
May  8 12:56:35 anthony-vm whoopsie[1256]: Could not get the Network Manager state:
May  8 12:56:35 anthony-vm whoopsie[1256]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
May  8 12:56:35 anthony-vm wpa_supplicant[729]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
May  8 12:56:37 anthony-vm wpa_supplicant[729]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  8 12:56:40 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x41acb2f6)
May  8 12:56:49 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x41acb2f6)
May  8 12:56:49 anthony-vm wpa_supplicant[729]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
May  8 12:56:49 anthony-vm wpa_supplicant[729]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
May  8 12:56:59 anthony-vm wpa_supplicant[729]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
May  8 12:57:00 anthony-vm wpa_supplicant[729]: wlan0: Associated with 60:c3:97:b4:73:f9
May  8 12:57:00 anthony-vm wpa_supplicant[729]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 12:57:00 anthony-vm wpa_supplicant[729]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
May  8 12:57:01 anthony-vm wpa_supplicant[729]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 12:57:03 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x41acb2f6)
May  8 12:57:03 anthony-vm wpa_supplicant[729]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
May  8 12:57:04 anthony-vm wpa_supplicant[729]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  8 12:57:16 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x41acb2f6)
May  8 12:57:16 anthony-vm wpa_supplicant[729]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
May  8 12:57:16 anthony-vm wpa_supplicant[729]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0



```


I'm getting the same messages but I still think your solution might have worked, when I rebooted my computer I automatically connected to the internet. :D

---

### Post by MintyFreshLinux on 2014-05-08
I rebooted again and my machine couldn't connect, so I deleted the changes I made to network manager, rebooted again, and my wifi seems to work (sort-of ). It takes a few minutes to connect and grab an IP address but at least it does so on i

```
After doing a dmesg[  134.320700] cfg80211: Calling CRDA for country: US
[  134.323158] cfg80211: Regulatory domain changed to country: US
[  134.323160] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  134.323161] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  134.323163] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  134.323164] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  134.323165] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  134.323166] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  134.323167] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  134.323168] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  134.859679] nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
[  135.425915] NVRM: Your system is not currently configured to drive a VGA console
[  135.425918] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[  135.425919] NVRM: requires the use of a text-mode VGA console. Use of other console
[  135.425921] NVRM: drivers including, but not limited to, vesafb, may result in
[  135.425922] NVRM: corruption and stability problems, and is not supported.
[  135.715141] init: plymouth-upstart-bridge main process ended, respawning
[  135.719929] init: plymouth-upstart-bridge main process (1359) terminated with status 1
[  135.719943] init: plymouth-upstart-bridge main process ended, respawning
[  324.247758] e1000e 0000:00:19.0: irq 48 for MSI/MSI-X
[  324.351011] e1000e 0000:00:19.0: irq 48 for MSI/MSI-X
[  324.351136] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  324.351334] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready




[[Aanthony@anthony-vm:~$ cat /var/log/syslog | grep -e wlan0 -e etwork | tail -n20                   cat /var/log/syslog | grep -e wlan0 -e etwork | tail -n20
May  8 13:40:16 anthony-vm wpa_supplicant[750]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 13:40:16 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
May  8 13:40:17 anthony-vm wpa_supplicant[750]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 13:40:19 anthony-vm wpa_supplicant[750]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
May  8 13:40:21 anthony-vm wpa_supplicant[750]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  8 13:40:27 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x2b286e34)
May  8 13:40:33 anthony-vm wpa_supplicant[750]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
May  8 13:40:33 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
May  8 13:40:38 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x2b286e34)
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: Associated with 60:c3:97:b4:73:f9
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
May  8 13:40:44 anthony-vm wpa_supplicant[750]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 13:40:46 anthony-vm wpa_supplicant[750]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
May  8 13:40:48 anthony-vm wpa_supplicant[750]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  8 13:40:52 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x2b286e34)
May  8 13:41:00 anthony-vm wpa_supplicant[750]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
May  8 13:41:00 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
May  8 13:41:05 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x2b286e34)
anthony@anthony-vm:~$ cat /var/log/syslog | grep -e wlan0 -e etwork | tail -n20
May  8 13:40:27 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x2b286e34)
May  8 13:40:33 anthony-vm wpa_supplicant[750]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
May  8 13:40:33 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
May  8 13:40:38 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x2b286e34)
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: Associated with 60:c3:97:b4:73:f9
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 13:40:43 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
May  8 13:40:44 anthony-vm wpa_supplicant[750]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 13:40:46 anthony-vm wpa_supplicant[750]: message repeated 2 times: [ wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]]
May  8 13:40:48 anthony-vm wpa_supplicant[750]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  8 13:40:52 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x2b286e34)
May  8 13:41:00 anthony-vm wpa_supplicant[750]: message repeated 11 times: [ wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
May  8 13:41:00 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
May  8 13:41:05 anthony-vm dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x2b286e34)
May  8 13:41:10 anthony-vm wpa_supplicant[750]: wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2417 MHz)
May  8 13:41:11 anthony-vm wpa_supplicant[750]: wlan0: Associated with 60:c3:97:b4:73:f9
May  8 13:41:11 anthony-vm wpa_supplicant[750]: wlan0: WPA: Key negotiation completed with 60:c3:97:b4:73:f9 [PTK=CCMP GTK=CCMP]
May  8 13:41:11 anthony-vm wpa_supplicant[750]: wlan0: CTRL-EVENT-CONNECTED - Connection to 60:c3:97:b4:73:f9 completed [id=0 id_str=]
May  8 13:41:11 anthony-vm wpa_supplicant[750]: wlan0: WPA: Group rekeying completed with 60:c3:97:b4:73:f9 [GTK=CCMP]
anthony@anthony-vm:~$ 



```

---

### Post by chili555 on 2014-05-08
> when I rebooted my computer I automatically connected to the internet. Awesome! Glad it's working!

---

