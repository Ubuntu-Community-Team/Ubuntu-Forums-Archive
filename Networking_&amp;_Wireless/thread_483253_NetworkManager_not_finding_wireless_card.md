---
title: "NetworkManager not finding wireless card?"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by reelbigjosh on 2007-06-24
I've replaced the HDD in my laptop and was attempting to install Fesity, but without luck (install freezes at 15% after initial setup and partitioning in both Ubuntu and Xubuntu).  So I switched out for Dapper, and am attempting to setup my wireless card.  Naturally, Ubuntu loads bcm43xx by default, but I need ndiswrapper (the wireless card is a PCMCIA Linksys WPC54G v3). I also need WPA to work.

The wireless worked exactly one time: when I first installed ndiswrapper (and suitable .inf) and network-manager.  At that time, before blacklisting bcm43xx and autoloading ndiswrapper, I had simply removed the modules ieee80211, ieee80211softmac, ieee80211crypt, and bcm43xx, then modprobe ndiswrapper.  Loaded nm-applet by hand and it picked up right away on my network.   

Current setup does not work.  nm-applet does not seem to detect my home WAP... or any at all for that point.  More info:

ndiswrapper is loaded at boot in /etc/modules.  bcm43xx blacklisted in /etc/modprobe.d/blacklist.
$ lsmod | grep ndiswrapper
ndiswrapper           177364  0
usbcore               130692  3 ndiswrapper,ohci_hcd

iwconfig yields:

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nm-applet is loaded and sitting in taskbar, but does not detect a WAP.  Have attempted to reinstall wpa_supplicant, as well as network-manager.  

Per the [WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-79f2be08212466f6708bdbaeae97e654f73aea66"), wlan0 is *not* in my /etc/network/interfaces ...

---

After all this, I attempt to configure WPA supplicant manually.  Still following the directions in the aforementioned WPA HowTo, 


sudo wpa_supplicant -wlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w gives me:

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=6):
     7a 6f 65 6e 65 74                                 zoenet          
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='zoenet'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:14:bf:1a:90:16
wpa_driver_ndiswrapper_set_wpa
wpa_driver_ndiswrapper_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ndiswrapper_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ndiswrapper_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ndiswrapper_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ndiswrapper_set_countermeasures
wpa_driver_ndiswrapper_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ndiswrapper_set_wpa
wpa_driver_ndiswrapper_set_drop_unencrypted
wpa_driver_ndiswrapper_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request

---

