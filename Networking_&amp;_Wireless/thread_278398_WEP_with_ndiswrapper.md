---
title: "WEP with ndiswrapper?"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by fishmonger12 on 2006-10-16
I recently installed ubuntu on my dell d620 laptop. I installed my wireless card's driver using ndiswrapper, and the light for the card came on. Ubuntu recognizes the card is there, but I cannot associate with any access points. The access points I'm trying to associate with have an encryption key, I believe they are WEP, but I'm not 100% sure. I looked through these forums and google for relative topics, found something about WPA_supplicant, tried that out, couldn't get that to work. Here's the output of iwlist scanning:

Cell 01 - Address: 00:16:47:A0:2D:60
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

And the output from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

To make things more difficult, the network doesn't broadcast the SSID. The SSID is UNC-1. I'm pretty sure the router found through iwlist scanning is the one I want to connect to. I've been using wireless assistant to try and connect, and it hasn't been working.

I'm pretty new to linux and it's quite possible I'm overlooking something very simple or obvious to experienced users. Any help is appreciated.

---

### Post by fishmonger12 on 2006-10-16
[http://ubuntuguide.org/wiki/Dapper#How_to_enable_WPA_with_Ndiswrapper_driver](http://ubuntuguide.org/wiki/Dapper#How_to_enable_WPA_with_Ndiswrapper_driver)

I've been trying to use the Ubuntu dapper guide on ndiswrapper with wpa, here's where i get stuck:

    * Test it. Make sure your router is broadcasting its SSID. 

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

The output is:

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=5):
     55 4e 43 2d 31                                    UNC-1
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 8: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='UNC-1'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:16:ce:73:93:6b
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request

---

### Post by jml on 2006-10-16
The first thing to do is to make sure that Ubuntu really recognizes your wireless card.  If you have admin privileges for the wireless access point, I would disable all encryption, and see if you can connect to it in the clear.  If you can't you will first have to make sure your card is both recognized and configured properly.

Go into system and select network.  Is your wireless card listed?  If not, then you probably have a driver issue.  If it is listed, then select it by clicking on it and then press configure.  Type in your settings, and close it out.  Then if the card is not activated, you will need to activate it.  This process takes time.  Once you have connectd successfully, enable the wireless access point's encryption.

Here is where it gets a bit tricky.  If the access point uses WEP then go back into the wireless card's properties and type in the WEP encryption key.  Be sure to choose either ASCII or hexadecimal depending on what is typed into the access point.  Back out like you did before and activate the card and you should be good to go.

WPA is a bit more problematic.  WPA supplicant can be downloaded from the Universe repository (I think, possibly Multiverse)  I have not yet been able to confiure it in Ubuntu yet, but others have.  I'm told that if you download Network Manager and Network-Manager-Gnome that this application will then allow the option of setting up a WPA encryption key.  Before you go too far down this path, I would recommend that you go to the WPA_SUPPLICANT web site and make sure your wireless card's chipset is supported.  I struggled for half a day before I realized my card was not supported.  If you search this forum and the wiki, for WPA and WPA_SUPPLICANT you will find a lot of valuable information on setting this up.  Good luck.

Joe

---

### Post by fishmonger12 on 2006-10-16
my wireless card is listed. I cannot change the router to unencrypted because it belongs to the school, and I don't have the ability to configure it. My wireless card is listed in network as active. When i try to choose the network and enter the encryption key, the network manager sits there "thinking" for about 3 or 4 minutes, and nothing happens. The wireless card is still listed as active, but there's no internet connection.

---

