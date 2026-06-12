---
title: "Problem with wireless on Dell D620"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by K_V_B on 2007-12-31
My laptop is a Dell Latitude D620. I've installed Ubuntu 7.10 on it and have some troubles getting wireless networking to work.

Currently I can use the networkmanager applet in KDE to connect to a wired network, and to connect to open wireless networks. The connection fails when I try to connect to a WPA secured network.

When trying to connect to a WPA secured network I get prompted for a key. After entering this key not a lot happens, until I some time out is reached and an error message is displayed. 

Some info:
```
krist@tell:/etc/network$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:E9:14:35:7C   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:529   Missed beacon:0

krist@tell:/etc/network$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:14:35:7C
                    ESSID:"Loveld"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-52 dBm  Noise level=-52 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 124ms ago

```
 The network card built in is an intel  PRO/Wireless 3945ABG

Lookign at my daemon.log I get the impression that something is not working:

```
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) started... 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1/wireless): access point 'Loveld' is encrypted, but NO valid 
key exists.  New key needed. 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Loveld'. 
Dec 31 15:54:19 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Dec 31 15:54:36 ubuntu NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Loveld' received. 
Dec 31 15:54:36 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 31 15:54:36 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec 31 15:54:36 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec 31 15:54:36 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec 31 15:54:36 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec 31 15:54:36 ubuntu NetworkManager: <info>  Activation (eth1/wireless): access point 'Loveld' is encrypted, and a key exi
sts.  No new key needed. 
Dec 31 15:54:37 ubuntu NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Dec 31 15:54:37 ubuntu NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I'
 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was '0' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4c6f76656c64' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Dec 31 15:54:38 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Dec 31 15:55:00 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Dec 31 15:55:00 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: Resource temporarily unavailable 
Dec 31 15:55:38 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Dec 31 15:55:38 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: Resource temporarily unavailable 
Dec 31 15:56:08 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Dec 31 15:56:08 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: Resource temporarily unavailable 
Dec 31 15:56:16 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Dec 31 15:56:16 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: Resource temporarily unavailable 
Dec 31 15:56:38 ubuntu NetworkManager: <info>  Activation (eth1/wireless): association took too long (>120s), failing activation. 
Dec 31 15:56:38 ubuntu NetworkManager: <info>  Activation (eth1) failure scheduled... 
Dec 31 15:56:38 ubuntu NetworkManager: <info>  Activation (eth1) failed for access point (Loveld) 
Dec 31 15:56:38 ubuntu NetworkManager: <info>  Activation (eth1) failed. 
Dec 31 15:56:38 ubuntu NetworkManager: <info>  Deactivating device eth1. 


```
What I asume here is that up to phase 2 (of 5) of whatever NetworkManager does worked fine. After that it went wrong, with these "Resource unavailable" errors. At one moment NetworkManager just gave up.

So what's going on? Is this just a NetworkManager problem? A bug in my driver?

---

### Post by K_V_B on 2007-12-31
I did some more tests, and found out that I could bring up a working wireless network connection manually.

Adding the correct lines, and my wpa passkey in the /etc/network/interfaces file, and then executing ifup eth1 gave me a working connection. But only if I configured a static IP address.


But via the Network Manager applet it still doesn't work...

---

### Post by kegobeer on 2007-12-31
Do you broadcast the SSID?  If not, have you tried with the SSID visible?  For me, even on open networks, I have to broadcast the SSID before I can connect.

---

