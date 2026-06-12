---
title: "wicd bad password at eduroam network"
date: 2015-05-20
forum: Networking &amp; Wireless
---

### Post by asgard2 on 2015-05-20
Hi,

I can not connect with wicd to my university eduroam network.

It breaks up after some time with "bad password".

After some research I tested this profile, but still the same problem.
[https://www.linuxquestions.org/questions/slackware-14/eduroam-wifi-connection-with-wicd-4175479700/](https://www.linuxquestions.org/questions/slackware-14/eduroam-wifi-connection-with-wicd-4175479700/)

No problems with my home wifi network with WPA2.

Version: Wicd 1.7.2.4
Xubuntu 14.04

Tested my login with lubuntu 15.04 live and regular network manager, these settings are working.

Regards

---

### Post by Bucky Ball on 2015-05-20
Before we go any further with this, have you talked to the IT department at the uni re. this issue? Get their opinion first as, as all is working fine with your home setup, there's a good possibility this problem is generated at their end or by how you have eduroam setup and/or your details in it. We can't help a lot with that but your IT dept. people will know exactly. 

Good luck and let us know what they have to say.

---

### Post by asgard2 on 2015-05-20
I asked the IT dep some time ago because of another connection problem and they can only check the settings:
encyption: WPA2+AES
authentification: 802.1x PEAP/MSCHAPv2

There is no linux user around.

When it is working with the network manager from vivid, I expect the problem on my side.

```
2015/05/19 13:07:08 :: 
2015/05/19 13:07:08 :: Executing /etc/network/if-post-down.d/wireless-tools with params 
2015/05/19 13:07:08 :: /etc/network/if-post-down.d/wireless-tools returned 0
2015/05/19 13:07:08 :: Executing /etc/network/if-post-down.d/wpasupplicant with params 
2015/05/19 13:07:08 :: /etc/network/if-post-down.d/wpasupplicant returned 0
2015/05/19 13:07:08 :: wpa_cli -i eth0 terminate
Failed to connect to non-global ctrl_ifname: eth0  error: No such file or directory
2015/05/19 13:07:08 :: Executing /etc/network/if-pre-up.d/ethtool with params 
2015/05/19 13:07:08 :: /etc/network/if-pre-up.d/ethtool returned 0
2015/05/19 13:07:08 :: Executing /etc/network/if-pre-up.d/wireless-tools with params 
2015/05/19 13:07:08 :: /etc/network/if-pre-up.d/wireless-tools returned 0
2015/05/19 13:07:08 :: Executing /etc/network/if-pre-up.d/wpasupplicant with params 
2015/05/19 13:07:08 :: /etc/network/if-pre-up.d/wpasupplicant returned 0
2015/05/19 13:07:08 :: Putting interface down
2015/05/19 13:07:08 :: ifconfig wlan0 down
2015/05/19 13:07:08 :: Releasing DHCP leases...
2015/05/19 13:07:08 :: attempting to set hostname with dhclient
2015/05/19 13:07:08 :: using dhcpcd or another supported client may work better
2015/05/19 13:07:08 :: /sbin/dhclient -v -r wlan0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/ **************
Sending on   LPF/wlan0/ **************
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.178.1 port 67 (xid=0x7e8d0c02)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2365: Failed to send 300 byte long packet over fallback interface.
2015/05/19 13:07:08 :: Setting false IP...
2015/05/19 13:07:08 :: ifconfig wlan0 0.0.0.0 
2015/05/19 13:07:08 :: Stopping wpa_supplicant
2015/05/19 13:07:08 :: wpa_cli -i wlan0 terminate
Failed to connect to non-global ctrl_ifname: wlan0  error: No such file or directory
2015/05/19 13:07:08 :: Flushing the routing table...
2015/05/19 13:07:08 :: /sbin/ip route flush dev wlan0
2015/05/19 13:07:08 :: iwconfig wlan0 mode managed
2015/05/19 13:07:08 :: Putting interface up...
2015/05/19 13:07:08 :: ifconfig wlan0 up
2015/05/19 13:07:10 :: enctype is peap
2015/05/19 13:07:10 :: Attempting to authenticate...
2015/05/19 13:07:10 :: ['wpa_supplicant', '-B', '-i', 'wlan0', '-c', '/var/lib/wicd/configurations/dca2f74a72n1', '-Dnl80211']
2015/05/19 13:07:10 :: ['iwconfig', 'wlan0', 'essid', '--', 'eduroam']
2015/05/19 13:07:10 :: iwconfig wlan0 channel 6
2015/05/19 13:07:10 :: iwconfig wlan0 ap **************
2015/05/19 13:07:10 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:11 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:12 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:13 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:14 :: WPA_CLI RESULT IS AUTHENTICATING
2015/05/19 13:07:15 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:16 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:17 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:18 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:19 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:20 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:20 :: wpa_supplicant rescan forced...
2015/05/19 13:07:21 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:22 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:23 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:24 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:25 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:26 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:27 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:28 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:29 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:30 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:31 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:32 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:33 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:34 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:35 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:36 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:37 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:38 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:39 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:40 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:41 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:42 :: WPA_CLI RESULT IS DISCONNECTED
2015/05/19 13:07:43 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:44 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:45 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:46 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:47 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:48 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:49 :: WPA_CLI RESULT IS SCANNING
2015/05/19 13:07:50 :: wpa_supplicant authentication may have failed.
2015/05/19 13:07:50 :: connect result is failed
2015/05/19 13:07:50 :: exiting connection thread
2015/05/19 13:07:50 :: iwconfig wlan0
2015/05/19 13:07:50 :: Sending connection attempt result bad_pass
2015/05/19 13:07:50 :: ifconfig eth0
2015/05/19 13:07:50 :: ifconfig wlan0
2015/05/19 13:07:50 :: Forced disconnect on
2015/05/19 13:07:50 :: Executing /etc/network/if-down.d/avahi-autoipd with params 
2015/05/19 13:07:50 :: /etc/network/if-down.d/avahi-autoipd returned 0
2015/05/19 13:07:50 :: Executing /etc/network/if-down.d/resolvconf with params 
2015/05/19 13:07:50 :: /etc/network/if-down.d/resolvconf returned 0
2015/05/19 13:07:50 :: Executing /etc/network/if-down.d/upstart with params 
2015/05/19 13:07:50 :: /etc/network/if-down.d/upstart returned 0
2015/05/19 13:07:50 :: Executing /etc/network/if-down.d/wpasupplicant with params 
2015/05/19 13:07:50 :: /etc/network/if-down.d/wpasupplicant returned 0
2015/05/19 13:07:50 :: attempting to set hostname with dhclient
2015/05/19 13:07:50 :: using dhcpcd or another supported client may work better
2015/05/19 13:07:50 :: /sbin/dhclient -v -r wlan0

```

---

### Post by Bucky Ball on 2015-05-20
Probably unrelated, but when you are connected to the uni network, have a look at that connection in Network Manager and see if you can spot anything. Is it set up as an 'ad-hoc' connection? I'm figuring it should be. Anything else there that is either obviously out of whack or you suspect that you can pass on here? Is IPv6 set to 'igonore'?

The security details they and you have provided should be set when you connect to the network automagically so doubt it has anything to do with it, unless you are setting them manually and they are incorrect. Looking in Network Manager they should be set without you doing anything. Check they are set to what they should be.

---

### Post by asgard2 on 2015-06-20
At the standard network manager, it is set to "infrastructure" and ipv6 to automatic, settings should be correct.

I could not find a solution, so I replaced wicd with to the standard manager. 
It is generally working, but with a bad connection quality. sometimes I only receive time outs and the wlan is unusable. Where no problems on other devices ...

---

### Post by Bucky Ball on 2015-06-21
IPv6 set to ignore. Try that.

---

