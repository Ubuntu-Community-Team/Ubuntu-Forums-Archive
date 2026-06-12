---
title: "Feisty ipw3945 - NO WPA"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by kspider on 2007-06-02
Please help.  I've been searching for days and can't find anything like this.

I just got an Inspiron 6400 with Intel wireless.  Using the Feisty Restricted Drivers Manager, I enabled the ipw3945 driver.  Using Network Manager, wireless works for everything except WPA.   I can connect to unencrypted networks and I can also connect to WEP networks.  For WPA, I am prompted for the shared key, but then Network Manager never connects.

Here's some /var/log/syslog (sorry, this is long, but I'm hoping someone out there can decipher it):

```
Jun  2 09:04:27 linspiron6400 NetworkManager: <debug info>^I[1180789467.235425] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'Sic' 
Jun  2 09:04:27 linspiron6400 NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Sic 
Jun  2 09:04:27 linspiron6400 NetworkManager: <information>^IDeactivating device eth1. 
Jun  2 09:04:27 linspiron6400 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jun  2 09:04:27 linspiron6400 NetworkManager: <information>^IDevice eth1 activation scheduled... 
Jun  2 09:04:27 linspiron6400 NetworkManager: <information>^IDeactivating device eth0. 
Jun  2 09:04:27 linspiron6400 dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5887
Jun  2 09:04:27 linspiron6400 dhclient: killed old client process, removed PID file
Jun  2 09:04:27 linspiron6400 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jun  2 09:04:27 linspiron6400 avahi-daemon[4936]: Withdrawing address record for 192.168.1.128 on eth0.
Jun  2 09:04:27 linspiron6400 avahi-daemon[4936]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.128.
Jun  2 09:04:27 linspiron6400 avahi-daemon[4936]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  2 09:04:27 linspiron6400 avahi-autoipd(eth0)[7057]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jun  2 09:04:27 linspiron6400 avahi-autoipd(eth0)[7057]: Successfully called chroot().
Jun  2 09:04:27 linspiron6400 avahi-autoipd(eth0)[7057]: Successfully dropped root privileges.
Jun  2 09:04:27 linspiron6400 avahi-autoipd(eth0)[7057]: fopen() failed: Permission denied
Jun  2 09:04:27 linspiron6400 avahi-autoipd(eth0)[7057]: Starting with address 169.254.10.6
Jun  2 09:04:28 linspiron6400 avahi-daemon[4936]: Withdrawing address record for fe80::219:b9ff:fe74:cbca on eth0.
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) started... 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1/wireless): access point 'Sic' is encrypted, but NO valid key exists.  New key needed. 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) New wireless user key requested for network 'Sic'. 
Jun  2 09:04:28 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun  2 09:04:32 linspiron6400 avahi-autoipd(eth0)[7057]: Callout BIND, address 169.254.10.6 on interface eth0
Jun  2 09:04:32 linspiron6400 avahi-daemon[4936]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.10.6.
Jun  2 09:04:32 linspiron6400 avahi-daemon[4936]: New relevant interface eth0.IPv4 for mDNS.
Jun  2 09:04:32 linspiron6400 avahi-daemon[4936]: Registering new address record for 169.254.10.6 on eth0.IPv4.
Jun  2 09:04:36 linspiron6400 avahi-autoipd(eth0)[7057]: Successfully claimed IP address 169.254.10.6
Jun  2 09:04:36 linspiron6400 avahi-autoipd(eth0)[7057]: fopen() failed: Permission denied
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1) New wireless user key for network 'Sic' received. 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1/wireless): access point 'Sic' is encrypted, and a key exists.  No new key needed. 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was '0' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 536963' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 proto WPA' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 psk <key>' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 group TKIP' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^ISUP: response was 'OK' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): Global control interface '/var/run/wpa_supplicant-global' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX global ctrl_iface - hexdump_ascii(len=49): 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h1__wext_/var/ru 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      09                                                _                
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): Initializing interface (2) 'eth1' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): EAPOL: SUPP_PAE entering state DISCONNECTED 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): EAPOL: SUPP_BE entering state INITIALIZE 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): EAP: EAP entering state DISABLED 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): EAPOL: External notification - portEnabled=0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): EAPOL: External notification - portValid=0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): SIOCGIWRANGE: WE(compiled)=21 WE(source)=16 enc_capa=0xf 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):   capabilities: key_mgmt 0xf enc 0xf 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): WEXT: Operstate: linkmode=1, operstate=5 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): 2 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): wpa_driver_wext_set_wpa 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): wpa_driver_wext_set_countermeasures 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): wpa_driver_wext_set_drop_unencrypted 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): Setting scan request: 0 sec 100000 usec 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): Added interface eth1 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): Wireless event: cmd=0x8b06 len=8 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=9): 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=11): 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: ADD_NETWORK 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=25): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: value - hexdump_ascii(len=6): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): ssid - hexdump_ascii(len=3): 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      53 69 63                                          Sic              
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):  - hexdump_ascii(len=23): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: SET_NETWORK id=0 name='proto' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: value - hexdump_ascii(len=3): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): proto: 0x1 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=30): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: value - hexdump_ascii(len=7): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): key_mgmt: 0x2 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=82): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: SET_NETWORK id=0 name='psk' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: value - hexdump_ascii(len=64): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): PSK - hexdump(len=32): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=27): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: SET_NETWORK id=0 name='pairwise' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): pairwise: 0x8 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=24): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: SET_NETWORK id=0 name='group' 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): group: 0x8 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): RX ctrl_iface - hexdump_ascii(len=16): 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): CTRL_IFACE: ENABLE_NETWORK id=0 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): Setting scan request: 0 sec 0 usec 
Jun  2 09:05:06 linspiron6400 NetworkManager: <information>^Iwpa_supplicant(7115): State: DISCONNECTED -> SCANNING 

```

Thanks a lot for your help.

---

### Post by hkahwaji on 2007-06-04
Hi

 I am using Intel 3945 on my notebook and I was able to set up WPA with TKIP. I followed the intructions that wiedman has posted. 

See the link.

let me know if that does not work


[http://ubuntuforums.org/showthread.php?t=202834&highlight=setting+up+WPA](http://ubuntuforums.org/showthread.php?t=202834&highlight=setting+up+WPA)

---

### Post by kspider on 2007-06-04
Thanks for replying hkahwaji.  It turns out that this was a couple of problems that made things seem more confusing than they really are.

At work, the WPA-PSK network that I want to connect to is not broadcasting its SSID.  This causes problems with NetworkManager that has been reported as a bug.  I'm probably going to have to configure my wireless adapter in /etc/interfaces manually.

At home, I was using OpenWRT for the firmware on my Linksys router.  For whatever reason, WPA wasn't working right with it - I couldn't connect using WPA with another machine.  So, I tried dd-wrt and I was able to set up a WPA WLAN that I could connect to.  I'm not really sure why I was having that problem with OpenWRT.  Its a shame - I really liked that firmware.

BTW - I used the Network Manager applet to connect to my WPA-PSK WLAN at home.  The post you referred to is ok if you prefer manually configuring everything.  However, if you just want to connect to a WPA WLAN (that IS broadcasting its SSID), you should be able to do it using the Network Manager applet.

Thanks.

---

