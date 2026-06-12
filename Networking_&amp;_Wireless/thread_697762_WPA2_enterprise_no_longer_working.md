---
title: "WPA2 enterprise no longer working"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by version7x on 2008-02-15
I've been loving ubuntu for quite some time now, but all of a sudden, my wireless network connection seems to have decided not to work.

I'm using WPA2 Enterprise with PEAP and a username and password.  This was working two days ago, but all of a sudden, it just times out.  I'm not even sure what to check at this point.  I know all of the software is installed - because it worked before.  I can connect on my windows (eww) and apple workstations, but not linux.

Some additional information...

At first, I would click the network Icon in the dock, select my wireless network and it would take about 20 seconds and then join it.  After a while, I started to have to enter my credentials every time I connected.  A few days later, this started not to work.  I would have to pretend my network wasn't there and select the option to "join other wireless network."   I'd re-enter all of the network info an my credentials and it would connect.  Now nothing works - even if I delete the configuration, reboot, and re-add it.

I'm using a dell D630 lattitude.  My windows partition has no problems accessing the wifi card, but when I boot into the REAL OS, I get no love!

Any ideas?

Thanks!

---

### Post by celljak on 2008-04-09
*Bump, as I'm curious. I cannot connect to Univ of Dallas via WPA2 and maybe this solution will help.

---

### Post by kevdog on 2008-04-10
What credentials is your university giving you?  Cert files, password, username, anything else?

---

### Post by jhallward on 2008-04-18
bump, same reason as above.

University gives me my username and password.  I'd found a fix for this problem sometime in late January/early February that I've been unable to find again, but since then I've restored my HD to an earlier partition image and I'm back to square one.

I can occasionally manage a connection (once out of several attempts), but I get disconnected after several seconds.  All other wireless works fine.  WPA, WEP and nonencrypted networks connect and stay connected without a problem.

