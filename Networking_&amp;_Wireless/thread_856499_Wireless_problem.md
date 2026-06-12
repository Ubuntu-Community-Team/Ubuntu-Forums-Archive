---
title: "Wireless problem"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by mariom48 on 2008-07-11
Hello 

I need some help with my wireless issues I have a Linksys wireless router and a Cisco 350 AP that I used to get more access around the house.

My problem is that if i try to access the net through my CISCO 350 AP I can not do it I had no problems in the past with other linux distros until now. I look through the message log but I can not see anything clear that points to a specific problem.

If I used the Linksys no problem which is what going out right now.

I have a Compaq Nc6000 when I run lspci -v this what I get:

 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
	Subsystem: Compaq Computer Corporation Unknown device 00e5
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 90080000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

Results from iwconfig are:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"chingado"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:2A:7D:F8   
          Bit Rate:18 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/70  Signal level=-77 dBm  Noise level=-99 dBm
          Rx invalid nwid:228077  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Does anybody has encountered any problem like this?
Could anybody help me please? I do not want to go back to MS.

Thank you very much.
Regards,
Mario Mira

---

### Post by DarkerViolet on 2008-07-25
Are you still having problems?  I also have an NC6000 and have been able to get wireless working on it since 7.X.

Please let us know if you're still wireless-less... :lolflag:

---

### Post by mariom48 on 2008-07-28
Hello, thank you very much for your response. I am still having the same problems with my CISCO AP 350 connectivity/access.

Here it's the output of the syslog.

Jul 28 14:39:48 eljocote NetworkManager: <debug> [1217281188.282110] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '****' 
Jul 28 14:39:48 eljocote NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ath0 / **** 
Jul 28 14:39:48 eljocote NetworkManager: <info>  Deactivating device ath0. 
Jul 28 14:39:48 eljocote dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 6855
Jul 28 14:39:48 eljocote dhclient: killed old client process, removed PID file
Jul 28 14:39:48 eljocote dhclient: wifi0: unknown hardware address type 801
Jul 28 14:39:48 eljocote dhclient: wifi0: unknown hardware address type 801
Jul 28 14:39:48 eljocote dhclient: DHCPRELEASE on ath0 to 192.168.1.1 port 67
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Withdrawing address record for 192.168.1.103 on ath0.
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.103.
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Interface ath0.IPv4 no longer relevant for mDNS.
Jul 28 14:39:49 eljocote avahi-daemon[4996]: Withdrawing address record for fe80::211:85ff:fe1b:4fad on ath0.
Jul 28 14:39:49 eljocote NetworkManager: <info>  Device ath0 activation scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) started... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0/wireless): access point '****' is encrypted, but NO valid key exists.  New key needed. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key requested for network '****'. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key for network '****' received. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0/wireless): access point '****' is encrypted, and a key exists.  No new key needed. 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was '0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7075746f' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 28 14:40:21 eljocote NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jul 28 14:40:53 eljocote last message repeated 2 times
Jul 28 14:41:57 eljocote last message repeated 4 times
Jul 28 14:42:05 eljocote NetworkManager: <info>  Activation (ath0/wireless): association took too long (>120s), asking for new key. 
Jul 28 14:42:05 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key requested for network '****'. 
        
I also notice a meesage saying that a Hardware device ID 801 is not supported it.

Do you know if Cisco 350 is supported?

Thank you very much for you help.

Regards,
Mario

---

### Post by mariom48 on 2008-07-28
Hello, thank you very much for your response. I am still having the same problems with my CISCO AP 350 connectivity/access.

Here it's the output of the syslog.

Jul 28 14:39:48 eljocote NetworkManager: <debug> [1217281188.282110] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '****' 
Jul 28 14:39:48 eljocote NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ath0 / **** 
Jul 28 14:39:48 eljocote NetworkManager: <info>  Deactivating device ath0. 
Jul 28 14:39:48 eljocote dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 6855
Jul 28 14:39:48 eljocote dhclient: killed old client process, removed PID file
Jul 28 14:39:48 eljocote dhclient: wifi0: unknown hardware address type 801
Jul 28 14:39:48 eljocote dhclient: wifi0: unknown hardware address type 801
Jul 28 14:39:48 eljocote dhclient: DHCPRELEASE on ath0 to 192.168.1.1 port 67
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Withdrawing address record for 192.168.1.103 on ath0.
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.103.
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Interface ath0.IPv4 no longer relevant for mDNS.
Jul 28 14:39:49 eljocote avahi-daemon[4996]: Withdrawing address record for fe80::211:85ff:fe1b:4fad on ath0.
Jul 28 14:39:49 eljocote NetworkManager: <info>  Device ath0 activation scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) started... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0/wireless): access point '****' is encrypted, but NO valid key exists.  New key needed. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key requested for network '****'. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key for network '****' received. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0/wireless): access point '****' is encrypted, and a key exists.  No new key needed. 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was '0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7075746f' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 28 14:40:21 eljocote NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jul 28 14:40:53 eljocote last message repeated 2 times
Jul 28 14:41:57 eljocote last message repeated 4 times
Jul 28 14:42:05 eljocote NetworkManager: <info>  Activation (ath0/wireless): association took too long (>120s), asking for new key. 
Jul 28 14:42:05 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key requested for network '****'. 
        
I also notice a meesage saying that a Hardware device ID 801 is not supported it.

Do you know if Cisco 350 is supported?

Thank you very much for you help.

Regards,
Mario

---

