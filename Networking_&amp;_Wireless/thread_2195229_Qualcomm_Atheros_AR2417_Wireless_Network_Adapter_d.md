---
title: "Qualcomm Atheros AR2417 Wireless Network Adapter disconnects often in xubuntu 13.10"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by karthik_jce on 2013-12-23
Hi,

I recently installed xubuntu 13.10 on my Desktop which has a wireless LAN card. Initially the computer connects to the network and works for some time. Then suddenly no communication will happen whereas the network would show as connection and after sometime the network would show as disconnected.

It would reconnect automatically after few minutes, or it starts working if i disable wifi and re-enable it from the notification area.

Please find below the details of the wireless lan card,

id:	
network
description: 	Wireless interface
product: 	AR2417 Wireless Network Adapter [AR5007G 802.11bg] [168C:1D]
vendor: 	Qualcomm Atheros [168C]
physical id: 	
0
bus info: 	
pci@0000:01:00.0
logical name: 	
wlan0
version: 	01
serial: 	b0:48:7a:99:9f:45
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	ath5k
driverversion	=	3.11.0-12-generic
firmware	=	N/A
ip	=	192.168.1.4
latency	=	168
link	=	yes
maxlatency	=	28
mingnt	=	10
multicast	=	yes
wireless	=	IEEE 802.11bg
resources:	
irq	:	17
memory	:	dbdf0000-dbdfffff


In the syslog i.e /var/log/syslog, I find these messages getting printed again and again,