tcpdump (wireshark's broken for now) gives some strange output around when I get disconnected, and it's to the tune of

11:51:40.870872 00:d0:02:29:34:00 (oui Unknown) Unknown SSAP 0x8c > 00:1c:b3:c5:e8:ad (oui Unknown) Unknown DSAP 0x5e Information, send seq 0, rcv seq 16, Flags [Command], length 1500
11:51:41.698297 IP <IP address>.56022 > 205.188.9.125.aol: P 3625:3631(6) ack 30068 win 62560
11:51:42.888418 IP <IP address>.56022 > 205.188.9.125.aol: P 3625:3631(6) ack 30068 win 62560
11:51:43.674814 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x28 Information, send seq 0, rcv seq 16, Flags [Command], length 92
11:51:43.737170 
11:51:43.741025 EAP code=1 id=0 length=58 
11:51:43.741090 EAP code=1 id=0 length=11 
11:51:43.748290 EAP code=1 id=0 length=6 
11:51:43.748469 EAP code=1 id=0 length=113 
11:51:43.761036 EAP code=1 id=0 length=1020 
11:51:43.761156 EAP code=1 id=0 length=6 
11:51:43.767282 EAP code=1 id=0 length=894 
11:51:43.790542 EAP code=1 id=0 length=204 
11:51:44.696962 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x28 Information, send seq 0, rcv seq 16, Flags [Command], length 193
Unknown DSAP 0x2a Information, send seq 0, rcv seq 16, Flags [Command], length 208
11:51:46.568204 IP wireless-165-124-113-243.nuwlan.northwestern.edu.56022 > 205.188.9.125.aol: P 3625:3631(6) ack 30068 win 62560
11:51:47.359190 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2a Information, send seq 0, rcv seq 16, Flags [Command], length 383
11:51:47.973396 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2c Information, send seq 0, rcv seq 16, Flags [Command], length 383
11:51:47.973604 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2c Information, send seq 0, rcv seq 16, Flags [Command], length 146
11:51:48.382870 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2e Information, send seq 0, rcv seq 16, Flags [Command], length 133
11:51:48.386030 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2e Information, send seq 0, rcv seq 16, Flags [Command], length 166
tcpdump: pcap_loop: recvfrom: Network is down
2063 packets captured
3244 packets received by filter
1181 packets dropped by kernel

I edited the output to read <IP address> instead of my IP+ISP/School info.

---

### Post by nikola.borisof on 2008-05-13
Hi Did you solve this problem. I'm also a Northwestern Student i also have hard time connecting to the wireless ;(

---

### Post by cacycleworks on 2008-05-15
I had some serious issues with wireless with many of the recent "updates" and upgrades". I just did a fresh install of Hardy ubuntu and everything works. To get a working kubuntu, I installed ubuntu then "apt-got" the kubuntu desktop. 

Maybe the upgrades made your life hard like it did mine?? 

Chris

---

### Post by Ti-Paul on 2008-05-19
Same trouble here...

Ubuntu 8.04 (latest update until now) on a Dell Inspiron 5150 with a Broadcomm 4306 (firmware version 4.10.47.3)...

Using ndiswrapper...

Continuously & randomly disconnecting... And after sometime, can no longer connect, even when deleting wifi accesspoint profile & creating a new one...

This is VERY anoying since using other solution (fwcutter) is giving me very poor connection... (at 11mbs instead of 54mbs of ndiswrapper)...

Seems like we have to make or network less secure to be able to use Ubuntu... :confused:

---

### Post by Ti-Paul on 2008-05-19
Just removed ndiswrapper and used:
sudo aptitude install b43-fwcutter

sudo iwlist wlan0 scan

Seem's like the connection is much more stable... But not very fast (1mbs instead of 22mbs i got with ndiswrapper)...

Until ndiswrapper is resolved, this'll do the job...:???:

---

### Post by nikola.borisof on 2008-05-21
mmm.. The problem that I have is different. I have a hard time connecting to the network. Fortunately i have a big nice log. Please give me soem suggestions. 
I'm running upgraded 8.04 but i also have a brand new 8.04 64bit where i have the same problem with the wireless. Before the upgrade the wireless worked most of the time. It was asking me for username and password every other time and i failed 30% of the time to connect but it was somewhat acceptable. Now I have been able to connect only twice this week. ;( 

The university basically gives us username and password. and also the group password (Private Key Password).


Here is a fat log file that may help:

May 20 11:34:48 nikola-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
May 20 11:34:49 nikola-laptop NetworkManager: <info>  Updating VPN Connections... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Will activate connection 'wlan0/Northwestern'. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) started... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Northwestern' is encrypted, but NO valid key exists.  New key needed. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Northwestern'. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'Northwestern' received. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 20 11:34:50 nikola-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Northwestern' is encrypted, and a key exists.  No new key needed. 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was '0' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4e6f7274687765737465726e' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap PEAP' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "npb853"' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 private_key_passwd <key>' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 fragment_size 1300' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:34:51 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 20 11:34:53 nikola-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 20 11:34:54 nikola-laptop NetworkManager: <info>  Supplicant state changed: 0 
May 20 11:34:55 nikola-laptop avahi-daemon[5752]: Registering new address record for fe80::213:e8ff:fe55:8cb1 on wlan0.*.
May 20 11:34:58 nikola-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 20 11:35:14 nikola-laptop NetworkManager: <info>  Activation (wlan0/wireless): disconnected during association, asking for new key. 
May 20 11:35:14 nikola-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Northwestern'. 
May 20 11:35:18 nikola-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key request for network 'Northwestern' was canceled. 
May 20 11:35:18 nikola-laptop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
May 20 11:35:18 nikola-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Northwestern) 
May 20 11:35:18 nikola-laptop NetworkManager: <info>  Activation (wlan0) failed. 
May 20 11:35:18 nikola-laptop NetworkManager: <info>  Deactivating device wlan0. 
May 20 11:35:19 nikola-laptop avahi-daemon[5752]: Withdrawing address record for fe80::213:e8ff:fe55:8cb1 on wlan0.
May 20 11:35:42 nikola-laptop NetworkManager: <debug> [1211301342.196952] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Northwestern' 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Northwestern 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Deactivating device wlan0. 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Activation (wlan0) started... 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 20 11:35:42 nikola-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Northwestern' is encrypted, and a key exists.  No new key needed. 
May 20 11:35:43 nikola-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 20 11:35:43 nikola-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 20 11:35:43 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was '0' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4e6f7274687765737465726e' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap PEAP' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "npb853"' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 private_key_passwd <key>' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 fragment_size 1300' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  SUP: response was 'OK' 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 20 11:35:44 nikola-laptop NetworkManager: <info>  Supplicant state changed: 0 
May 20 11:35:45 nikola-laptop avahi-daemon[5752]: Registering new address record for fe80::213:e8ff:fe55:8cb1 on wlan0.*.
May 20 11:35:45 nikola-laptop NetworkManager: <info>  Supplicant state changed: 1 
May 20 11:35:45 nikola-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Northwestern'. 
May 20 11:35:45 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 20 11:35:45 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
May 20 11:35:46 nikola-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
May 20 11:35:46 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
May 20 11:35:46 nikola-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
May 20 11:35:46 nikola-laptop dhclient: wmaster0: unknown hardware address type 801
May 20 11:35:48 nikola-laptop dhclient: wmaster0: unknown hardware address type 801
May 20 11:35:48 nikola-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
May 20 11:35:50 nikola-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May 20 11:35:50 nikola-laptop dhclient: DHCPOFFER of 165.124.215.0 from 165.124.112.2
May 20 11:35:50 nikola-laptop dhclient: DHCPREQUEST of 165.124.215.0 on wlan0 to 255.255.255.255 port 67
May 20 11:35:51 nikola-laptop dhclient: DHCPACK of 165.124.215.0 from 165.124.112.2
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Joining mDNS multicast group on interface wlan0.IPv4 with address 165.124.215.0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: New relevant interface wlan0.IPv4 for mDNS.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Registering new address record for 165.124.215.0 on wlan0.IPv4.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Withdrawing address record for 165.124.215.0 on wlan0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 165.124.215.0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Joining mDNS multicast group on interface wlan0.IPv4 with address 165.124.215.0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: New relevant interface wlan0.IPv4 for mDNS.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Registering new address record for 165.124.215.0 on wlan0.IPv4.
May 20 11:35:51 nikola-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
May 20 11:35:51 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 20 11:35:51 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
May 20 11:35:51 nikola-laptop dhclient: bound to 165.124.215.0 -- renewal in 851 seconds.
May 20 11:35:51 nikola-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 20 11:35:51 nikola-laptop NetworkManager: <info>    address 165.124.215.0 
May 20 11:35:51 nikola-laptop NetworkManager: <info>    netmask 255.255.252.0 
May 20 11:35:51 nikola-laptop NetworkManager: <info>    broadcast 165.124.215.255 
May 20 11:35:51 nikola-laptop NetworkManager: <info>    gateway 165.124.212.1 
May 20 11:35:51 nikola-laptop NetworkManager: <info>    nameserver 165.124.49.21 
May 20 11:35:51 nikola-laptop NetworkManager: <info>    nameserver 129.105.49.1 
May 20 11:35:51 nikola-laptop NetworkManager: <info>    domain name 'northwestern.edu' 
May 20 11:35:51 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 20 11:35:51 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
May 20 11:35:51 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Withdrawing address record for 165.124.215.0 on wlan0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 165.124.215.0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Withdrawing address record for fe80::213:e8ff:fe55:8cb1 on wlan0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Joining mDNS multicast group on interface wlan0.IPv4 with address 165.124.215.0.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: New relevant interface wlan0.IPv4 for mDNS.
May 20 11:35:51 nikola-laptop avahi-daemon[5752]: Registering new address record for 165.124.215.0 on wlan0.IPv4.
May 20 11:35:52 nikola-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
May 20 11:35:52 nikola-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May 20 11:35:52 nikola-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
May 20 11:35:52 nikola-laptop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
May 20 11:35:52 nikola-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
May 20 11:35:52 nikola-laptop NetworkManager: <debug> [1211301352.137525] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Northwestern' 
May 20 11:35:52 nikola-laptop NetworkManager: <info>  SWITCH: terminating current connection 'wlan0' because it's no longer valid. 
May 20 11:35:52 nikola-laptop NetworkManager: <info>  Deactivating device wlan0. 
May 20 11:35:52 nikola-laptop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 7188
May 20 11:35:52 nikola-laptop dhclient: killed old client process, removed PID file
May 20 11:35:52 nikola-laptop dhclient: wmaster0: unknown hardware address type 801
May 20 11:35:52 nikola-laptop dhclient: wmaster0: unknown hardware address type 801
May 20 11:35:52 nikola-laptop dhclient: DHCPRELEASE on wlan0 to 129.105.49.10 port 67
May 20 11:35:52 nikola-laptop avahi-daemon[5752]: Withdrawing address record for 165.124.215.0 on wlan0.
May 20 11:35:52 nikola-laptop avahi-daemon[5752]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 165.124.215.0.
May 20 11:35:52 nikola-laptop avahi-daemon[5752]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 20 11:35:52 nikola-laptop ntpdate[7356]: can't find host ntp.ubuntu.com

---

