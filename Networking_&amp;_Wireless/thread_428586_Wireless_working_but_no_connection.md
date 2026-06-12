---
title: "Wireless working but no connection"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by brizzlepop on 2007-04-30
I just did a fresh install of Feisty and I'm using ndiswrapper.  Under the network manager, it shows that I'm connected and shows signal strength, but I'm not actually connected.. like I can't access the internet from a browser.  

I searched around the boards but I couldn't find anything, so I'm sorry if this question has already been asked.  Thank you to anybody who can try to help!

---

### Post by sdide on 2007-04-30
post output of (as root or with sudo)

~# iwconfig

---

### Post by brizzlepop on 2007-04-30
lo        no wireless extensions.



eth0      no wireless extensions.



eth1      IEEE 802.11g  ESSID:off/any  

          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   

          Bit Rate=48 Mb/s   Tx-Power:25 dBm   

          RTS thr=2347 B   Fragment thr=2346 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sdide on 2007-04-30
you are not associated with the AP, look at the 2nd line of output:

"Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated"

you need to associate to your AP,

---

### Post by brizzlepop on 2007-04-30
I'm sorry but how should I associate my access point?  I'm pretty much clueless when it comes to networking. :confused:

---

### Post by sdide on 2007-04-30
I'm not sure how one does it with NetworkManager.
I use wpa_supplicant myself. 

wpa_supplicant is a command line tool, its usually a lot easier to debug using such tools, At least, thats what I think. If you want to give wpa_supplicant a try, 

you need to do 

~# apt-get install wpasupplicant    

this won't break any current setup btw.

Then you probably need to edit the /etc/wpa_supplicant.conf,

look in  /usr/share/doc/wpasupplicant/examples  (after you installed) 

you need to write a config that fits with your AP. e.g type of encryption, key, essid, such things.

for example if your AP named "My_very_own_AP" expects you to use WPA-PSK, with key "My_very_own_key" - a section in your config, would probably look like: 

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

network {
        ssid=""My_very_own_AP
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="My_very_own_key"
}
 
make sure only the root user can acces the file, 

~# chmod 600 /etc/wpa_supplicant.conf

execute wpa_supplicant:

~# wpa_supplicant -ieth1 -Dwext -c/etc/wpa_supplicant.conf

---

### Post by ifmusic on 2007-04-30
i have a similar problem i tried with the iwlist scan command and it shows my AP up and running.
I also have a config file for supplicant

```

# path to UNIX socket control interface
ctrl_interface=/var/run/wpa_supplicant

### Example of basic WPA-PSK secured AP
network={
	ssid="CasitaWiFi"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
             # psk="My 63byte long ascii passphrase....."
	psk=my 64byte long Hex Hash from Passphrase + ssid (from wpa_passphrase
  }

```

But when i launch supplicant i DOES associate to my AP, but right after that i times out...
I don't know what's wrong... i think it's a similar problem.

---

### Post by ifmusic on 2007-04-30
Also :

```
Output from Wpa_Supplicant with psk=64byte Hash:

ifmusic@rodrigo:~$ sudo wpa_supplicant -Dwext -iwlan0 -cconfig 
Password:
Trying to associate with 00:0e:2e:7c:f6:cf (SSID='CasitaWiFi' freq=2462 MHz)
Associated with 00:0e:2e:7c:f6:cf
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
CTRL-EVENT-TERMINATING - signal 2 received
ifmusic@rodrigo:~$ sudo wpa_supplicant -Dwext -iwlan0 -cconfig 
Trying to associate with 00:0e:2e:7c:f6:cf (SSID='CasitaWiFi' freq=2462 MHz)
Associated with 00:0e:2e:7c:f6:cf
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Authentication with 00:0e:2e:7c:f6:cf timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
and so on.......

--------------------------------------------------------------------------------------
Output from Wpa_Supplicant with psk="passphrase":

ifmusic@rodrigo:~$ sudo wpa_supplicant -Dwext -iwlan0 -cconfig 
Password:
Trying to associate with 00:0e:2e:7c:f6:cf (SSID='CasitaWiFi' freq=2462 MHz)
Associated with 00:0e:2e:7c:f6:cf
Authentication with 00:0e:2e:7c:f6:cf timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:0e:2e:7c:f6:cf (SSID='CasitaWiFi' freq=2462 MHz)
Associated with 00:0e:2e:7c:f6:cf
Authentication with 00:0e:2e:7c:f6:cf timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-TERMINATING - signal 2 received


```

---

### Post by sdide on 2007-05-01
try running 

~# wpa_supplicant -Dwext -iwlan0 -cconfig -dd

(you might want to pipe standard out and standard error into a file, it could be a lot of output.)
and lets see what fails,