Dec 23 09:53:27 karthik kernel: [ 2097.052271] cfg80211: Calling CRDA to update world regulatory domain
Dec 23 09:53:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Dec 23 09:53:27 karthik NetworkManager[664]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.
Dec 23 09:53:27 karthik NetworkManager[664]: <info> (wlan0): device state change: activated -> need-auth (reason 'supplicant-disconnect') [100 60 8]
Dec 23 09:53:27 karthik kernel: [ 2097.061079] cfg80211: World regulatory domain updated:
Dec 23 09:53:27 karthik kernel: [ 2097.061091] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 23 09:53:27 karthik kernel: [ 2097.061097] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:53:27 karthik kernel: [ 2097.061101] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:53:27 karthik kernel: [ 2097.061106] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:53:27 karthik kernel: [ 2097.061110] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:53:27 karthik kernel: [ 2097.061114] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:53:27 karthik whoopsie[1011]: offline
Dec 23 09:53:27 karthik dbus[444]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 23 09:53:27 karthik dbus[444]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 23 09:53:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Dec 23 09:53:36 karthik NetworkManager[664]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 23 09:53:36 karthik NetworkManager[664]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 23 09:53:36 karthik NetworkManager[664]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Activation (wlan0/wireless): connection 'K Karthigeyan' has security, and secrets exist.  No new secrets needed.
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Config: added 'ssid' value 'K Karthigeyan'
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Config: added 'scan_ssid' value '1'
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Config: added 'auth_alg' value 'OPEN'
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Config: added 'psk' value '<omitted>'
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Config: set interface ap_scan to 1
Dec 23 09:53:36 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: inactive -> scanning
Dec 23 09:53:37 karthik wpa_supplicant[798]: wlan0: SME: Trying to authenticate with d4:4c:24:2b:ed:2c (SSID='K Karthigeyan' freq=2412 MHz)
Dec 23 09:53:37 karthik kernel: [ 2106.620691] wlan0: authenticate with d4:4c:24:2b:ed:2c
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 23 09:53:37 karthik kernel: [ 2106.625352] wlan0: send auth to d4:4c:24:2b:ed:2c (try 1/3)
Dec 23 09:53:37 karthik wpa_supplicant[798]: wlan0: Trying to associate with d4:4c:24:2b:ed:2c (SSID='K Karthigeyan' freq=2412 MHz)
Dec 23 09:53:37 karthik kernel: [ 2106.804196] wlan0: authenticated
Dec 23 09:53:37 karthik kernel: [ 2106.804449] ath5k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
Dec 23 09:53:37 karthik kernel: [ 2106.808066] wlan0: associate with d4:4c:24:2b:ed:2c (try 1/3)
Dec 23 09:53:37 karthik wpa_supplicant[798]: wlan0: Associated with d4:4c:24:2b:ed:2c
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 23 09:53:37 karthik kernel: [ 2106.810408] wlan0: RX AssocResp from d4:4c:24:2b:ed:2c (capab=0x411 status=0 aid=1)
Dec 23 09:53:37 karthik kernel: [ 2106.810868] wlan0: associated
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: associating -> associated
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Dec 23 09:53:37 karthik wpa_supplicant[798]: wlan0: WPA: Key negotiation completed with d4:4c:24:2b:ed:2c [PTK=TKIP GTK=TKIP]
Dec 23 09:53:37 karthik wpa_supplicant[798]: wlan0: CTRL-EVENT-CONNECTED - Connection to d4:4c:24:2b:ed:2c completed (reauth) [id=0 id_str=]
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: group handshake -> completed
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'K Karthigeyan'.
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 23 09:53:37 karthik NetworkManager[664]: (nm-device.c:2049):dhcp4_start: runtime check failed: (priv->dhcp4_client == NULL)
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 4438
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 23 09:53:37 karthik NetworkManager[664]: <info> dhclient started with pid 4561
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Beginning IP6 addrconf.
Dec 23 09:53:37 karthik avahi-daemon[559]: Withdrawing address record for fe80::b248:7aff:fe99:9f45 on wlan0.
Dec 23 09:53:37 karthik avahi-daemon[559]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::b248:7aff:fe99:9f45.
Dec 23 09:53:37 karthik avahi-daemon[559]: Interface wlan0.IPv6 no longer relevant for mDNS.
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 23 09:53:37 karthik dhclient: Internet Systems Consortium DHCP Client 4.2.4
Dec 23 09:53:37 karthik dhclient: Copyright 2004-2012 Internet Systems Consortium.
Dec 23 09:53:37 karthik dhclient: All rights reserved.
Dec 23 09:53:37 karthik dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 23 09:53:37 karthik dhclient: 
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 23 09:53:37 karthik dhclient: Listening on LPF/wlan0/b0:48:7a:99:9f:45
Dec 23 09:53:37 karthik dhclient: Sending on   LPF/wlan0/b0:48:7a:99:9f:45
Dec 23 09:53:37 karthik dhclient: Sending on   Socket/fallback
Dec 23 09:53:37 karthik dhclient: DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67 (xid=0x3ce0aa2a)
Dec 23 09:53:37 karthik dhclient: DHCPACK of 192.168.1.4 from 192.168.1.1
Dec 23 09:53:37 karthik dhclient: bound to 192.168.1.4 -- renewal in 39903 seconds.
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec 23 09:53:37 karthik NetworkManager[664]: <info>   address 192.168.1.4
Dec 23 09:53:37 karthik NetworkManager[664]: <info>   prefix 24 (255.255.255.0)
Dec 23 09:53:37 karthik NetworkManager[664]: <info>   gateway 192.168.1.1
Dec 23 09:53:37 karthik NetworkManager[664]: <info>   nameserver '192.168.1.1'
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 23 09:53:37 karthik NetworkManager[664]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Dec 23 09:53:37 karthik NetworkManager[664]: <info> Activation (wlan0) successful, device activated.
Dec 23 09:53:37 karthik dbus[444]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 23 09:53:37 karthik dbus[444]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 23 09:53:38 karthik whoopsie[1011]: online
Dec 23 09:53:38 karthik avahi-daemon[559]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::b248:7aff:fe99:9f45.
Dec 23 09:53:38 karthik avahi-daemon[559]: New relevant interface wlan0.IPv6 for mDNS.
Dec 23 09:53:38 karthik avahi-daemon[559]: Registering new address record for fe80::b248:7aff:fe99:9f45 on wlan0.*.
Dec 23 09:53:38 karthik whoopsie[1011]: online
Dec 23 09:53:39 karthik whoopsie[1011]: online
Dec 23 09:53:45 karthik ntpdate[4609]: adjust time server 91.189.94.4 offset -0.011020 sec
Dec 23 09:53:57 karthik NetworkManager[664]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec 23 09:53:57 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 23 09:53:57 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 23 09:53:57 karthik NetworkManager[664]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 23 09:55:24 karthik whoopsie[1011]: online
Dec 23 09:56:14  whoopsie[1011]: last message repeated 2 times
Dec 23 09:56:14 karthik wpa_supplicant[798]: wlan0: CTRL-EVENT-DISCONNECTED bssid=d4:4c:24:2b:ed:2c reason=4
Dec 23 09:56:14 karthik kernel: [ 2264.047153] cfg80211: Calling CRDA to update world regulatory domain
Dec 23 09:56:14 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 23 09:56:14 karthik kernel: [ 2264.053865] cfg80211: World regulatory domain updated:
Dec 23 09:56:14 karthik kernel: [ 2264.053873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 23 09:56:14 karthik kernel: [ 2264.053878] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:56:14 karthik kernel: [ 2264.053882] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:56:14 karthik kernel: [ 2264.053886] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:56:14 karthik kernel: [ 2264.053890] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:56:14 karthik kernel: [ 2264.053894] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 09:56:14 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 23 09:56:27 karthik wpa_supplicant[798]: wlan0: SME: Trying to authenticate with d4:4c:24:2b:ed:2c (SSID='K Karthigeyan' freq=2412 MHz)
Dec 23 09:56:27 karthik kernel: [ 2276.776897] wlan0: authenticate with d4:4c:24:2b:ed:2c
Dec 23 09:56:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 23 09:56:27 karthik kernel: [ 2276.781625] wlan0: send auth to d4:4c:24:2b:ed:2c (try 1/3)
Dec 23 09:56:27 karthik wpa_supplicant[798]: wlan0: Trying to associate with d4:4c:24:2b:ed:2c (SSID='K Karthigeyan' freq=2412 MHz)
Dec 23 09:56:27 karthik kernel: [ 2277.057368] wlan0: authenticated
Dec 23 09:56:27 karthik kernel: [ 2277.057650] ath5k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
Dec 23 09:56:27 karthik kernel: [ 2277.060042] wlan0: associate with d4:4c:24:2b:ed:2c (try 1/3)
Dec 23 09:56:27 karthik kernel: [ 2277.062375] wlan0: RX AssocResp from d4:4c:24:2b:ed:2c (capab=0x411 status=0 aid=1)
Dec 23 09:56:27 karthik kernel: [ 2277.062926] wlan0: associated
Dec 23 09:56:27 karthik wpa_supplicant[798]: wlan0: Associated with d4:4c:24:2b:ed:2c
Dec 23 09:56:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 23 09:56:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: associating -> associated
Dec 23 09:56:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Dec 23 09:56:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Dec 23 09:56:27 karthik wpa_supplicant[798]: wlan0: WPA: Key negotiation completed with d4:4c:24:2b:ed:2c [PTK=TKIP GTK=TKIP]
Dec 23 09:56:27 karthik wpa_supplicant[798]: wlan0: CTRL-EVENT-CONNECTED - Connection to d4:4c:24:2b:ed:2c completed (reauth) [id=0 id_str=]
Dec 23 09:56:27 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: group handshake -> completed
Dec 23 09:56:36 karthik whoopsie[1011]: online
Dec 23 09:57:14 karthik wpa_supplicant[798]: wlan0: WPA: Group rekeying completed with d4:4c:24:2b:ed:2c [GTK=TKIP]
Dec 23 09:57:55 karthik whoopsie[1011]: online
Dec 23 09:58:18 karthik wpa_supplicant[798]: wlan0: CTRL-EVENT-DISCONNECTED bssid=d4:4c:24:2b:ed:2c reason=4
Dec 23 09:58:18 karthik kernel: [ 2387.582300] cfg80211: Calling CRDA to update world regulatory domain
Dec 23 09:58:18 karthik NetworkManager[664]: <info> (wlan0): supplicant interface state: completed -> disconnected


Please suggest any to make this work. 


Regards
Karthigeyan

---

### Post by varunendra on 2013-12-23
> **karthik_jce said:**
> 
Dec 23 09:53:36 karthik NetworkManager[664]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
....
Dec 23 09:53:37 karthik kernel: [ 2106.804449] ath5k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
....
Dec 23 09:53:37 karthik wpa_supplicant[798]: wlan0: WPA: Key negotiation completed with d4:4c:24:2b:ed:2c [PTK=TKIP GTK=TKIP]

Are you using WPA or WPA/WPA2 mixed mode with TKIP? It is highly recommended to avoid TKIP and use pure WPA**2**-PSK with AES/CCMP instead.

Change the encryption in the router to that, and if that alone doesn't solve the problem, try this command in Ubuntu -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot. If it helps, it can be made permanent.

If none of these changes help improving the connectivity, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

