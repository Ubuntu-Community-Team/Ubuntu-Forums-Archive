---
title: "Scripts in /etc/NetworkManager/dispatcher.d aren't running"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by nick167 on 2015-01-17
I have a fresh install of 14.04 on my mbp 8.1 (though I'm using gnome classic (metacity) if that's at all relevant). My understanding from googling is that nm_dispatcher should run scripts (provided they're owned by root, got file permissions 755 etc.) in /etc/NetworkManager/dispatcher.d. As far as I can tell from the logs, nm_dispatcher doesn't even attempt to run these scripts when I connect to a wireless network. I'm not really sure how to work out what's going wrong?

The only script currently in /etc/NetworkManager/dispatcher.d is the original 01ifupdown script:

```
nick@nick-MacBookPro:/etc/NetworkManager/dispatcher.d$ ls -l
total 4
-rwxr-xr-x 1 root root 1131 Apr 10  2014 01ifupdown
```

Here's what /var/log/syslog gets when I connect to a wireless network:

```
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) starting connection 'freeTether'
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> NetworkManager state is now CONNECTING
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0/wireless): access point 'freeTether' has security, but secrets are required.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0/wireless): connection 'freeTether' has security, and secrets exist.  No new secrets needed.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Config: added 'ssid' value 'freeTether'
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Config: added 'scan_ssid' value '1'
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Config: added 'psk' value '<omitted>'
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Config: set interface ap_scan to 1
Jan 18 12:00:53 nick-MacBookPro wpa_supplicant[1073]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 18 12:00:58 nick-MacBookPro wpa_supplicant[1073]: wlan0: Trying to associate with ***** (SSID='freeTether' freq=2412 MHz)
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): supplicant interface state: disconnected -> associating
Jan 18 12:00:58 nick-MacBookPro wpa_supplicant[1073]: wlan0: Associated with *****
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan 18 12:00:58 nick-MacBookPro wpa_supplicant[1073]: wlan0: WPA: Key negotiation completed with ***** [PTK=CCMP GTK=TKIP]
Jan 18 12:00:58 nick-MacBookPro wpa_supplicant[1073]: wlan0: CTRL-EVENT-CONNECTED - Connection to ***** completed [id=0 id_str=]
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'freeTether'.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> dhclient started with pid 22738
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan 18 12:00:58 nick-MacBookPro avahi-daemon[869]: Withdrawing address record for ***** on wlan0.
Jan 18 12:00:58 nick-MacBookPro avahi-daemon[869]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::e6ce:8fff:fe41:ffc.
Jan 18 12:00:58 nick-MacBookPro avahi-daemon[869]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 18 12:00:58 nick-MacBookPro dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jan 18 12:00:58 nick-MacBookPro dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jan 18 12:00:58 nick-MacBookPro dhclient: All rights reserved.
Jan 18 12:00:58 nick-MacBookPro dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan 18 12:00:58 nick-MacBookPro dhclient: 
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 18 12:00:58 nick-MacBookPro dhclient: Listening on LPF/wlan0/*****
Jan 18 12:00:58 nick-MacBookPro dhclient: Sending on   LPF/wlan0/*****
Jan 18 12:00:58 nick-MacBookPro dhclient: Sending on   Socket/fallback
Jan 18 12:00:58 nick-MacBookPro dhclient: DHCPREQUEST of 192.168.100.51 on wlan0 to 255.255.255.255 port 67 (xid=0x590a71c5)
Jan 18 12:00:58 nick-MacBookPro dhclient: DHCPACK of 192.168.100.51 from 192.168.100.1
Jan 18 12:00:58 nick-MacBookPro dhclient: bound to 192.168.100.51 -- renewal in 3139 seconds.
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info>   address 192.168.100.51
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info>   prefix 24 (255.255.255.0)
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info>   gateway 192.168.100.1
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info>   nameserver '192.168.100.1'
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan 18 12:00:58 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jan 18 12:00:58 nick-MacBookPro avahi-daemon[869]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.100.51.
Jan 18 12:00:58 nick-MacBookPro avahi-daemon[869]: New relevant interface wlan0.IPv4 for mDNS.
Jan 18 12:00:58 nick-MacBookPro avahi-daemon[869]: Registering new address record for 192.168.100.51 on wlan0.IPv4.
Jan 18 12:00:59 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jan 18 12:00:59 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jan 18 12:00:59 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 18 12:00:59 nick-MacBookPro NetworkManager[1023]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jan 18 12:00:59 nick-MacBookPro NetworkManager[1023]: <info> Policy set 'freeTether' (wlan0) as default for IPv4 routing and DNS.
Jan 18 12:00:59 nick-MacBookPro NetworkManager[1023]: <info> Writing DNS information to /sbin/resolvconf
Jan 18 12:00:59 nick-MacBookPro dnsmasq[1145]: setting upstream servers from DBus
Jan 18 12:00:59 nick-MacBookPro dnsmasq[1145]: using nameserver 192.168.100.1#53
Jan 18 12:01:00 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) successful, device activated.
Jan 18 12:01:00 nick-MacBookPro dbus[780]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 18 12:01:00 nick-MacBookPro dbus[780]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 18 12:01:00 nick-MacBookPro avahi-daemon[869]: Joining mDNS multicast group on interface wlan0.IPv6 with address *****.
Jan 18 12:01:00 nick-MacBookPro avahi-daemon[869]: New relevant interface wlan0.IPv6 for mDNS.
Jan 18 12:01:00 nick-MacBookPro avahi-daemon[869]: Registering new address record for ***** on wlan0.*.
Jan 18 12:01:00 nick-MacBookPro whoopsie[1054]: message repeated 3 times: [ offline]
Jan 18 12:01:00 nick-MacBookPro whoopsie[1054]: online
Jan 18 12:01:08 nick-MacBookPro ntpdate[22833]: adjust time server ***** offset -0.027658 sec
Jan 18 12:01:19 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan 18 12:01:19 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 18 12:01:19 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 18 12:01:19 nick-MacBookPro NetworkManager[1023]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 18 12:01:46 nick-MacBookPro wpa_supplicant[1073]: wlan0: CTRL-EVENT-SCAN-STARTED 
```

And here's what /var/log/syslog gets when I disconnect from the network.

```
Jan 18 11:59:10 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jan 18 11:59:10 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Jan 18 11:59:10 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 21914
Jan 18 11:59:10 nick-MacBookPro avahi-daemon[869]: Withdrawing address record for ***** on wlan0.
Jan 18 11:59:10 nick-MacBookPro avahi-daemon[869]: Leaving mDNS multicast group on interface wlan0.IPv6 with address *****.
Jan 18 11:59:10 nick-MacBookPro avahi-daemon[869]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan 18 11:59:10 nick-MacBookPro avahi-daemon[869]: Withdrawing address record for 192.168.100.51 on wlan0.
Jan 18 11:59:10 nick-MacBookPro avahi-daemon[869]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.100.51.
Jan 18 11:59:10 nick-MacBookPro avahi-daemon[869]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan 18 11:58:53 nick-MacBookPro wpa_supplicant[1073]: message repeated 13 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 18 11:59:10 nick-MacBookPro wpa_supplicant[1073]: wlan0: CTRL-EVENT-DISCONNECTED bssid=***** reason=3 locally_generated=1
Jan 18 11:59:11 nick-MacBookPro wpa_supplicant[1073]: nl80211: Was expecting local disconnect but got another disconnect event first
Jan 18 11:59:11 nick-MacBookPro NetworkManager[1023]: <warn> DNS: plugin dnsmasq update failed
Jan 18 11:59:11 nick-MacBookPro NetworkManager[1023]: <info> Removing DNS information from /sbin/resolvconf
Jan 18 11:59:11 nick-MacBookPro dnsmasq[1145]: setting upstream servers from DBus
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.944558] cfg80211: Calling CRDA to update world regulatory domain
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.976957] cfg80211: World regulatory domain updated:
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.976965] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.976970] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.976974] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.976977] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.976981] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 18 11:59:11 nick-MacBookPro kernel: [16707.976984] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 18 11:59:11 nick-MacBookPro NetworkManager[1023]: <info> NetworkManager state is now DISCONNECTED
Jan 18 11:35:05 nick-MacBookPro whoopsie[1054]: message repeated 2 times: [ online]
Jan 18 11:59:11 nick-MacBookPro whoopsie[1054]: offline
Jan 18 11:59:11 nick-MacBookPro wpa_supplicant[1073]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 18 11:59:11 nick-MacBookPro NetworkManager[1023]: <warn> Connection disconnected (reason -3)
Jan 18 11:59:11 nick-MacBookPro dbus[780]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 18 11:59:11 nick-MacBookPro NetworkManager[1023]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jan 18 11:59:11 nick-MacBookPro dbus[780]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 18 11:59:12 nick-MacBookPro avahi-daemon[869]: Joining mDNS multicast group on interface wlan0.IPv6 with address *****.
Jan 18 11:59:12 nick-MacBookPro avahi-daemon[869]: New relevant interface wlan0.IPv6 for mDNS.
Jan 18 11:59:12 nick-MacBookPro avahi-daemon[869]: Registering new address record for ***** on wlan0.*.
```

Here's the wireless-info.txt I get as well..

```


########## wireless info START ##########


Report from: 18 Jan 2015 12:27 AEDT +1100


Booted last: 17 Jan 2015 19:10 AEDT +1100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME Flashback (Metacity)


##### lspci #############################


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3


03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00d6]
    Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 004: ID 04e8:6033 Samsung Electronics Co., Ltd 
Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 005: ID 05ac:0245 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 009: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.100.51  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::e6ce:8fff:fe41:ffc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1464428 errors:0 dropped:0 overruns:0 frame:79377
          TX packets:549894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2153892614 (2.1 GB)  TX bytes:59064628 (59.0 MB)
          Interrupt:17 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"freeTether"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'freeTether' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [freeTether] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *freeTether:     Infra, <MAC 'freeTether' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2


  IPv4 Settings:
    Address:         192.168.100.51
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1


    DNS:             192.168.100.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Telstra41182B]] (600 root)
[connection] id=Telstra41182B | type=802-11-wireless
[802-11-wireless] ssid=Telstra41182B | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/freeTether]] (600 root)
[connection] id=freeTether | type=802-11-wireless
[802-11-wireless] ssid=freeTether | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Australia/Hobart (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


wlan0     26 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'freeTether' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"freeTether"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[wl]
filename:       /lib/modules/3.13.0-44-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-44-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:5E:E8:B6:65:D0:55:58:A1:DE:E8:E3:1B:F1:6E:B8:DF:8F:D8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b4 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[18422.460609] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############

```

---