---

### Post by ifmusic on 2007-05-01
Ok, so this is an output with DD, 
Remember that without DD i get something like:
WPA: EAPOL-Key Replay Counter did not increase - dropping packet

So this is the -dd output:

```
Initializing interface 'wlan0' conf '/home/ifmusic/config' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/home/ifmusic/config' -> '/home/ifmusic/config'
Reading configuration file '/home/ifmusic/config'
ctrl_interface='/var/run/wpa_supplicant'
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=10):
     43 61 73 69 74 61 57 69 46 69                     CasitaWiFi      
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=62): [REMOVED]
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='CasitaWiFi'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:14:a5:73:e0:5a
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 259 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:0e:2e:7c:f6:cf ssid='CasitaWiFi' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:0e:2e:7c:f6:cf (SSID='CasitaWiFi' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=89
AssocReq IE wireless event - hexdump(len=81): 00 0a 43 61 73 69 74 61 57 69 46 69 01 08 82 84 0b 16 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 06 00 40 96 01 01 00 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 08 82 84 0b 16 0c 12 18 24 32 04 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0e:2e:7c:f6:cf
Association info event
req_ies - hexdump(len=81): 00 0a 43 61 73 69 74 61 57 69 46 69 01 08 82 84 0b 16 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 06 00 40 96 01 01 00 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
resp_ies - hexdump(len=16): 01 08 82 84 0b 16 0c 12 18 24 32 04 30 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0e:2e:7c:f6:cf
No keys have been configured - skip key clearing
Associated with 00:0e:2e:7c:f6:cf
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:0e:2e:7c:f6:cf (ver=1)
WPA: Renewed SNonce - hexdump(len=32): f8 63 7a 0a bb 67 92 a4 37 f8 d8 d9 f2 5f 7c e8 76 55 67 05 be 5a c6 48 53 27 85 db c4 97 8c f4
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 09 00 20 00 00 00 00 00 00 00 00 f8 63 7a 0a bb 67 92 a4 37 f8 d8 d9 f2 5f 7c e8 76 55 67 05 be 5a c6 48 53 27 85 db c4 97 8c f4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 23 09 d1 c9 83 fa 48 42 5b aa 07 91 18 d5 a7 bf 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 01 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 05 2e d8 61 38 b8 6e e3 2b 7e 9a 76 1b 35 d4 4f 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 05 2e d8 61 38 b8 6e e3 2b 7e 9a 76 1b 35 d4 4f
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 01 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 05 2e d8 61 38 b8 6e e3 2b 7e 9a 76 1b 35 d4 4f 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:0e:2e:7c:f6:cf (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 de fc 1f 8d 6b 79 d9 d6 29 7d e4 ee 88 5a 14 a6 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
RX EAPOL from 00:0e:2e:7c:f6:cf
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 f8 13 5a fb ed f9 f5 6d f3 60 66 8a c6 0b b1 bc 85 9b ad 4c bd 09 c1 58 d7 1c df 2b 3c 39 c8 48 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Authentication with 00:0e:2e:7c:f6:cf timed out.
Added BSSID 00:0e:2e:7c:f6:cf into blacklist
State: GROUP_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_disassociate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:0e:2e:7c:f6:cf blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
Scan timeout - try to get results
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Removed BSSID 00:0e:2e:7c:f6:cf from blacklist (clear)
Cancelling scan request
```

i'm really unable to follow this dump.
Some help???
(i waited a couple of seconds and then Ctrl+C)

---

### Post by ifmusic on 2007-05-02
This is the second post about this same problem and No answer!!

Please!! Where did the experts go?!!

---

### Post by mas99 on 2007-05-03
> **ifmusic said:**
> This is the second post about this same problem and No answer!!

Please!! Where did the experts go?!!

Their wireless isnt working either ;)

In that long log extract it looks as if you are configured for wpa using tkip but there are no keys defined.

Can you check your config files and make sure that you have your key set.  If using wpa_supplicant in the config file, if network manager are you being asked for a key or a password for a keyring?

I have to say I think that wireless is well and truly screwed up.   mine is working about half the time.   I suspect network manager but Im too busy trying to do other stuff to spend time looking through other peoples code.

---

### Post by bedfojo on 2007-05-03
All I can suggest is to do what I did with Feisty's borked wireless.

Uninstall ndiswrapper and network-manager completely with synaptic.

Compile the latest version of ndiswrapper (1.42) yourself - see the ubuntu wiki for instructions.

Reinstall the windows drivers.

Install wicd instead of network-manager. (Not in the repos, you need to go to their website).

Mine now works on an Acer Aspire 3613WLMi with the Broadcom 4318 chipset, using WPA.

Apologies I'm not at home so don't have access to all the links to help you with this, but I'm sue a bit of searching will show you how to do it.

---

### Post by ifmusic on 2007-05-03
> **bedfojo said:**
> All I can suggest is to do what I did with Feisty's borked wireless.

Uninstall ndiswrapper and network-manager completely with synaptic.

Compile the latest version of ndiswrapper (1.42) yourself - see the ubuntu wiki for instructions.

Reinstall the windows drivers.

Install wicd instead of network-manager. (Not in the repos, you need to go to their website).

Mine now works on an Acer Aspire 3613WLMi with the Broadcom 4318 chipset, using WPA.

Apologies I'm not at home so don't have access to all the links to help you with this, but I'm sue a bit of searching will show you how to do it.

All right, i'll try that then. Thanks for the hope!

---

### Post by Candace on 2007-05-04
Hi ifmusic,
I am having exactly the same symptoms as you are (wireless light is on but no connection), and I am going to try what was  suggested right now. If I have any luck I will post what I did, and if you get yours working please post! I have an HP dv2000, with wire less card Broadcom 1390 WLAN.  "Talk" to you soon hopefully. :)

---

### Post by Candace on 2007-05-04
It works!! Finally I have a wireless connection with Feisty Fawn! This is so awesome! Okay, I was having the same problem exactly as user ifmusic, and here is what I did.  I have a dual boot Ubuntu 7.04 and WinXP HP dv2000 laptop, with wireless card Broadcom 1390 WLAN. The more detailed steps are in link 1, it is just a really long message and I only found it looking for something else.  This is really very simple and makes so much sense even to a noob. :) These steps start from the wifi light being ON, but no real wireless connection.  If you have done the steps in Link 2, you don't have to install or uninstall anything else to get wireless working. :guitar: 

Link 1: [http://ubuntuforums.org/showthread.php?t=422741](http://ubuntuforums.org/showthread.php?t=422741). 

If your wireless light is not on, I followed the steps here to get it on (from a fresh Ubuntu install)  

Link 2: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

**1.**  (not sure if this first step is really necessary but I did it and wireless works)
In the directory where you installed R151517.EXE (see link 2) do this:
Update modules...
Code:

sudo depmod -a

**2.  **Assuming you have done all the other steps from Link 2, proceed.  
[/B]Now you have to modify some of the files that came with your Ubuntu install.
 
[please note: most of what follows is from user itsmeagain, see link 1, thank you itsmeagain, aka Stew. I just edited them, not meaning to plagiarize or anything like that]

**3. Modifying some files...**
[/B]From a Terminal window
Code:

sudo gedit /etc/iftab

Original File:
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:08:c7:ca:91:ff arp 1
eth1 mac 00:06:25:1c:f3:d6 arp 1

Change this file as shown below, then File > Save ***... (iftab) > Save > Replace > close the window:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:08:c7:ca:91:ff arp 1
wlan0 mac 00:06:25:1c:f3:d6 arp1

[changed eth1 to wlan0 :)  and mac doesn't mean you have a mac computer, not sure what it means but in case you were worried.]
Notes:
“wlan0 mac 00:06:25:1c:f3:d6 arp1” is the Linksys wireless card mac address

**4. Keep modifying files. **
Code:

sudo gedit /etc/modules

Original File:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

[my file had sbp2 at the bottom which I removed]

Change this file as shown below then File > Save ***... (modules) > Save > Replace > close the window

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

[B]5. And just look at this file
[/B]
Code:

sudo gedit /etc/modprobe.d/ndiswrapper

Original File:
alias wlan0 ndiswrapper
Note:
This file should be as above and should not need modifying

**6. Reboot the machine. At this point, you [B]must** unplug your ethernet (wired) connection.
[/B]

**7. Setting up the Network...**

Go to System > Administration > Network > input the root password if prompted > click on Wireless Connection > Properties > set the following...
Remove the tick from “Enable roaming mode
Network Name (ESSID): Input your ESSID (network name), e.g. "linksys"

To find out your ESSID, you can just type this into a terminal:
Code:

sudo iwconfig

Some output will show up similar to this, which will show your ESSID. Note also that the Access Point is set, so the no wireless issue does not relate to the Access Point (at least for me).

candace@home:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:3D:27:6F   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key: off
          Power Management: off
          Link Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Don't put in your network password (yet). There are also instructions in Link 1 to secure your network, I am just not there yet.

Configuration: to Automatic configuration (DHCP)
OK > Close

[B]8. Check one more file, it should look like below...

Code:

sudo gedit /etc/network/interfaces

Original file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid “YOUR ESSID”

The internet should now work! Congratulations!

**Troubleshooting:**

If your internet is still not working, try unplugging your ethernet cable and rebooting (restarting) again.

---

